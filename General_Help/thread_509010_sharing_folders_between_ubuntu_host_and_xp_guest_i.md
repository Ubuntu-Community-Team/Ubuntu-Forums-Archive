---
title: "sharing folders between ubuntu host and xp guest in virtualbox"
date: 2007-07-24
forum: General Help
---

### Post by geekphreak on 2007-07-24
OK, I realize this gets asked a lot, but I need to clarify something: I run XP in Virtualbox on Feistyn and I want to set up shared folders. I followed the instructions from the Virtualbox manual and I have the following questions:
1. Do I need to have Samba on Ubuntu for this to work?
 - I have shared folders with a virtual machine through Samba before, but I was under impression that Virtualbox does not need Samba for shared folders to work.
2. Do I need to have same usernames and passwords in Ubuntu and XP virtual machine?
 - When I try to connect to the share, I am prompted for a username and password, but I am unable to connect regardless of whether II enter my Ubuntu host's or XP virtual machine's credentials.
3. If the only way to get this to work is through Samba, will I need to be connected to the Internet all the time? 

Thanks for your help

---

### Post by HermanAB on 2007-07-24
Windows has a built-in SMB server called, drum roll, wait for it......... 'server' - duh.

Server is launched when you enable 'File and Printer Sharing' and once running is well nigh impossible to ever stop again - well except from the DOS command line using 'net stop server'.

Soooooo, you need a SMB server, whether you run it on Windoze or on Linux is your choice.

'Hope that helps!

Herman

---

### Post by HermanAB on 2007-07-24
Well actually, you don't necessarily need a SMB server - you could go to filezilla.sourceforge.net and get a FTP server for Windoze, or use proftpd or vsftpd on Linux and use the Filezilla client on Windoze.  Just depends on what you wanna do.

FTP is more efficient and more clunky.  Samba is more fancy and schloooowww. 

Your call!

H.

---

### Post by HermanAB on 2007-07-24
BTW, if you have connection issues, check your firewall settings.  

Test the connectivity with telnet:
telnet wh.er.ev.er 445

Your username and password is the one used on the server side, because it is the server that is trying to authenticate you.

Maybe see this:
[http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

Cheers,

H.

---

### Post by swisscow on 2007-07-25
I have set this up this week from a clean install and haven't put in Samba or anything.

I just did these steps.

#install xp in virtualbox
#install the virtualbox additions
#made a folder in my home folder on ubuntu called virtualboxshare
#without xp running, went to settings in the xp machine, shared folders and navigated to this folder
#boot xp, then click start, run and entered the command:

```
net use x: \\vboxsvr\virtualboxshare
```

#Give it a moment and then in My Computer in XP you should have a shared folder.

Good luck

---

### Post by andrewoftheelves on 2007-10-16
> **swisscow said:**
> I have set this up this week from a clean install and haven't put in Samba or anything.

I just did these steps.

#install xp in virtualbox
#install the virtualbox additions
#made a folder in my home folder on ubuntu called virtualboxshare
#without xp running, went to settings in the xp machine, shared folders and navigated to this folder
#boot xp, then click start, run and entered the command:

```
net use x: \\vboxsvr\virtualboxshare
```

#Give it a moment and then in My Computer in XP you should have a shared folder.

Good luck

i did all of this (except the virtualbox additions) and it cant find the network path, so im guessing its the virtual box additions that im missing that is the problem, what additions do i need?

---

### Post by hamster_billy on 2007-10-17
In the Devices menu of the virtual machine window you'll find Install Guest Additions at the bottom. Once you've done this it should work fine.

---

### Post by andrewoftheelves on 2007-10-18
thanks, yeah i eventually figured that out on my own, but i couldnt figure out where that option was untill reciently.

---

### Post by Fanless_Puppy_Fan on 2007-11-18
Thanks swisscow. I'm just posting to let anyone looking know that this works flawlessly in my gutsy-win2k setup. There's a lot of old posts floating around out there that seem to make this a lot more complicated than it is.

---

### Post by adza on 2008-03-26
Another great post... thanks guys! perfect!

---

