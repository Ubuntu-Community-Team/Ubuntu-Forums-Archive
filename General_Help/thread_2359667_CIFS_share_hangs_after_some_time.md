---
title: "CIFS share hangs after some time"
date: 2017-04-26
forum: General Help
---

### Post by thedavix on 2017-04-26
Hello,

Since yesterday, I am experiencing hangs on my mounted network folder and I have no idea where to look to solve this problem.
I must precise I have been using the following configuration since more than a year now and everything was working fine until yesterday.
Yesterday, I did some apt-get update of generic stuff.. I don't know if it's because of that.. usually, I do update my box once a week to make sure I have the latest soft, following is what got updated

```
Start-Date: 2017-04-25  09:32:03
Commandline: apt-get dist-upgrade
Requested-By: mickey (1000)
Install: linux-image-4.4.0-75-generic:amd64 (4.4.0-75.96, automatic), linux-image-extra-4.4.0-75-generic:amd64 (4.4.0-75.96, automatic), linux-headers-4.4.0-75-generic:amd64 (4.4.0-75.96, automatic), linux-headers-4.4.0-75:amd64 (4.4.0-75.96, automatic)
Upgrade: linux-headers-generic:amd64 (4.4.0.72.78, 4.4.0.75.81), linux-image-generic:amd64 (4.4.0.72.78, 4.4.0.75.81), linux-generic:amd64 (4.4.0.72.78, 4.4.0.75.81)
End-Date: 2017-04-25  09:32:32


Start-Date: 2017-04-25  10:46:57
Commandline: apt autoremove
Requested-By: mickey (1000)
Remove: linux-image-extra-4.4.0-71-generic:amd64 (4.4.0-71.92), linux-headers-4.4.0-71-generic:amd64 (4.4.0-71.92), linux-headers-4.4.0-66:amd64 (4.4.0-66.87), linux-headers-4.4.0-71:amd64 (4.4.0-71.92), linux-image-4.4.0-66-generic:amd64 (4.4.0-66.87), linux-image-extra-4.4.0-66-generic:amd64 (4.4.0-66.87), linux-headers-4.4.0-66-generic:amd64 (4.4.0-66.87), linux-image-4.4.0-71-generic:amd64 (4.4.0-71.92)
End-Date: 2017-04-25  10:47:11


Start-Date: 2017-04-26  13:55:59
Commandline: apt-get upgrade
Requested-By: mickey (1000)
Upgrade: gir1.2-gtk-3.0:amd64 (3.18.9-1ubuntu3.2, 3.18.9-1ubuntu3.3), libapt-inst2.0:amd64 (1.2.19, 1.2.20), appstream:amd64 (0.9.4-1ubuntu2, 0.9.4-1ubuntu3), libgtk-3-common:amd64 (3.18.9-1ubuntu3.2, 3.18.9-1ubuntu3.3), apt:amd64 (1.2.19, 1.2.20), libgtk-3-0:amd64 (3.18.9-1ubuntu3.2, 3.18.9-1ubuntu3.3), libapt-pkg5.0:amd64 (1.2.19, 1.2.20), cifs-utils:amd64 (2:6.4-1ubuntu1, 2:6.4-1ubuntu1.1), libgtk-3-bin:amd64 (3.18.9-1ubuntu3.2, 3.18.9-1ubuntu3.3), libgail-3-0:amd64 (3.18.9-1ubuntu3.2, 3.18.9-1ubuntu3.3), apt-utils:amd64 (1.2.19, 1.2.20), thermald:amd64 (1.5-2ubuntu3, 1.5-2ubuntu4), apt-transport-https:amd64 (1.2.19, 1.2.20), libappstream3:amd64 (0.9.4-1ubuntu2, 0.9.4-1ubuntu3)
End-Date: 2017-04-26  13:56:04
```


What is happening is basically, when booting, the share is correctly mounted and I can access it, but after a while (30min - 1h), the share is stuck and if I want to access it, it hangs.
The only way I found to stop the "hanging" is to do a 
```
sudo umount -lf /mount/point
```


I have the following VMs running on a VMware.
- Ubuntu 16.04.2 LTS (GNU/Linux 4.4.0-75-generic x86_64)
- Windows 10

