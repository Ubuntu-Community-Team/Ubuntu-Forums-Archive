---
title: "system sounds won't work"
date: 2007-10-23
forum: General Help
---

### Post by 127.0.0.1 on 2007-10-23
hello Ubuntu forums, i am currently running a Realtek sound card with i don't know what drivers. and am running Ubuntu 7.10 Gutsy Gibbion. some of my system sounds arn't working, like error pop-up messages, log out tone, the only system sounds that do work are the login tone, and the start up sound (question.wav) Instead of these sounds i get the system beep, witch i disabled when it got annoying.

others like, beep, siren, and clink to name a few arn't working, When i play them in the sound settings window they will work, however when i logout, or example, the logout tone will not play. This is a small problem but it would be nice to have fixed thanks.
:popcorn:

Oh, and here is the site for drivers, i dont know how to install them XD [http://www.realtek.com.tw/default.aspx]("http://www.realtek.com.tw/default.aspx")

---

### Post by yyz on 2007-10-23
Hi 127.0.0.1, I wouldn't want to sabotage your thread, but I'm having the same problem on Windows (XP). I am using an AC97 Realtek sound-card, and my system currently has no sound at all. Its on XP, anybody know how to fix it?

I installed drivers from their official websites, but the problem still presists.

Help is appreciated :)

---

### Post by 127.0.0.1 on 2007-10-24
> **yyz said:**
> Hi 127.0.0.1, I wouldn't want to sabotage your thread, but I'm having the same problem on Windows (XP). I am using an AC97 Realtek sound-card, and my system currently has no sound at all. Its on XP, anybody know how to fix it?

I installed drivers from their official websites, but the problem still presists.

Help is appreciated :)

well i reinstalled drivers, still no system sounds here, as for XP i had that problem a long time ago and i just reinstalled drivers and it worked. I hear that reltek sound cards have lots of problems with them some times.

help please!

---

### Post by unebaguettesvp on 2007-10-24
i was having a similar problem. here is my launchpad bug that i submitted. see if there is anything similar.

