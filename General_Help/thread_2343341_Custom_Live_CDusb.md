---
title: "Custom Live CD/usb"
date: 2016-11-15
forum: General Help
---

### Post by weisswilly1985 on 2016-11-15
Hello. I`m new in this, and i need your help. Basically what i`m trying to do, is pretty simple, but i can not make it, i`m to noob.
So, I install Kubuntu, and customize it as i like. Now, How can i create an image of my actual system? 
I do a lot with my operating system, am trying new stuff, and learning. But some times i mess things out. 
I will like to create tow things:
1) A SYSTEM RESTORE POINT, to be used without any usb/cd etc. Just recover from there. 
2) A live usb with that restore point. 

The result that i`m trying to obtain is to eliminate the NOOB problem. Every time that i mess things up, i just restore.
If the things are beyond repair, i will just plug the usb, and reinstall my custom system from there. So...this is it. 
After i finish, i will post my distro, for anybody to see and use, if they like. 
What i`m trying to create is a distro similar to Kali, but on ubuntu kernel. 
The distro will provide minimal pen-testing software like Metasploit, SORT, OpenVAS, wireshark, aircrack, etc.  all with a cool interface.
I will be for people like me, who are trying to learn but they will like an every day use operating system.  
Help a noob please.

---

### Post by yancek on 2016-11-15
I'm not aware of anything like a "Restore Point" for Linux because it usually isn't necessary as most Linux systems don't crash as often as other systems. 
There was software called Remastersys which you could use to create an iso image of an installed system which had size limitations.  Remastersys is no longer being developed but there is software called Systemback which basically does the same thing for newer Ubuntu releases.  Should be in the repositories for Ubuntu.

Two other possibilities are to do backups of things you change before changing, the original configuration file before editing changing, etc.
Do a second full install and use one install to customize and leave the other without changes once set up.

---

### Post by weisswilly1985 on 2016-11-15
Hmmmm.......
So i can not restore but i can create an image of the actual system. One slap, one kiss.
Thank you for that. 
Now, i know how to make an image of the system, for later use or distribution. BUT!
I still can not manage to keep safe from screw-ups. In this case........
I just wonder... what if, i will make a backup copy of my system files only? I mean the core part.
If you will need to backup a system without the additional installed software , what files will YOU backup?
I`m asking, because in this case, i just replace the files. Recovery done!!!! I`m up and running without too much damage. 
If this works, a simple bash can be created to do this. First .sh recovery ? LOL.
How noob and crazy I am??

---

### Post by C.S.Cameron on 2016-11-15
Have a look at **mkusb**, I think it restores O/S image files.

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

or **One Button Installer** might be more specific to your needs.

[https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)

---

### Post by ian-weisser on 2016-11-15
What the OP is asking for is simple to describe, but extraordinarily complex to execute.

If you are unskilled at restoring your system from a backup, then use a VM. Those have snapshots.

---

### Post by weisswilly1985 on 2016-11-16
Ok, i have a strage fix for my problem.
Just do an archive with the system files, and replace them if crashed. My problem is, WHAT files to put in the achive?
For an example, if dpkg is crashed. or any other packets and dependencys...how i back those up?
My simple solution will be to take kubuntu-desktop (in my case) and redeploy. But i will like to do it without the softwares that comes with the pack.
I have no interest in firefox, dolphin etc...just the core files. That ones that they crash is good bye.
Which folders i need to put in the archive?
The fix is simple, just go on to grub terminal, login as root and extract the files. BUT WHAT FILES DO I NEED TO BACKUp? What folders?

---

### Post by ian-weisser on 2016-11-16
Yes, that's exactly what I mean by "simple to describe, but extraordinarily complex to execute."
Really, play with a VM. Much easier.

---

