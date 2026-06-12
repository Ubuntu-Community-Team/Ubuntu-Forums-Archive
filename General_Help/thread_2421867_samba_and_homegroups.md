---
title: "samba and homegroups"
date: 2019-06-28
forum: General Help
---

### Post by ccor58 on 2019-06-28
What has changed, I presume in Windows world, such that samba does not connect with correct permissions to windows workgroups. I set workgroup name the same in samba as in the windows PC properties window but on windows PC's that are more current and using homegroups there seems to be something not allowing smb shared access properly. UserID's and passwords are the same on ubuntu as windows boxes yet workgroup function not as they once were under older versions of windows like XP or Vista. 7,8, & 10 with emphasis on homegroups appears to need an extra trick to get them playing nice together.

Thanks

---

### Post by HermanAB on 2019-06-28
Note that Windows natively supports two types of networked file systems: SMB/CIFS and Anonymous FTP.

If you want a simple, no nonsense file server, the venerable old FTP is still the best.

Some people will immediately scream that FTP is not secure.  Well, neither is SMB/CIFS.  The difference is that Anonymous FTP doesn't even pretend to be secure.

So, if you want a home file server that is pretty much zero maintenance and just works, then install vsftpd on a Linux machine, configure it for anonymous read/write and be done with it.  You won't be sorry.

---

### Post by ccor58 on 2019-06-28
I use NFS file systems for important file shares that I keep permissions and user specific access. It works great for linux boxes no problem. Problem arises when sharing printers and file shares with windoze boxes and laptops. Then samba needed and normally I used to just specify the same workgroup name but with latest variants of windows embracing the homegroup workgroup then tend not to play nice. I had once understood that homegroups, although they could be named the same as snb workgroup names they used IPv6 protocols and thus problems arise. Likewise using CUPS to manage and share printers is a pain as often an update for linux would badly affect the smb sharing of CUPS managed printers; so best result was to just use samba and windows printer sharing on the linux box. FTP might partially solve file sharing but not network access to printer.

---

### Post by Morbius1 on 2019-06-28
There is no such thing as a HomeGroup in Linux or MacOS. There is no such thing as a HomeGroup in Windows 10 as of build 1803: [https://support.microsoft.com/en-us/help/4091368/windows-10-homegroup-removed](https://support.microsoft.com/en-us/help/4091368/windows-10-homegroup-removed)

---

### Post by HermanAB on 2019-06-28
Technically, you don't need Samba to print from Windows.  CUPS effectively makes any printer a network printer and you can simply send a PS or PDF file to a CUPS printer to have it printed for you.  There are many ways to do that and while Samba may make it a little more convenient, you don't really need it.

---

