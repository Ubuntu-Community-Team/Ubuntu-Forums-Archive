---
title: "Can not mount 2nd drive"
date: 2019-02-26
forum: General Help
---

### Post by raleigh3 on 2019-02-26
This USED to mount sdb. Now it doesn't ?

[https://www.dropbox.com/s/abf4t4o4v6ezf5g/Fstab.png?dl=0](https://www.dropbox.com/s/abf4t4o4v6ezf5g/Fstab.png?dl=0)

```
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sda1: UUID="a85421a7-db09-4922-ba41-8312a2f66556" TYPE="ext4" PARTUUID="87fb6afb-01"
/dev/sdb1: LABEL="MAXTOR_SDB1" UUID="b3b0f384-9e2e-45f5-8995-932f1113f59d" TYPE="ext3" PARTUUID="000f0791-01"
/dev/sdb2: LABEL="MAXTOR_SDB2" UUID="8adebdf0-6bc3-4eee-8363-3e9440688d42" SEC_TYPE="ext2" TYPE="ext3" PARTUUID="000f0791-02"
/dev/sdb5: LABEL="MAXTOR_SDB5" UUID="8cdd0e0d-7714-4199-90ba-c6c20ff0ee1d" SEC_TYPE="ext2" TYPE="ext3" PARTUUID="000f0791-05"
/dev/loop8: TYPE="squashfs"
```

---

### Post by TheFu on 2019-02-26
I have no idea what is inside that code block.

Please show the exact mount/fstab/autofs line you expect to work.
Images too hard to read. I have terrible eyesight.

---

### Post by raleigh3 on 2019-02-26
> **TheFu said:**
> I have no idea what is inside that code block.

Please show the exact mount/fstab/autofs line you expect to work.
Images too hard to read. I have terrible eyesight.

It's the result of running sudo blkid.

```
#
# Define default options for autofs.
#
[ autofs ]
#
# master_map_name - default map name for the master map.
#
master_map_name = /etc/auto.master
#
# timeout - set the default mount timeout in secons. The internal
#        program default is 10 minutes, but the default installed
#        configuration overrides this and sets the timeout to 5
#        minutes to be consistent with earlier autofs releases.
#
timeout = 300
#
# negative_timeout - set the default negative timeout for
#              failed mount attempts (default 60).
#
#negative_timeout = 60
#
# mount_wait - time to wait for a response from mount(8).
#            Setting this timeout can cause problems when
#            mount would otherwise wait for a server that
#            is temporarily unavailable, such as when it's
#            restarting. The default setting (-1) of waiting
#            for mount(8) usually results in a wait of around
#            3 minutes.
#
#mount_wait = -1
#
# umount_wait - time to wait for a response from umount(8).
#
#umount_wait = 12
#
# browse_mode - maps are browsable by default.
#
browse_mode = no
#
# mount_nfs_default_protocol - specify the default protocol used by
#                    mount.nfs(8). Since we can't identify
#                    the default automatically we need to
#                    set it in our configuration.
#
#mount_nfs_default_protocol = 3
#
# append_options - append to global options instead of replace.
#
#append_options = yes
#
# logging - set default log level "none", "verbose" or "debug"
#
#logging = none
#
# force_standard_program_map_env - disable the use of the "AUTOFS_"
#            prefix for standard environemt variables when
#            executing a program map. Since program maps
#            are run as the privileded user this opens
#            automount(8) to potential user privilege
#            escalation when the program map is written
#            in a language that  can load components from,
#            for example, a user home directory.
#
# force_standard_program_map_env = no
#
# Define base dn for map dn lookup.
#
# Define server URIs
#
# ldap_uri - space seperated list of server uris of the form
#          <proto>://<server>[/] where <proto> can be ldap
#          or ldaps. The option can be given multiple times.
#          Map entries that include a server name override
#          this option.
#
#         This configuration option can also be used to
#         request autofs lookup SRV RRs for a domain of
#         the form <proto>:///[<domain dn>]. Note that a
#         trailing "/" is not allowed when using this form.
#         If the domain dn is not specified the dns domain
#         name (if any) is used to construct the domain dn
#         for the SRV RR lookup. The server list returned
#         from an SRV RR lookup is refreshed according to
#         the minimum ttl found in the SRV RR records or
#         after one hour, whichever is less.
#
#ldap_uri = ""
#
# ldap_timeout - timeout value for the synchronous API  calls
#          (default is LDAP library default).
#
#ldap_timeout = -1
#
# ldap_network_timeout - set the network response timeout (default 8).
#
#ldap_network_timeout = 8
#
# search_base - base dn to use for searching for map search dn.
#         Multiple entries can be given and they are checked
#         in the order they occur here.
#
#search_base = ""
#
# Define the LDAP schema to used for lookups
#
# If no schema is set autofs will check each of the schemas
# below in the order given to try and locate an appropriate
# basdn for lookups. If you want to minimize the number of
# queries to the server set the values here.
#
#map_object_class = nisMap
#entry_object_class = nisObject
#map_attribute = nisMapName
#entry_attribute = cn
#value_attribute= nisMapEntry
#
# Other common LDAP naming
#
#map_object_class = automountMap
#entry_object_class = automount
#map_attribute = ou
#entry_attribute = cn
#value_attribute= automountInformation
#
#map_object_class = automountMap
#entry_object_class = automount
#map_attribute = automountMapName
#entry_attribute = automountKey
#value_attribute= automountInformation
#
# auth_conf_file - set the default location for the SASL
#           authentication configuration file.
#
#auth_conf_file = /etc/autofs_ldap_auth.conf
#
# map_hash_table_size - set the map cache hash table size.
#             Should be a power of 2 with a ratio of
#             close to 1:8 for acceptable performance
#             with maps up to around 8000 entries.
#             See autofs.conf(5) for more details.
#
#map_hash_table_size = 1024
#
# use_hostname_for_mounts - nfs mounts where the host name resolves
#             to more than one IP address normally need
#             to use the IP address to esure a mount to
#             a host that isn't responding isn't done.
#             If that behaviour is not wanted then set
#            ths to "yes", default is "no".
#
#use_hostname_for_mounts = "no"
#
# disable_not_found_message - The original request to add this log message
#              needed it to be unconditional. That produces, IMHO,
#              unnecessary noise in the log so a configuration option
#              has been added to provide the ability to turn it off.
#              The default is "no" to maintain the current behaviour.
#
#disable_not_found_message = "no"
#
# Otions for the amd parser within autofs.
#
# amd configuration options that are aren't used, haven't been
# implemented or have different behaviour within autofs.
#
# A number of the amd configuration options are not used by autofs,
# some because they are not relevant within autofs, some because
# they are done differently in autofs and others that are not yet
# implemented.
#
# Since "mount_type" is always autofs (because there's no user space
# NFS server) the configuration entries relating to that aren't used.
# Also, server availability is done differently within autofs so the
# options that relate to the amd server monitoring sub-system are
# also not used.
#
# These options are mount_type, auto_attrcache, portmap_program,
# nfs_vers_ping, nfs_allow_any_interface, nfs_allow_insecure_port,
# nfs_proto, nfs_retransmit_counter, nfs_retransmit_counter_udp,
# nfs_retransmit_counter_tcp, nfs_retransmit_counter_toplvl,
# nfs_retry_interval, nfs_retry_interval_udp, nfs_retry_interval_tcp,
# nfs_retry_interval_toplvl and nfs_vers.
#
#
# Other options that are not used within the autofs implementation:
#
# log_file, truncate_log - autofs used either stderr when running in
#    the foreground or sends its output to syslog so an alternate
#    log file (or truncating the log) can't be used.
#
# print_pid - there's no corresponding option for this within autofs.
#
# use_tcpwrappers, show_statfs_entries - there's no user space NFS
#    server to control access to so this option isn't relevant.
#    The show_statfs_entries can't be implemented for the same
#    reason.
#
# debug_mtab_file - there's no user space NFS server and autofs
#    avoids using file based mtab whenever possible.
#
# sun_map_syntax - obviously, are provided by autofs itself.
#
# plock, show_statfs_entries, preferred_amq_port - not supported.
#
# ldap_cache_maxmem, ldap_cache_seconds - external ldap caching
#    is not used by autofs.
#
# ldap_proto_version - autofs always attempts to use the highest
#    available ldap protocol version.
#
# cache_duration, map_reload_interval, map_options - the map
#    entry cache is continually updated and stale entries
#    cleaned on re-load, which is done when map changes are
#    detected so these configuration entries are not used
#    by autofs.
#
# localhost_address - is not used within autofs. This
#    configuration option was only used in the amd user
#    space server code and is not relevant within autofs.
#
#
# Options that are handled differently within autofs:
#
# pid_file - must be given as a command line option on startup.
#
# print_version - program version and feature information is obtained
#    by using the automount command line option "-V".
#
# debug_options, log_options - autofs has somewhat more limited
#    logging and debug logging options. When the log_options
#    options is encountered it is converted to the nearest
#    matching autofs logging option. Since the configuration
#    option debug_options would be handled the same way it
#    is ignored.
#
# restart_mounts - has no sensible meaning within autofs because autofs
#    always tries to re-connect to existing mounts. While this
#    has its own set of problems not re-connecting to existing
#    mounts always results in a non-functional automount tree if
#    mounts were busy at the last shutdown (as is also the case
#    with amd when using mount_type autofs).
#
# forced_unmounts - detaching mounts often causes serious problems
#    for users of existing mounts. It is used by autofs in some
#    cases, either at the explicit request of the user (with a
#    command line or init option) and in some special cases during
#    program operation but is avoided whenever possible.
#
#
# A number of configuration options are not yet implemented:
#
# fully_qualified_hosts - not yet implemented.
#
# unmount_on_exit - since autofs always tries to re-connect
#    to mounts left mounted from a previous shutdown this
#    is a sensible option to implement and that will be
#    done.
#
# browsable_dirs - not yet implemented.
#
# exec_map_timeout - a timeout is not currently used for
#    for program maps, might be implemented.
#
# tag - the tag option is not implemented within autofs.
#
#
# Supported options:
#
# arch, karch, os, osver - these options default to what is returned
#    from uname(2) and can be overridden if required.
#
# full_os - has no default and must be set in the configuration
#    if used in maps.
#
# cluster - if not set defaults to the host domain name. This option
#    corresponds to the HP_UX cluster name (according to the amd
#    source) and is probably not used in Linux but is set anyway.
#
# vendor - has a default value of "unknown", it must be set in the
#    configuration if used in maps.
#
# auto_dir - is the base name of the mount tree used for external
#    mounts that are sometimes needed by amd maps. Its default
#    value is "/a".
#
# map_type - specifies the autofs map source, such as file, nis,
#    ldap etc. and has no default value set.
#
# map_defaults - is used to override /defaults entries within maps
#    and can be used to provide different defaults on specific
#    machines without having to modify centrally managed maps.
#    It is empty by default.
#
# search_path - colon seperated paths to search for maps that
#    are not specified as a full path.
#
# dismount_interval - is equivalent to the autofs timeout option. It
#    is only possible to use this with type "auto" mounts due
#    to the way the autofs kernel module performs expiry. It
#    takes its default value from the autofs internal default
#    of 600 seconds.
#
# autofs_use_lofs - if set to "yes" autofs will attempt to use bind
#    mounts for type "auto" when possible.
#
# nis_domain - allows setting of a domain name other than the system
#    default.
#
# local_domain - is used to override (or set) the host domain name.
#
# normalize_hostnames - if set to "yes" then the contents of ${rhost}
#    is translated in its official host name.
#
# domain_strip - if set to "yes" the domain name part of the host
#     is strippped when normalizing hostnames. This can be useful
#    when using of the same maps in a multiple domain environment.
#
# normalize_slashes - is set to "yes" by default and will collapse
#    multiple unescaped occurrences of "/" to a single "/".
#
# selectors_in_defaults, selectors_on_default - has a default value
#    of "no". If set to "yes" then any defaults entry will be
#    checked for selectors to determine the values to be used.
#    selectors_in_defaults is the preferred option to use.
#
# ldap_base - has no default value. It must be set to the base dn
#    that is used for queries if ldap is to be used as a map
#    source.
#
# ldap_hostports - has no default value set. It must be set to
#    the URI of the LDAP server to be used for lookups when
#    ldap is used a map source. It may contain a comma or
#    space seperated list of LDAP URIs.
#
# hesiod_base - the base name used for hesiod map sources.
#
# Additional configuration options added:
#
# linux_ufs_mount_type - set the default system filesystem type that's
#    used for mount type ufs. There's no simple way to determine
#    what the system default filesystem is and am-utils needs to
#    be continually updated to do this and can easily get it wrong
#    anyway.
#
#
# Define global options for the amd parser within autofs.
#
[ amd ]
#
# Override the internal default with the same timeout that
# is used by the override in the autofs configuration, sanity
# only change.
#
dismount_interval = 300
#
# map_type = file
#
# Overriding this can cause autofs to use less resources because
# it will use symlinks instead of bind mounts in certain cases.
# You should ensure that the autofs kernel module your using
# supports expration of symlinks for best results (although this
# appears to work reasonably well most of the time without the
# update).
#
# autofs_use_lofs = yes
#
# Several configuration options can be set per mount point.
# In particulr map_type, map_name, map_defaults, search_path,
# browsable_dirs, dismount_interval and selectors_in_defaults
# (not all of which are currently implemented, see above).
#
# Also, if a section for an amd mount point is defined here
# it isn't necessary to specify the format in the corresponding
# master map entry and the format will be inherited for type
# "auto" mounts.
#
# [ /expamle/mount ]
# dismount_interval = 60
# map_type = nis

[CODE]# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
#
# As of 2/26/19, this does NOT mount sdb
#
UUID=a85421a7-db09-4922-ba41-8312a2f66556      /                   ext4    errors=remount-ro   0       1
#
#
UUID=b3b0f384-9e2e-45f5-8995-932f1113f59d      /SDB1_Mountpoint     ext3     defaults          0       0
#
UUID=8adebdf0-6bc3-4eee-8363-3e9440688d42      /SDB2_Mountpoint     ext3        defaults       0       0
#
UUID=8cdd0e0d-7714-4199-90ba-c6c20ff0ee1d      /SDB5_Mountpoint     ext3     defaults          0       0

/swapfile                             none            swap    sw                               0       0
```[/CODE]

---

### Post by dmnur on 2019-02-27
Please show us what happens when you run:
```
sudo mount /SDB1_Mountpoint
```

---

### Post by raleigh3 on 2019-02-27
It does mount.

---

### Post by dmnur on 2019-02-27
Is this an external USB drive? Do you expect it to be automatically mounted when you plug it in? Or just at boot? Please clarify.

---

### Post by raleigh3 on 2019-02-27
Internal drive. It used to mount automatically. 

I can access drive with this, but I would still like to know why the drive does not show up on the desktop like it used to.

```
thunar /media/andy/MAXTOR_SDB1/Ubuntu_Mate_18.04/
```

---

### Post by TheFu on 2019-02-28
My intent by asking for
> 
Please show the exact mount/fstab/autofs line you expect to work.
Was to see the specific line you had manually added to one of those files that would make something mount automatically. If you didn't do that (add at least 1 line), then I haven't any idea how it would mount automatically, unless you are using gvfs.  

I avoid using gvfs for a number of reasons.  [https://wiki.gnome.org/Projects/gvfs](https://wiki.gnome.org/Projects/gvfs) has more details about how it should work, if that is what you desire.

With USB storage, using permanent mount techniques like the fstab isn't something I'd advise, but using autofs is slightly more involved. I'm willing if you are.
If I scroll to the bottom, I see the fstab lines:```

UUID=b3b0f384-9e2e-45f5-8995-932f1113f59d      /SDB1_Mountpoint     ext3     defaults          0       0
UUID=8adebdf0-6bc3-4eee-8363-3e9440688d42      /SDB2_Mountpoint     ext3        defaults       0       0
UUID=8cdd0e0d-7714-4199-90ba-c6c20ff0ee1d      /SDB5_Mountpoint     ext3     defaults          0       0
```
Each of the mount points, empty directories, needs to exist.```

sudo mkdir /SDB1_Mountpoint  /SDB2_Mountpoint   /SDB5_Mountpoint   
```
Next, we need to look at the mount options - _defaults_ - checking the mount manpage ... 
```
       defaults
              Use the default options: rw, suid, dev, exec, auto, nouser,  and
              async.

              Note  that  the real set of all default mount options depends on
              kernel and filesystem type.  See the beginning of  this  section
              for more details.
```
The manpage for fstab has some more information.  The last field, ```

       The sixth field (fs_passno).
              This field is used by fsck(8) to determine the  order  in  which
              filesystem  checks  are  done at boot time.  The root filesystem
              should be specified with a fs_passno of  1.   Other  filesystems
              should  have  a fs_passno of 2.  Filesystems within a drive will
              be checked sequentially, but  filesystems  on  different  drives
              will  be  checked at the same time to utilize parallelism avail&#8208;
              able in the hardware.  Defaults to  zero  (don't  fsck)  if  not
              present.
```
 
If the HDD is powered and connected when the machine is rebooted, I would think the _defaults_ option would automatically mount the storage, assuming the directories already exist. If they do not exist, the mounts will fail.  Check the system log files in /var/log/ for issues.

If the file systems have any corruption or were not properly closed, then they won't mount. Usually, there would be an error in the log files explaining it.

---

