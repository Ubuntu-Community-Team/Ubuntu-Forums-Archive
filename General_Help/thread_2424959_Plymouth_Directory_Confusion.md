---
title: "Plymouth Directory Confusion"
date: 2019-08-18
forum: General Help
---

### Post by rwe061 on 2019-08-18
Ubuntu 19.04

In looking at the _plymouth-debug.log_ file I am confused about a failed message, missing directory and files.  Here are some lines from that log file.

[main.c:1683]                 tell_systemd_to_print_details:telling systemd to start printing details
[main.c:734]                       get_cache_file_for_mode:returning cache file '/var/lib/plymouth//boot-duration'
[main.c:316]                                 load_settings:Trying to load /etc/plymouth//plymouthd.conf
[ply-key-file.c:83]                        ply_key_file_open_file:Failed to open key file /etc/plymouth//plymouthd.conf: No such file or directory
[main.c:463]                    find_system_default_splash:failed to load /etc/plymouth//plymouthd.conf
[main.c:316]                                 load_settings:Trying to load /run/plymouth/plymouthd.defaults
[ply-key-file.c:83]                        ply_key_file_open_file:Failed to open key file /run/plymouth/plymouthd.defaults: No such file or directory
[main.c:477]              find_distribution_default_splash:failed to load /run/plymouth/plymouthd.defaults, trying /usr/share/plymouth//
[main.c:316]                                 load_settings:Trying to load /usr/share/plymouth//plymouthd.defaults
[ply-key-file.c:83]                        ply_key_file_open_file:Failed to open key file /usr/share/plymouth//plymouthd.defaults: No such file or directory
[main.c:479]              find_distribution_default_splash:failed to load /usr/share/plymouth//plymouthd.defaults

It looks like there should be a directory at /etc/plymouth, but my ubuntu 19.04 does not have that directory.  There are some plymouth files under /var 

What is the best way to fix this in an ubuntu standard way ?  Should I create /etc/plymouth and find missing files and move them to the directories mentioned in the error log ?  

What or where is the ubuntu default directory for plymouth ?

I may have had this same issue in 18.04 before upgrading.  It really doesn't create any problem other than reporting a pop-up error after boot.

---