[https://bugs.launchpad.net/ubuntu/+bug/121433]("https://bugs.launchpad.net/ubuntu/+bug/121433")

i also have a realtek audio output, but it's on my motherboard. i don't use that. i use an ati sound card.

my problem was related to ubuntu using the sound device, /dev/dsp, WHICH DIDN'T EXIST! i have had to use /dev/dsp3 and /dev/dsp1 for my applications that require sound. but for edgy and feisty, i never had any system sounds!

do:

ls /dev/*dsp*

and see what you get. if you don't have /dev/dsp listed, then that's my guess as to what your problem is. good luck.

---

### Post by mdurham on 2007-10-24
I think it's a well known problem that system sound doesn't work, it's something to do with the removal of ESD and the transition to Pulse Audio, or so I believe. Seems a bit strange that they release a distro without system sounds.
Cheers, Mike

---

### Post by Crafty Kisses on 2007-10-24
> **127.0.0.1 said:**
> hello Ubuntu forums, i am currently running a Realtek sound card with i don't know what drivers. and am running Ubuntu 7.10 Gutsy Gibbion. some of my system sounds arn't working, like error pop-up messages, log out tone, the only system sounds that do work are the login tone, and the start up sound (question.wav) Instead of these sounds i get the system beep, witch i disabled when it got annoying.

others like, beep, siren, and clink to name a few arn't working, When i play them in the sound settings window they will work, however when i logout, or example, the logout tone will not play. This is a small problem but it would be nice to have fixed thanks.
:popcorn:

Oh, and here is the site for drivers, i dont know how to install them XD [http://www.realtek.com.tw/default.aspx]("http://www.realtek.com.tw/default.aspx")
Post the following output:
```
lspci
```

---

### Post by 127.0.0.1 on 2007-10-25
> **Codename said:**
> Post the following output:
```
lspci
```

```
matt@homebox:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 RAID bus controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA RAID Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
01:03.0 Network controller: Texas Instruments ACX 100 22Mbps Wireless Interface
01:04.0 Communication controller: Conexant HSF 56k Data/Fax Modem
01:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)
matt@homebox:~$ 

```

> i was having a similar problem. here is my launchpad bug that i submitted. see if there is anything similar.

[https://bugs.launchpad.net/ubuntu/+bug/121433](https://bugs.launchpad.net/ubuntu/+bug/121433)

i also have a realtek audio output, but it's on my motherboard. i don't use that. i use an ati sound card.

my problem was related to ubuntu using the sound device, /dev/dsp, WHICH DIDN'T EXIST! i have had to use /dev/dsp3 and /dev/dsp1 for my applications that require sound. but for edgy and feisty, i never had any system sounds!

do:

ls /dev/*dsp*

and see what you get. if you don't have /dev/dsp listed, then that's my guess as to what your problem is. good luck.
thats some what is like what i am having, only the start up drum sound always works, (Question.wav) but none of the other system sounds work (error meesages, pop-up menus, log-out sound, ect.) instead they are replaced with the system beep, i turned the system beep off because it was getting annoying though.

---

### Post by dahlheim on 2007-10-26
i am still using a gutsy beta at this point, having reverted to it because i wasn't getting any sound at all with a newer, still pre-release candidate.  with the beta, i was getting all sound except system sounds, like the original poster.  i just managed to fix that with 
sudo apt-get install esound
simple as that, i hope this helps somebody.
(i have an xps-m1210 btw)

---

### Post by Therion on 2007-10-26
See if this post helps: [[COLOR="Blue"]Comprehensive Sound Problem Solution Guide[/COLOR]]("http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide")

---

### Post by mdurham on 2007-10-26
> **dahlheim said:**
> i am still using a gutsy beta at this point, having reverted to it because i wasn't getting any sound at all with a newer, still pre-release candidate.  with the beta, i was getting all sound except system sounds, like the original poster.  i just managed to fix that with 
sudo apt-get install esound
simple as that, i hope this helps somebody.
(i have an xps-m1210 btw)

Yes dahlheim, it did help me thanks. I tried this (plus lots of other things) a few weeks ago but it didn't work then. Now my system sound is working again.
Have you ever noticed that the 'clink' sound, sounds like "boing" and the 'boing' sound, sounds like a "clink"?
Cheers, Mike

---

### Post by dahlheim on 2007-10-27
funny you should mention that.  in fact, i do believe, when i had tried the pre-release gutsy updated i referred to above, i subsequently tried to install esound also without success.  kind of makes me want to update to 7.10 final and try again (but not enough to actually do it- i'll wait for more problems to be ironed out since my current install is working great).  yes, the system sound names don't make much sense to me, but putting the "clink" sounding one on checkbox sounds and the "bonk" sounding ones on buttons feels good to me in terms of general mouse feedback.

> **mdurham said:**
> Yes dahlheim, it did help me thanks. I tried this (plus lots of other things) a few weeks ago but it didn't work then. Now my system sound is working again.
Have you ever noticed that the 'clink' sound, sounds like "boing" and the 'boing' sound, sounds like a "clink"?
Cheers, Mike

---

### Post by mdurham on 2007-10-27
dahlheim, I don't think that installing the 7.10 final release will make any difference, I tried it and it had exactly the same problem, no system sound, even on the live CD. I would suggest that if it works now, stay with that install! 
Thanks again, Mike

---

### Post by 127.0.0.1 on 2007-10-27
> **mdurham said:**
> Yes dahlheim, it did help me thanks. I tried this (plus lots of other things) a few weeks ago but it didn't work then. Now my system sound is working again.
Have you ever noticed that the 'clink' sound, sounds like "boing" and the 'boing' sound, sounds like a "clink"?
Cheers, Mike

didnt work for me, still getting system beeb instead of system sounds. =\

---

### Post by unebaguettesvp on 2007-11-02
the command:

sudo apt-get install esound

worked for me! now, i get system sounds! thanks dahlheim!

---

### Post by dcstar on 2007-11-02
> **unebaguettesvp said:**
> the command:

sudo apt-get install esound

worked for me! now, i get system sounds! thanks dahlheim!

Or just use Synaptic to install the** esound** package - as people do with all others........

Anyway, it is good that this Gutsy annoyance had such a simple fix, one for the Gutsy FAQs...   :)

---

### Post by jespdj on 2007-11-07
Also thanks - Installing esound and logging out and in again worked for me too.

---

### Post by RgnKjnVA on 2007-11-19
Thank you! I can remove "No system sounds" from my list of annoyances in Gutsy. =o )

---

### Post by 127.0.0.1 on 2007-11-21
awesome it worked :D now i have a bigger problem...[http://ubuntuforums.org/showthread.php?t=617745](http://ubuntuforums.org/showthread.php?t=617745)

---

### Post by xboxmods3077 on 2008-03-26
Esound worked for me too. You guys rock!!! Hey, Do you guys think that not having esound installed would stop compiz from starting?

---

### Post by RgnKjnVA on 2008-03-26
I seriously doubt it. I don't think any sound components are required for start up. Are you seeing any errors?

---

### Post by richbl on 2008-03-28
> **dahlheim said:**
> i am still using a gutsy beta at this point, having reverted to it because i wasn't getting any sound at all with a newer, still pre-release candidate.  with the beta, i was getting all sound except system sounds, like the original poster.  i just managed to fix that with 
sudo apt-get install esound
simple as that, i hope this helps somebody.
(i have an xps-m1210 btw)

I, for one, can confirm that this appears to solve my problem. Previously, I wasn't getting system sounds, though startup/shutdown sounds always seemed to work just fine. Go figure.

In any case, thanks for the solution.

---

### Post by m3alnemer on 2008-04-02
> **dahlheim said:**
> i am still using a gutsy beta at this point, having reverted to it because i wasn't getting any sound at all with a newer, still pre-release candidate.  with the beta, i was getting all sound except system sounds, like the original poster.  i just managed to fix that with 
sudo apt-get install esound
simple as that, i hope this helps somebody.
(i have an xps-m1210 btw)

This worked great
thanks

m3alnemer

---

### Post by stmcc on 2008-06-26
System sounds seem to be controlled in Gnome ALSA Mixer, tritech id 3, with Master = high , PCM=MAX ,WAVE=MAX
mac

---

