---
title: "Pam_mount causing extreme load average"
date: 2022-05-11
forum: General Help
---

### Post by vincentya on 2022-05-11
Hi

I am using PBIS-open and pam mount to get ad membership and domain creds to use.
I have an issue when mounting windows shares through pam mount where load average keeps increasing and never stops increasing.
From what i can find as reason to load average is the following:
```

      72 |        4.00 | (pool)                | Disk (Uninterruptible) | statfs          | smb2_reconnect.part.23    | __x64_sys_statfs()->__do_sys_statfs()->user_statfs()->vfs_statfs()->statfs_by_dentry()->cifs_statfs()->smb311_queryfs()->smb2_queryfs()->smb2_query_info_compound()->SMB2_open_init()->smb2_plain_req_init()->smb2_reconnect.part.23()                                                                                
      36 |        2.00 | (cifsd)               | Disk (Uninterruptible) | [kernel_thread] | dfs_cache_update_vol      | kthread()->cifs_demultiplex_thread()->cifs_handle_standard()->cifs_reconnect()->dfs_cache_update_vol()                                                                                                                                                                                                                
      18 |        1.00 | (I/O pool *)          | Disk (Uninterruptible) | lstat           | smb2_reconnect.part.23    | __x64_sys_newlstat()->__do_sys_newlstat()->vfs_statx()->vfs_getattr()->vfs_getattr_nosec()->cifs_getattr()->cifs_revalidate_dentry_attr()->cifs_get_inode_info()->smb2_query_path_info()->open_shroot()->SMB2_open_init()->smb2_plain_req_init()->smb2_reconnect.part.23()                                            
      18 |        1.00 | (kworker/*:*+cifsiod) | Disk (Uninterruptible) | [kernel_thread] | smb2_reconnect.part.23    | kthread()->worker_thread()->process_one_work()->refresh_cache_worker()->smb2_get_dfs_refer()->SMB2_ioctl()->SMB2_ioctl_init()->smb2_plain_req_init()->smb2_reconnect.part.23()                                                                                                                                        
      18 |        1.00 | (kworker/*:*+cifsiod) | Disk (Uninterruptible) | [kernel_thread] | smb2_reconnect.part.23    | kthread()->worker_thread()->process_one_work()->smb2_reconnect_server()->smb2_reconnect.part.23()                                                                                                                                                                                                                     
      18 |        1.00 | (kworker/*:*+cifsiod) | Disk (Uninterruptible) | [kernel_thread] | wait_for_response.isra.12 | kthread()->worker_thread()->process_one_work()->smb2_reconnect_server()->smb2_reconnect.part.23()->cifs_negotiate_protocol()->smb2_negotiate()->SMB2_negotiate()->cifs_send_recv()->compound_send_recv()->wait_for_response.isra.12()                                                                                 
      18 |        1.00 | (pool)                | Disk (Uninterruptible) | statfs          | wait_for_response.isra.12 | __x64_sys_statfs()->__do_sys_statfs()->user_statfs()->vfs_statfs()->statfs_by_dentry()->cifs_statfs()->smb311_queryfs()->smb2_queryfs()->smb2_query_info_compound()->SMB2_open_init()->smb2_plain_req_init()->smb2_reconnect.part.23()->cifs_negotiate_protocol()->smb2_negotiate()->SMB2_negotiate()->cifs_send_recv()->compound_send_recv()->wait_for_response.isra.12()

```

The folder is mounted with CIFS and options NOSUID and NODEV
example:


```
<volume       user="username"       fstype="cifs"       server="server"      path="%(USER)"   mountpoint="~/somefolder/%(USER)" options="NOSUID,NODEV"/>

```

Any suggestions to why this is happening. 
I can add that mounting with gio mount does not trigger this problem but  there seems to be some issues with gio mounted disks as well . 
I.ex extracting .tar.gz files fails or gives errormessages and is generally slower.

---

### Post by TheFu on 2022-05-12
I've never heard of pam_mount. Cannot help with that.  Not sure what it does.
[https://wiki.archlinux.org/title/pam_mount](https://wiki.archlinux.org/title/pam_mount) seems relevant.

Would you consider using **autofs** instead?  It is based on amd from the mid-1990s and has been very stable for 20 yrs.
[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

With CIFS, NODEV and NOSUID don't really make sense.  CIFS doesn't convey Unix permissions, so only some odd mount options would allow those to work.

Does a normal CIFS mount on the command line work? That would be the first things to test.

---