I am mounting a shared folder from Windows 10 to my Ubuntu, below is my /etc/fstab
```

root@frontierland:/var/log# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=296ce9b1-ad77-4099-81d5-2a8825573b23 /               ext4    errors=remount-ro 0       1


//fantasyland/Media  /home/mickey/WindowsShare  cifs  _netdev,credentials=/home/mickey/.smbcredentials,iocharset=utf8,sec=ntlm,nosetuids,noperm  0  0
```


I found out that I have a lot of messages like this in my syslog

```
Apr 26 15:43:55 frontierland kernel: [ 6240.153417] INFO: task mount.cifs:9755 blocked for more than 120 seconds.Apr 26 15:43:55 frontierland kernel: [ 6240.153421]       Not tainted 4.4.0-75-generic #96-Ubuntu
Apr 26 15:43:55 frontierland kernel: [ 6240.153422] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Apr 26 15:43:55 frontierland kernel: [ 6240.153423] mount.cifs      D ffff880135c3fbe8     0  9755      1 0x00000004
Apr 26 15:43:55 frontierland kernel: [ 6240.153426]  ffff880135c3fbe8 ffff8801368fecb8 ffff880138688e00 ffff8800b65faa00
Apr 26 15:43:55 frontierland kernel: [ 6240.153428]  ffff880135c40000 ffff8800ba19c624 ffff8800b65faa00 00000000ffffffff
Apr 26 15:43:55 frontierland kernel: [ 6240.153430]  ffff8800ba19c628 ffff880135c3fc00 ffffffff81837845 ffff8800ba19c620
Apr 26 15:43:55 frontierland kernel: [ 6240.153431] Call Trace:
Apr 26 15:43:55 frontierland kernel: [ 6240.153436]  [<ffffffff81837845>] schedule+0x35/0x80
Apr 26 15:43:55 frontierland kernel: [ 6240.153438]  [<ffffffff81837aee>] schedule_preempt_disabled+0xe/0x10
Apr 26 15:43:55 frontierland kernel: [ 6240.153440]  [<ffffffff81839729>] __mutex_lock_slowpath+0xb9/0x130
Apr 26 15:43:55 frontierland kernel: [ 6240.153442]  [<ffffffff818397bf>] mutex_lock+0x1f/0x30
Apr 26 15:43:55 frontierland kernel: [ 6240.153459]  [<ffffffffc02e9a8e>] cifs_get_smb_ses+0x22e/0x690 [cifs]
Apr 26 15:43:55 frontierland kernel: [ 6240.153468]  [<ffffffffc02ea54b>] cifs_mount+0x65b/0xdc0 [cifs]
Apr 26 15:43:55 frontierland kernel: [ 6240.153471]  [<ffffffff811f0ef4>] ? __kmalloc_track_caller+0x1b4/0x250
Apr 26 15:43:55 frontierland kernel: [ 6240.153478]  [<ffffffffc02d58c8>] cifs_do_mount+0x118/0x5c0 [cifs]
Apr 26 15:43:55 frontierland kernel: [ 6240.153480]  [<ffffffff811e2b1c>] ? alloc_pages_current+0x8c/0x110
Apr 26 15:43:55 frontierland kernel: [ 6240.153482]  [<ffffffff81212e98>] mount_fs+0x38/0x160
Apr 26 15:43:55 frontierland kernel: [ 6240.153484]  [<ffffffff8122f527>] vfs_kern_mount+0x67/0x110
Apr 26 15:43:55 frontierland kernel: [ 6240.153486]  [<ffffffff81231bdf>] do_mount+0x25f/0xda0
Apr 26 15:43:55 frontierland kernel: [ 6240.153488]  [<ffffffff81232a5f>] SyS_mount+0x9f/0x100
Apr 26 15:43:55 frontierland kernel: [ 6240.153490]  [<ffffffff8183b972>] entry_SYSCALL_64_fastpath+0x16/0x71
Apr 26 15:45:55 frontierland kernel: [ 6360.152349] INFO: task mount.cifs:9755 blocked for more than 120 seconds.
Apr 26 15:45:55 frontierland kernel: [ 6360.152352]       Not tainted 4.4.0-75-generic #96-Ubuntu
Apr 26 15:45:55 frontierland kernel: [ 6360.152353] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Apr 26 15:45:55 frontierland kernel: [ 6360.152355] mount.cifs      D ffff880135c3fbe8     0  9755      1 0x00000004
Apr 26 15:45:55 frontierland kernel: [ 6360.152358]  ffff880135c3fbe8 ffff8801368fecb8 ffff880138688e00 ffff8800b65faa00
Apr 26 15:45:55 frontierland kernel: [ 6360.152360]  ffff880135c40000 ffff8800ba19c624 ffff8800b65faa00 00000000ffffffff
Apr 26 15:45:55 frontierland kernel: [ 6360.152361]  ffff8800ba19c628 ffff880135c3fc00 ffffffff81837845 ffff8800ba19c620
Apr 26 15:45:55 frontierland kernel: [ 6360.152363] Call Trace:
Apr 26 15:45:55 frontierland kernel: [ 6360.152368]  [<ffffffff81837845>] schedule+0x35/0x80
Apr 26 15:45:55 frontierland kernel: [ 6360.152370]  [<ffffffff81837aee>] schedule_preempt_disabled+0xe/0x10
Apr 26 15:45:55 frontierland kernel: [ 6360.152372]  [<ffffffff81839729>] __mutex_lock_slowpath+0xb9/0x130
Apr 26 15:45:55 frontierland kernel: [ 6360.152373]  [<ffffffff818397bf>] mutex_lock+0x1f/0x30
Apr 26 15:45:55 frontierland kernel: [ 6360.152387]  [<ffffffffc02e9a8e>] cifs_get_smb_ses+0x22e/0x690 [cifs]
Apr 26 15:45:55 frontierland kernel: [ 6360.152396]  [<ffffffffc02ea54b>] cifs_mount+0x65b/0xdc0 [cifs]
Apr 26 15:45:55 frontierland kernel: [ 6360.152399]  [<ffffffff811f0ef4>] ? __kmalloc_track_caller+0x1b4/0x250
Apr 26 15:45:55 frontierland kernel: [ 6360.152405]  [<ffffffffc02d58c8>] cifs_do_mount+0x118/0x5c0 [cifs]
Apr 26 15:45:55 frontierland kernel: [ 6360.152408]  [<ffffffff811e2b1c>] ? alloc_pages_current+0x8c/0x110
Apr 26 15:45:55 frontierland kernel: [ 6360.152410]  [<ffffffff81212e98>] mount_fs+0x38/0x160
Apr 26 15:45:55 frontierland kernel: [ 6360.152412]  [<ffffffff8122f527>] vfs_kern_mount+0x67/0x110
Apr 26 15:45:55 frontierland kernel: [ 6360.152414]  [<ffffffff81231bdf>] do_mount+0x25f/0xda0
Apr 26 15:45:55 frontierland kernel: [ 6360.152416]  [<ffffffff81232a5f>] SyS_mount+0x9f/0x100
Apr 26 15:45:55 frontierland kernel: [ 6360.152418]  [<ffffffff8183b972>] entry_SYSCALL_64_fastpath+0x16/0x71



```


