---
title: "/opt not listing files and folders"
date: 2021-12-09
forum: General Help
---

### Post by aug7744 on 2021-12-09
I have used Rapiddisk cache to create writeback caches for /root , /opt and /home.
Rapiddisk is available from link below
[https://github.com/pkoutoupis/rapiddisk](https://github.com/pkoutoupis/rapiddisk)

When OS is starting root opt home are mounted using a writeback cache.
The problem is when browsing /opt is empty not showing any file or folder.
opt have folders and files.
If starting a file manager using sudo browsing /opt in few seconds is listed all files and folders.
In /opt have in root a folder owner root and other folder owner user.
That issue not had happened before creating writeback cache for /opt.

If running a software being sudo browse /opt all files and folders will be listed to current login and in next reboot need repeat the same action.

Thanks for read and reply.

---

### Post by TheFu on 2021-12-10
Snap packages?  snap programs cannot access storage outside /home by default.

What are the permissions and owner/group/other on the /opt directory?  Any ACLs applied?

Also, it is usually a very bad idea to use a GUI file manager with sudo. If not now, later, you'll have issues. This is an Ubuntu problem. No all other distros have the same issue. There is a sudo option to make it ok, but people almost always forget to use that option.

---

### Post by aug7744 on 2021-12-10
"What are the permissions and owner/group/other on the /opt directory?  Any ACLs applied?"
/opt is root , but inside a folder is root and another owner user.
Not related with snap.

The problem is when starting OS is created a writecache buffer for /opt using dm-writecache, but is how if not is being correctly mounted.
In file manager is listed "dm-2". /opt is using a second created buffer.
If clicking in "dm-2" automatically change the naming to "opt" and now all files are listed.
I need a command or configuration to when OS was totally started is how if was "clicked" in "dm-2" to list all files in /opt

---

### Post by TheFu on 2021-12-10
Forget using a GUI. GUIs lie.

What are the permissions?  Looking for **ls -la /opt** 

What does the mount line in the fstab show for /opt?

---

### Post by aug7744 on 2021-12-10
total 0
drwxr-xr-x 1 root 0 Nov 24 05:09
drwxr-xr-x 1 root 186 Nov 24 05:39

Is how if not was mounted correctly. Not file system errors, but if running "sudo mount -a" /opt is mounted correctly.
If in OS boot adding a delay when mounting /opt or run "sudo munt -a" may fix it.

In OS startup is listed the error message
FAILED Failed to mount /opt
DEPEND Dependency failed for local file Systems

---

### Post by HermanAB on 2021-12-11
According to that error, /opt is not mounted.  Therefore all you can see with a file browser or ls, is the mount point, which then seems empty with no files or folders.

---

### Post by TheFu on 2021-12-11
> **TheFu said:**
> What does the mount line in the fstab show for /opt?

And what, exactly, does the fstab file show for mounting /opt?
This shouldn't be so hard.

```
grep /opt /etc/fstab 
```
will provide the answer. If nothing, then the system admin needs to be consulted to correct the issue.

---

### Post by aug7744 on 2021-12-11
UUID=6a7412f7-f09e-464a-93fe-63ac4529ae94 /opt           btrfs   defaults,noatime,nodiratime,lazytime,acl,noautodefrag,commit=360,compress-force=zlib:9,datacow,datasum,max_inline=0,nospace_cache,nossd,notreelog 0 0

---

### Post by deadflowr on 2021-12-11
> noautodef rag
Was this accidental? Like it came out this way when copying to the forums, or is it actually written as this in the real fstab?

---

### Post by TheFu on 2021-12-12
> **aug7744 said:**
> UUID=6a7412f7-f09e-464a-93fe-63ac4529ae94 /opt           btrfs   defaults,noatime,nodiratime,lazytime,acl,noautodefrag,commit=360,compress-force=zlib:9,datacow,datasum,max_inline=0,nospace_cache,nossd,notreelog 0 0

Ok - BRTFS isn't a normal file system.  Does it even use an fstab?  I'm fairly ignorant about it, but whenever dealing with BRTFS, always, always, mention that you aren't using a default file system and give the name so people with that expertise can help.  It would be worth mentioning in the thread title - it is THAT different from other file systems.

Just looking over those options, I'm seeing a few that aren't needed for normal Linux file systems (acl is default) and others that don't exist. I'd start with simplified options in a little test environment, perhaps in a VM.

---

### Post by aug7744 on 2021-12-13
@deadflowr
"Was this accidental?"
I had replied correctly noautodefrag, but was added ["]("https://ubuntuforums.org/member.php?u=1276577")noautodef rag".
If selecting to edit post show correctly noautodefrag
Have anything wrong.

@TheFu
I had configured to avoid very much written in disk.
BTRFS use fstab. See mount options
[https://btrfs.wiki.kernel.org/index.php/Manpage/btrfs%285%29#MOUNT_OPTIONS](https://btrfs.wiki.kernel.org/index.php/Manpage/btrfs%285%29#MOUNT_OPTIONS)     
 
I have formated the /opt partition and using a same UUID.
Now the /opt is being mounted. I wait not see the problem again.
Running btrfs check not had listed errors.
Thanks for all replies.

---

