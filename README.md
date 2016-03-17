Ansible Role for Redis
====================

[![Build Status](https://travis-ci.org/vitalied/ansible-role-redis.svg?branch=master)](https://travis-ci.org/vitalied/ansible-role-redis)
[![GitHub tag](https://img.shields.io/github/tag/vitalied/ansible-role-redis.svg)](https://github.com/vitalied/ansible-role-redis)
[![GitHub license](https://img.shields.io/github/license/vitalied/ansible-role-redis.svg)](https://github.com/vitalied/ansible-role-redis/blob/master/LICENSE)
[![Ansible Role](https://img.shields.io/ansible/role/8587.svg)](https://galaxy.ansible.com/detail#/role/8587)

Ansible Role for Redis Management.

Requirements
------------

This role require Ansible 2.0 or higher.

This role was designed for Ubuntu Server 14.04+.

Role Variables
--------------

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th>parameter</th>
<th>required</th>
<th>default</th>
<th>choices</th>
<th>comments</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>redis_data_dir</td>
<td>yes</td>
<td>/srv/redis</td>
<td></td>
<td>Specifies the redis data storage directory.</td>
</tr>
<tr class="even">
<td>redis_db_filename</td>
<td>yes</td>
<td>dump.rdb</td>
<td></td>
<td>Specifies the redis db filename.</td>
</tr>
<tr class="odd">
<td>redis_bind_interface</td>
<td>yes</td>
<td>127.0.0.1</td>
<td></td>
<td>The IP address (127.0.0.1 for localhost) on which redis will listen for requests. Set to 0.0.0.0 to listen on all interfaces.</td>
</tr>
<tr class="even">
<td>redis_port</td>
<td>yes</td>
<td>6379</td>
<td></td>
<td>The port on which redis will listen for requests.</td>
</tr>
<tr class="odd">
<td>redis_unix_socket</td>
<td>yes</td>
<td>""</td>
<td></td>
<td>The unix socket file on which redis will listen for requests.</td>
</tr>
<tr class="even">
<td>redis_timeout</td>
<td>yes</td>
<td>300</td>
<td></td>
<td>Close a connection after a client is idle N seconds. Set to 0 to disable timeout.</td>
</tr>
<tr class="odd">
<td>redis_databases</td>
<td>yes</td>
<td>16</td>
<td></td>
<td>The number of Redis databases.</td>
</tr>
<tr class="even">
<td>redis_rdb_compression</td>
<td>yes</td>
<td>yes</td>
<td><ul>
<li><code>yes</code></li>
<li><code>no</code></li>
</ul></td>
<td>Compress string objects using LZF when dump .rdb databases.</td>
</tr>
<tr class="odd">
<td>redis_save</td>
<td>yes</td>
<td><a href="https://github.com/vitalied/ansible-role-redis/blob/master/defaults/main.yml">defaults/main.yml</a></td>
<td><ul>
<li><code>list</code></li>
</ul></td>
<td>
Snapshotting configuration. Setting values in this list will save the database to disk
if the given number of seconds (e.g. 900) and the given number of write operations (e.g. 1) have occurred.
</td>
</tr>
<tr class="even">
<td>redis_max_memory</td>
<td>yes</td>
<td>0</td>
<td></td>
<td>Limit memory usage to the specified amount of bytes. Leave at 0 for unlimited.</td>
</tr>
<tr class="odd">
<td>redis_max_memory_policy</td>
<td>yes</td>
<td>noeviction</td>
<td><ul>
<li><code>volatile-lru</code> (remove the key with an expire set using an LRU algorithm)</li>
<li><code>allkeys-lru</code> (remove any key according to the LRU algorithm)</li>
<li><code>volatile-random</code> (remove a random key with an expire set)</li>
<li><code>allkeys-random</code> (remove a random key, any key)</li>
<li><code>volatile-ttl</code> (remove the key with the nearest expire time (minor TTL))</li>
<li><code>noeviction</code> (don't expire at all, just return an error on write operations)</li>
</ul></td>
<td>The method to use to keep memory usage below the limit.</td>
</tr>
<tr class="even">
<td>redis_max_memory_samples</td>
<td>yes</td>
<td>5</td>
<td></td>
<td>Number of samples to use to approximate LRU.</td>
</tr>
<tr class="odd">
<td>redis_append_only</td>
<td>yes</td>
<td>no</td>
<td><ul>
<li><code>yes</code></li>
<li><code>no</code></li>
</ul></td>
<td>
The appendonly option, if enabled, affords better data durability guarantees, at the cost of slightly slower performance.
</td>
</tr>
<tr class="even">
<td>redis_append_fsync</td>
<td>yes</td>
<td>everysec</td>
<td><ul>
<li><code>always</code> (fsync after every write to the append only log. Slow, Safest)</li>
<li><code>everysec</code> (fsync only one time every second. Compromise)</li>
<li><code>no</code> (don't fsync, just let the OS flush the data when it wants. Faster, Most risky)</li>
</ul></td>
<td>Appnedonly sync type.</td>
</tr>
</tbody>
</table>

Dependencies
------------

No additional role dependencies.

Example Playbook
----------------

    - hosts: all
      roles:
        - role: vitalied.redis    

License
-------

-   Code released under [MIT](https://github.com/vitalied/ansible-role-redis/blob/master/LICENSE)
-   Docs released under [CC BY 4.0](http://creativecommons.org/licenses/by/4.0/)