Any idea what I could do to solve this problem or check why it's hanging like this?


Thank you very much for your help!

David

---

### Post by thedavix on 2017-04-27
I found out it's not CIFS-UTILS the problem.
I tried the following

- Did a fresh install of Ubuntu 16.04.2 LTS, after the installation did an apt-get upgrade and dist-upgrade --> Result: got the same issue
- Did a fresh install of Ubuntu 16.04.2 LTS, didn't update anything --> Result: no issue

in both cases the cifs-utils is the same version

```
mickey@frontierland2:~$ apt-cache policy cifs-utilscifs-utils:
  Installed: 2:6.4-1ubuntu1.1
  Candidate: 2:6.4-1ubuntu1.1
  Version table:
 *** 2:6.4-1ubuntu1.1 500
        500 http://ch.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     2:6.4-1ubuntu1 500
        500 http://ch.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
```

Thus my understanding is that it's not cifs-utils causing the issue.. but now I have 89 items to update.. so I need to find which one is causing this problem...

to be continued..

If anyone as more idea now ;-) I'll be happy to hear about it

---

### Post by justinmpowell on 2017-05-02
I have what appears to be the exact same issue, but I don't believe it's on the ubuntu side. 

The issues appeared around April 25th, 2017 after applying patches to my windows 10 system.   The issue appears on all of my ubuntu systems spanning from 14.04 LTS through 16.04 LTS systems that were not patched during the time the issue occurred.

I have since found a very TRASHY workaround by adding the following to crontab.  This makes the systems query the mounts every 5 minutes which appears to prevent them from timing out.
    */5 * * * * /bin/df -h >/dev/null 2>&1

I'm confident it was the security patches on the windows side that caused the issues; however, even after rolling back the patches it was still not resolved (I'm expecting some registry entry somewhere I can't find that is causing this). :mad:

