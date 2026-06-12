---
title: "ipod touch problems"
date: 2007-12-26
forum: General Help
---

### Post by evanct on 2007-12-26
So i got an ipod touch with firmware 1.1.2 for christmas. which is great, except that ubuntu feisty thinks it's a camera and thus will not mount it. I've activated it by plugging it into a friend's Vista, and since then i have successfully jailbroken it and installed ssh. what do i do from here? i've tried looking online but have found no clear answers to my problem. can anyone help?

---

### Post by evanct on 2007-12-26
alright, so i'm trying to set up a mount manually. i access ssh via

ssh root@<my ipod's ip address>

type the correct password, and this appears on a new line:

-sh-32#

if if try to type anything, regardless of what it is, on the third keystroke the connection automatically closes.

---

### Post by tgalati4 on 2007-12-26
I don't remember the exact syntax, but put a file on your iTouch in the root directory called:

.is_a_dap_player

My problem with the iTouch is that it won't play/stream mp3's from a music server (gnump3d) through Safari.  It seems to only play music through the iTunes music store or music loaded through iTunes.  What is the purpose of having WiFi and Safari then on this device?

Correction:  Put a blank file in the root directory of the player called *.is_audio_player*

You can also add a file called *autorun *.  Make in executable (sudo chmod +x autorun) and put whatever commands that you want to run when it's plugged in.  You have to enable automatic running of scripts in the Gnome tool Removable Media.

So I guess the iTouch doesn't show up automatically as removable storage in Linux?  My issue with the iTouch is that it won't play music from my music server:  
[B]
[http://wofmusic.homelinux.org:9000/](http://wofmusic.homelinux.org:9000/)[/B]

---

### Post by evanct on 2007-12-26
anyone else?

---

### Post by Metaljaz on 2007-12-30
Read through this site by Lifehacker and see if it helps. Maybe missed something:

[http://lifehacker.com/software/feature/how-to-install-thirdparty-apps-on-your-new-iphone-or-ipod-touch-337863.php](http://lifehacker.com/software/feature/how-to-install-thirdparty-apps-on-your-new-iphone-or-ipod-touch-337863.php)

---

### Post by ntetreau on 2008-01-02
Hi guys, there is a "near"complete solution for ipod touch and iphone users on Ubuntu.  Please take a look at this wiki
[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)
if you are having problems, please read and post to this thread:
[http://ubuntuforums.org/showthread.php?t=588246&highlight=iphone](http://ubuntuforums.org/showthread.php?t=588246&highlight=iphone)

---

