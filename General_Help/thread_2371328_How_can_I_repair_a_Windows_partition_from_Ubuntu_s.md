---
title: "How can I repair a Windows partition from Ubuntu since I can't login to Windows?"
date: 2017-09-13
forum: General Help
---

### Post by Bobby_James on 2017-09-13
I have a dual boot 16.04 / Windows 8 system. For some reason, I can no longer load Windows (the computer just hangs) and can only access the contents of Windows from Ubuntu by mounting in read only status. Trying in read write status generates:

The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda4': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option

I can mount with ro but I want to copy content to my Ubuntu partition. I cannot shutdown Windows because I cannot login. 

What can I do - if anything - from Ubuntu? Thanks.

---

### Post by andrew772 on 2017-09-13
I also have a dual-booting machine and Windows was hanging. I tried everything until I finally managed to fix Windows by using [https://youtu.be/2f-GorXWkoc](https://youtu.be/2f-GorXWkoc) . It's for Windows 10 but hopefully will help you too.

---

### Post by oldfred on 2017-09-13
If Windows 8 and installed by vendor, it must be UEFI.
You then should be able to directly boot from UEFI boot menu, often f10 or f12 check your manual.

Windows fast start up will block grub from booting Windows as grub only boots working Windows and the Linux NTFS driver will not default mount hibernated Windows to prevent damage.

Windows also turns fast start up back on with some updates, which normally is in background so you do not know setting changed unless you check.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