---

### Post by HNmYk3h on 2017-05-02
Over in the Networks sub-forum I posted that I discovered that adding the option vers=3.0 to cifs mounts in fstab fixed share drops and some other problems too. Still not sure yet that it fixes my problems permanently.

---

### Post by justinmpowell on 2017-05-02
> **HNmYk3h said:**
> Over in the Networks sub-forum I posted that I discovered that adding the option vers=3.0 to cifs mounts in fstab fixed share drops and some other problems too. Still not sure yet that it fixes my problems permanently.

I haven't had any issues for the last 2 years--- in fact things have been operating flawlessly (auto reconnects to win 10 shares once they become available again after a reboot, etc) with the following options:

     //server/share /path/to/mountpoint   cifs    uid=XXXX,gid=YYYY,credentials=/path/to/.smbcredentials,iocharset=utf8,sec=ntlm 0 0


If adding the vers=3.0 can get me back to the way things were, I'll be very excited!   Trying this out tonight --- thank you for taking the time to post this as my preliminary tests are looking promising.

---

### Post by thedavix on 2017-05-03
Thank you guys for your replies.

I indeed tried to generate some activities on the share every 5 min, I am doing a "touch /myshare/KeepAlive/check_$(date "+%b_%d_%Y_%H.%M.%S")" , it does reduce this problem but doesn't solve it, as from time to time I'll have a drop of connection during a couple of hours and then back up.

I will try the vers=3.0 in the cifs and will let you know how it goes :-)

---

### Post by justinmpowell on 2017-05-03
I'm about 11 hours in with no issues and no "keep alive" on my test system.  Things are looking good so far!

---

### Post by justinmpowell on 2017-05-03
Over 20 hours on my test system, and 8 hours on my live systems with no issues.   I still believe the issue was on the MS end after the patches; however, this option appears to have returned functionality it's original state.

Current fstab mounts look like this:
    //server.domain/share /path/to/mount   cifs   **vers=3.0**,uid=XXXX,gid=YYYY,credentials=/home/user/.smbcredentials,iocharset=utf8,sec=ntlm 0 0

Thanks again to HNmYk3h for posting the solution, and thedavix for posting the issue.

---

### Post by thedavix on 2017-05-04
I confirm, 

It's been 22hrs, with the solution provided by HNmYk3h and everything works fine by adding vers=3.0 in the fstab mount and without any keep alive every 5 min.

My mount is the following
//servershare  /ShareMount  cifs  **vers=3.0**,credentials=/home/user/.smbcredentials,iocharset=utf8,sec=ntlm,nosetuids,noperm  0  0


Thanks guys for helping in this issue, for me it is solved.

---

### Post by andreigorgan on 2017-05-04
I would just like to add that if you're running a server[FONT=arial][/FONT] with an older version of Windows Server (in this case 2008), you could use [FONT=lucida console][FONT=arial]**vers=2.1** and it should work just as well. See [/FONT][FONT=franklin gothic medium][/FONT][/FONT][this post from Microsoft]("https://blogs.technet.microsoft.com/josebda/2013/10/02/windows-server-2012-r2-which-version-of-the-smb-protocol-smb-1-0-smb-2-0-smb-2-1-smb-3-0-or-smb-3-02-are-you-using/") for supported versions by each OS.

---

### Post by justinmpowell on 2017-05-04
andreigorgan, 

Awesome thanks for sharing!

---

### Post by justinmpowell on 2017-05-10
After 6 days and 11 hours the issue came back on one of my 14.04 LTS systems.   No patches were applied to the OS; however, the microsoft standard patches were deployed in on the windows 10 system (cifs host), but it hadn't yet restarted.

It was awaiting restart after the patch install and now the ubuntu client can not maintain the mounts for more than 15-20 minutes without hanging--- yet appear to be fine from my other 14.04 LTS system.   Going to reboot and let it finish the installation and see if the issue persists.  Anyone else having to revisit this issue?

---

### Post by jphilippou on 2017-05-10
> **HNmYk3h said:**
> Over in the Networks sub-forum I posted that I discovered that adding the option vers=3.0 to cifs mounts in fstab fixed share drops and some other problems too. Still not sure yet that it fixes my problems permanently.

I had the exact same problem on Ubuntu 16.04.2.

 I always get nervous when doing updates on my server. 

Thank God for internet searches and thank you for the solution to this issue!!!

Jim

---

