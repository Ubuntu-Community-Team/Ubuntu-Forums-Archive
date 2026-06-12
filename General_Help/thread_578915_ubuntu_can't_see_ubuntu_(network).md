---
title: "ubuntu can't see ubuntu (network)"
date: 2007-10-17
forum: General Help
---

### Post by delfick on 2007-10-17
hello

I have a laptop and a desktop computer both with ubuntu linux installed.

Both have access to my network (desktop through wire, laptop through wireless)

But I can't figure out how to see one computer from the other.

The closest I get is to go to network:/// in nautilus on the laptop, where I can see the computer

But when I click on it, there isn't any folders in there.

On the computer, when I go to network:/// I can't see the laptop but I do see the desktop computer and inside that is the shared folder I have made (a random folder in my home folder)....

So I was wondering if anyone could help me figure out how to make the two computers see each other ??

thnx :D

---

### Post by scrooge_74 on 2007-10-17
On Linux things are a little different.

What you are doing is mostly to see XP machines using samba, you could configure samba servers in both machines so they act as XP shared folders.

But in Linux, since you are always thinking on security first what you do is mount drives (or folders) using NFS, or through a ssh connection

Also to share a printer you dont do it like in Windows where you need to share the printer you see on a machine, you use CUPS 

A couple of threads to give you an idea on the subject

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)
[https://help.ubuntu.com/community/InternetAndNetworking](https://help.ubuntu.com/community/InternetAndNetworking)
[http://doc.gwos.org/index.php/Share_files_using_Samba](http://doc.gwos.org/index.php/Share_files_using_Samba)

---

### Post by delfick on 2007-10-19
thankyou very much for that :D

it worked :D

though unfortunately, I need to share an NTFS drive from my laptop, so that the computer can see it, but it tells me that that drive doesn't support nfs, so how would I go about doing that ??

thnx :D

(also, is it possible for exported folders to come up in network:/// of the other machine ??)

---

### Post by dayvy on 2007-10-19
Try the following:

-open nautilus (file manager)
-click "file" (if gutsy) or "go" (if earlier version)
-click "Connect to Server"
-click  "Service type" and choose "Windows share"
-type in the relevant connection information (if you type in a computer name instead of an IP address, make sure it is mapped with an IP address in the /etc/hosts file
-this will create an icon on your desktop and also in nautilus
-when you double-click this icon it will ask you for the password, enter your password for the windows share
-provided all the information is right you'll have access to your windows share

Note: This is a really handy feature in nautilus. I use it all the time for windows shares and to other linux boxes via ssh.

---

