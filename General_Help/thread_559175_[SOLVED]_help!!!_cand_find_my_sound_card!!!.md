---
title: "[SOLVED] help!!! cand find my sound card!!!"
date: 2007-09-24
forum: General Help
---

### Post by S.S.S.P5 on 2007-09-24
hi, Im brand new to Ubuntu or linux and Im really trying to like it, but Im really having problems getting my system to recognize the sound card, the card on the mainboard works but it wont even see the pci sound card even after I disable the onboard one in the BIOS. the reason I wanted linux was for music mixing ect, and not using the sound card is a real let down as the sound off of the board is choppy and jarbled.

I have the low latency kernel uo and runnung, the jackd server runnung finally after a week of reloading the hard drives and figuring out xserver a bunch of times, 10 times in recovery mode, and i still cant get this figured out, i really want to see how great this os/can be please help!

I have a 1.6 intel p4
asrock mb
creativelabs live! sb0200
ati radeon 9200 se (currently recognized but still not allowing desktop effects or beryl {2nd priority})
1.5 gig of ram
bla bla bla

tx in advance

---

### Post by S.S.S.P5 on 2007-09-24
i also get this message when i try to open the vol. controll 


The volume control did not find any elements and/or devices to control. This means either that you do not have the right GStreamer plugins installed, or that you do not have a sound card configured.

---

### Post by Maestro23 on 2007-09-24
This thread might help: [http://ubuntuforums.org/showthread.php?t=146505&highlight=disable+onboard+soundcard](http://ubuntuforums.org/showthread.php?t=146505&highlight=disable+onboard+soundcard)

---

### Post by S.S.S.P5 on 2007-09-25
tx for the reply, this is what i get

james@james-desktop:~$ cat /proc/asound/cards
cat: /proc/asound/cards: No such file or directory
james@james-desktop:~$

---

### Post by Maestro23 on 2007-09-25
> **S.S.S.P5 said:**
> tx for the reply, this is what i get

james@james-desktop:~$ cat /proc/asound/cards
cat: /proc/asound/cards: No such file or directory
james@james-desktop:~$

What is in your asound directory?

> cd /proc/asound

ls (lists files in asound directory).  


Paste output here.

---

### Post by S.S.S.P5 on 2007-09-25
ok here goes...

james@james-desktop:~$ cd /proc/sound
bash: cd: /proc/sound: No such file or directory
james@james-desktop:~$ 


not good, right?

---

### Post by S.S.S.P5 on 2007-09-25
oh btw, i disabled the on board sound card in the BIOS

---

### Post by Maestro23 on 2007-09-25
> **S.S.S.P5 said:**
> ok here goes...

james@james-desktop:~$ cd /proc/sound
bash: cd: /proc/sound: No such file or directory
james@james-desktop:~$ 


not good, right?

Do you have an "asound" directory under /proc ?

Check my previous post.

---

### Post by S.S.S.P5 on 2007-09-25
ok plz bear with me as this is still really new to me, how do you do this? the terminal says no file or directory when i type-


james@james-desktop:~$ cd /proc/sound
bash: cd: /proc/sound: No such file or directory


Im thinking that im doing this wrong

---

### Post by Maestro23 on 2007-09-25
> **S.S.S.P5 said:**
> ok plz bear with me as this is still really new to me, how do you do this? the terminal says no file or directory when i type-


james@james-desktop:~$ cd /proc/sound
bash: cd: /proc/sound: No such file or directory


Im thinking that im doing this wrong

cd /proc/**asound**

---

### Post by S.S.S.P5 on 2007-09-25
sorry bout that... heres what i get



james@james-desktop:~$ cd /proc/asound
bash: cd: /proc/asound: No such file or directory
james@james-desktop:~$

---

### Post by Maestro23 on 2007-09-25
> **S.S.S.P5 said:**
> sorry bout that... heres what i get



james@james-desktop:~$ cd /proc/asound
bash: cd: /proc/asound: No such file or directory
james@james-desktop:~$

Hmm.. Are you using alsa sound? Might be because you disabled the on-board sound.  Try enabling the on-board sound again and check that directory.  (Reboot, Enable the on-board sound in BIOS).

---

### Post by akumudzi on 2007-09-25
I had this problem using a USB Logitech headset. Ubuntu won't switch between the computer soundcard and my Logitech USB headset automatically. 

I know it might seem obvious but have you checked; System -> Preferences -> Sound under "Default Sound Card" in the Sound Preferences dialog? You might have the wrong sound card (onboard one) listed there.

---

### Post by S.S.S.P5 on 2007-09-25
o kre-enabled the onboard card this is what i get...

james@james-desktop:~$ cd /proc/asound
james@james-desktop:/proc/asound$ asound

---

### Post by Maestro23 on 2007-09-25
> **S.S.S.P5 said:**
> o kre-enabled the onboard card this is what i get...

james@james-desktop:~$ cd /proc/asound
james@james-desktop:/proc/asound$ asound

What is listed inside the asound directory?

Use the "ls" command to list contents.

Here's mine:

robert@gt5058:/proc/asound$ ls
> Bt878  card0  card1  cards  devices  ICH  modules  oss  pcm  seq  timers  version

---

### Post by S.S.S.P5 on 2007-09-25
james@james-desktop:/proc/asound$ ls
card0  cards    modules  pcm  SI7012  UART
card1  devices  oss      seq  timers  version

---

### Post by S.S.S.P5 on 2007-09-25
lspci now reads...

 james@james-desktop:/proc/asound$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 80)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)

---

### Post by S.S.S.P5 on 2007-09-25
ok I got desktop effects up and running!

---

### Post by Maestro23 on 2007-09-25
> **S.S.S.P5 said:**
> ok I got desktop effects up and running!

So you got sound and everything now?  If so good deal man.

Don't forget to mark this thread SOLVED.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by S.S.S.P5 on 2007-09-25
well i got beryl emerald desktop fx running, the jacd server is up, but not in realtime, and the system cant find the sound card still, but getting the effects up and running did give a glimmer of hope on this being a usable every day program, and considering switching my pressario V2000 laptop over as well, like this thing looks and runs almost as good as my HP m7780n with vista home premium on it- really cool stuff, just wish it were easier to get running out of the box,

---

