---
title: "encrypted persistent overlay ( writable ) partition for live stick, possible?"
date: 2023-06-03
forum: General Help
---

### Post by newbie-03 on 2023-06-03
hi, :-) , I'm new here, pls. don't rip my head if not fully respecting not known habits,  
   
I'm used to a setup with a 'normal' live stick with a separate persistence / overlay partition,  
'writable' at ubuntu, works,  As that partiton often contains sensitive data I'd like it encrypted,  
luks - cryptsetup ... Kali has such option as quasi default, during boot asks for the 
password for the enccrypted partition.  
I couldn't convince ubuntu to  
search for and open an encrypted partition during boot. Anybody a tip for me?  
It's wanted to work from a - if necessary patched - live stick!  
( patched live stick: to automatically open an unencrytped overlay partition I had to patch  
'maybe-ubiquity' to 'persistent    ' in the ISO file, such is no problem.)

---

### Post by sudodus on 2023-06-03
A persistent live system is good for many tasks, but Ubuntu does not provide a solution with encryption.

When you want encryption, I suggest that you create an installed system with encryption, there is an option during installation for that purpose.

There are several tutorials for this purpose, for example [this one (1)](https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step) and [this one (2)](https://askubuntu.com/questions/1403792/how-to-create-a-full-install-of-ubuntu-22-04-to-usb-device-step-by-step). You can find several answers by the same author via the internet.

[hr][/hr]
Please notice that a USB pendrive might wear out and suddenly die, when used like this. I would recommend that you use an SSD (connected via USB). It is not only more reliable but also much faster, particularly for write operations.

---

### Post by newbie-03 on 2023-06-04
:-) thanks for reply,  
   
> but Ubuntu does not provide a solution with encryption.  
   
:-(  -  let's say 'enhancement request', 'Kali' serves as practical example.  
[ edit ] other options: [https://superuser.com/questions/379890/looking-for-an-encrypted-persistent-and-live-linux-distro-preferably-with-tor](https://superuser.com/questions/379890/looking-for-an-encrypted-persistent-and-live-linux-distro-preferably-with-tor) [ /edit ]  

> I suggest that you create an installed system with encryption,  
   
for simplicity, and to provide easy test and try for others, I'd like the pendrive solution.  
   
> Please notice that a USB pendrive might wear out and suddenly die,  
    
YES, I've already lost some sticks, long ones due to breakage, other by 'bricking',  
esp. from a company 'I.....o', mostly one try with 'disks' benchmark, and then return to vendor.  
At this moment in time I'm quite happy with very slim sticks from 'S.....k', they are  
'plug and stay' size, are fast, become hot! but sustain due to thermal throtteling  
( 100MB/s start speed, going down to ~50 at about 2 - 3 GB written ). That's sufficient  
for my use, I see nearly no difference to an m2 disk, assume the setup holds most in memory,  
XFCE monitor shows very moderate stick use even in compiling bigger projects.

---

### Post by sudodus on 2023-06-04
You can try to make a persistent live drive with encryption according to [this method by F. Hauri](https://unix.stackexchange.com/questions/118965/how-to-create-a-debian-live-usb-with-persistence/538665#538665). Scroll down to the paragraph 'Debian live with encrypted persistence'. It is made for Debian, but you might succeed after some (minor?) modifications for Ubuntu.

You can also try with an installed Ubuntu Desktop or Lubuntu or Xubuntu system, installed like into an internal drive, but in this case installed into a USB drive (according to the links in my first post), I think this method is more straightforward, and should be portable enough between computers where the linux built-in drivers work (in other words in computers without problematic graphics and/or wifi chips/cards).

---

### Post by newbie-03 on 2023-06-05
:-)  thank you for the link, looks like good source to learn but will require some time,  
in general I stay with the idea / proposal ubuntu should try to provide such as general option.

---

### Post by sudodus on 2023-06-05
The Ubuntu developers seldom visit the Ubuntu Forums. Here we are volunteers, users who try to help other users. If you want to reach the Ubuntu developers I can suggest two ways,

1. Write a bug report at [Launchpad](https://launchpad.net/) (bug reports are not only focusing on bugs but you can also suggest improvements).

2. Start a 'new topic' thread at [Ubuntu Discourse](https://discourse.ubuntu.com/)

---

### Post by newbie-03 on 2023-07-17
hi, 
launchpad likes to nag me with '
**Oops!**

                    Sorry, something just went wrong in Launchpad.         ',  
  
and discourse, One-login and others are confusing me in a way that I think they don't  
want new contributors, I don't want to need to keep track of and investigate about  
the nesting of options / websites / communities ...  
  
If you like to do me - and the community - a favor use your experience and place at  
appropriate places:  
1.) 'live stick' is a good option, hardware independent, fast operation in ram, saves the stick from wear and tear ... 
2.) persistence is a must for real live use,  
3.) encrypting private data is a must on devices which might get lost or stolen,  
4.) 'overlay' is much better than 'home directory', because it preserves also settings, package installs ...  
5.) 'overlay' seems to me to also operate in ram mostly, thus fast and not ruining the stick,  
6.) ubuntu has advantages over others in points like 4k screen adaption ... I'd like to use, but lack of encryption is a blocker,  
7.) it works like a charm in e.g. Kali or Parrot, ubuntu needs to keep up ... IMHO ...

---

