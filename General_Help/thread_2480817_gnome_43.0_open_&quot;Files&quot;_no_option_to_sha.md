---
title: "gnome 43.0 open &quot;Files&quot; no option to share after right click properties"
date: 2022-11-11
forum: General Help
---

### Post by naiqor0-people on 2022-11-11
Up dated to Ubuntu 21.10 two weeks ago, every thing goes well, can see my win10 laptop and copy files from it, Win10 can see Ubuntu and copy files from it. But  cannot set up a new folder in Ubuntu and mark it as shared, as when i right click the folder and select properties i am not given the option to share the folder. Current shared folders do not show that option in properties either, but win10 can still see them.
How do i get my shared option back again.
Thank you.

---

### Post by TheFu on 2022-11-11
Support for Ubuntu 21.10 ended last June. No security patches have been provided since that time and there are a few remote attacks in the wild. 

Use either 20.04 or 22.04. 

Always, always, run a supported release.  Non-LTS releases only have 6-9 months of support.

---

### Post by maglin2 on 2022-11-11
Guessing that the OP means 22.10 (given gnome 43), perhaps by installing the extension 'nautilus-share'? 
'Nautilus Share allows you to quickly share a folder from the GNOME Nautilus file manager without requiring root access.'
I've never used file share myself, so I haven't tried this out personally.

---

### Post by TheFu on 2022-11-11
[https://www.techrepublic.com/article/share-directories-lan-from-ubuntu-desktop-22-04/](https://www.techrepublic.com/article/share-directories-lan-from-ubuntu-desktop-22-04/) is a reputable website. The 22.04 how-to seems reasonable, though there are some issues with setting up CIFS shares using the GUI method.  Odd things seem to happen in the future.

If the OP wants, we can post how to setup "permanent" CIFS sharing using the safer /etc/samba/smb.conf method. We'd need to know all the clients, however, to specify the fastest, most secure, options, since different clients support different levels of MSFT's CIFS protocol.

If the client devices aren't MS-Windows, there are other methods that are easier, faster, and more secure, available like NFS or sftp or sshfs ... There are clients for sftp for Windows - WinSCP or FileZilla, but NFS provides native access for non-MS-Windows clients with full support of file permissions on a system-to-system level, not user-to-system.  For user-to-system, there's sshfs.

---

### Post by naiqor0-people on 2022-11-11
Thank you for that, it is 22.10 that i run and installing 'nautilus share' solved the problem

---

### Post by maglin2 on 2022-11-12
Good, but I wonder why the nautilus-share extension, which was part of 22.04 default install, is removed with upgrade to 22.10/gnome 43? Suggests perhaps something wasn't working well.
Edit - having read TheFu's post, and its link, again, and also this  [https://discourse.ubuntu.com/t/nautilus-share-fixing-or-removing/3763](https://discourse.ubuntu.com/t/nautilus-share-fixing-or-removing/3763) it seems there have been issues for a while.

---

