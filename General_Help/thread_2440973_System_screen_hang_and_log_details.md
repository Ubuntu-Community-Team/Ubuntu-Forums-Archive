---
title: "System screen hang and log details"
date: 2020-04-17
forum: General Help
---

### Post by aniketiitr on 2020-04-17
Hi
I have  installed ubuntu bionic 18.04 3 days back through usb to my pc, after  having multiple BSOD problems with win 10. The system is working well.
The pc configuration is
AMD Ryzen 5 3500
Gigabyte B450M DS3H
Adata Gammix 3200mhz 16GB 
Gigabyte RX570 graphic card
1 Tb WD blue HDD
I checked hard drive through SMART data and Self tests (extended) and all is OK.
Yesterday while watching a youtube video, my system screen got stcuk. I i tried terminal, Alt+Ctrl+F1..F6 etc. but none worked. I had to hard reset it. Today same happened.
Then i looked into log file, it has many errors but I am sharing Important log screenshot and details as below:
System #PF: error_code(0x0001) - permissions violation
System #PF: supervisor read access in kernel mode
System BUG: unable to handle page fault for address: 00007f995964f278
Application [alsa-sink-ALC887-VD Analog] alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
Application [alsa-sink-ALC887-VD Analog] alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Application [alsa-sink-ALC887-VD Analog] alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write.
Application [pulseaudio] bluez5-util.c: GetManagedObjects() failed: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Application [pulseaudio] bluez5-util.c: GetManagedObjects() failed: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

But I understand none of it. Please help me understand. Also tell me if there is anything really important to attend.

---

### Post by CelticWarrior on 2020-04-17
My guess is faulty RAM, either the memory in the motherboard or the one in the graphics, or both.

---

### Post by mörgæs on 2020-04-17
Hi, welcome to the fora.

> **aniketiitr said:**
> 
Application [alsa-sink-ALC887-VD Analog] alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.


This is the risk associated with using old software. It may or may not be fixed in 20.04 so I suggest that you try a fresh install of this one. We see many similar questions from other people using 18.04.

There is no need to report bugs for 18.04, though, in spite of the message.

---

### Post by aniketiitr on 2020-04-17
> **CelticWarrior said:**
> My guess is faulty RAM, either the memory in the motherboard or the one in the graphics, or both.

Thank you so much for your reply. Can you please tell me how to check both of them in ubuntu?? I am quite new to ubuntu.
Thanks so much again.

---

### Post by CelticWarrior on 2020-04-17
Please first try the suggestion above of installing 20.04. We can troubleshoot from there.

---

### Post by aniketiitr on 2020-04-18
> **CelticWarrior said:**
> Please first try the suggestion above of installing 20.04. We can troubleshoot from there.

Upgrade done. I am now on 20.04. Please guide me further.

---

### Post by mörgæs on 2020-04-18
Was it a fresh install or an upgrade in-place?

---

### Post by aniketiitr on 2020-04-18
> **mörgæs said:**
> Was it a fresh install or an upgrade in-place?

I did upgrade in-place. Is that okay or should I do another fresh new install?

---

### Post by mIk3_08 on 2020-04-18
In my case, I did a fresh install of 20.04 and it solve my problem. :-D

---

### Post by mörgæs on 2020-04-18
> **aniketiitr said:**
> I did upgrade in-place. Is that okay or should I do another fresh new install?

You can of course keep it running to see if you are lucky but if the error reappears (or if a new error has been introduced in the upgrade process) then do the fresh install.

---

### Post by aniketiitr on 2020-04-18
> **mörgæs said:**
> You can of course keep it running to see if you are lucky but if the error reappears (or if a new error has been introduced in the upgrade process) then do the fresh install.

okay, thanks a lot. 
Can you suggest me how to check graphic card RAM in ubuntu, as suggested by another.  Actually al my hardware is under warranty and I am eager to replace the culprit.
I checked RAM through memtest 15G 5times and it showed Okay.
Thanks a lot once again.

---

### Post by mörgæs on 2020-04-18
Only thing I can suggest is to keep using a selection of programs and see how they behave. Browsers, GIMP, VLC and other media players, Blender, Libreoffice...

---

### Post by aniketiitr on 2020-04-18
The problem has reoccurred. The screen got stuck in the mid of the video alongwith audio. Please help me find out the problem.

---

### Post by mörgæs on 2020-04-18
That's exactly what I am trying to do: Helping people to find the problem. That's not the same as solving the problem for people.

Using the information in this thread (and in the forum in general) I think it's time for you to take the lead. Tell us in detail what you have done and what you are planning to do in order to diagnose the problem. 

Read some other threads. What have I and other users suggested elsewhere?

---

### Post by aniketiitr on 2020-04-26
> **mörgæs said:**
> That's exactly what I am trying to do: Helping people to find the problem. That's not the same as solving the problem for people.

Using the information in this thread (and in the forum in general) I think it's time for you to take the lead. Tell us in detail what you have done and what you are planning to do in order to diagnose the problem. 

Read some other threads. What have I and other users suggested elsewhere?

Hi,
As suggested, I did another fresh install then only. After that my pc was okay until yesterday, when i got latest 20.04 LTS from beta. Very soon, my video and audio both stuck similarly. The log file is attached for reference. May be culprit is somewhere in LTS version!!!???

I am thankful to you for giving me the lead, but i am not at all in position for such a lead as I am very very primitive here. I am surviving on copying the terminal commands written by people like you:P, that too without being able to understand.

 I have a self made game build and is waiting for problem free system (only doing browsing and not gaming) with the hope that people like you will help me to resolve all problems.

Sorry to disappoint you for that. But for sure i can get all the info of my pc for getting resolutions.

---

### Post by mörgæs on 2020-04-26
I am aware that you are new. Still I think it's time for you to begin studying how other problems have been dealt with rather than only asking. That could have lead you to a post like
[https://ubuntuforums.org/showthread.php?t=2440774&p=13947137&viewfull=1#post13947137](https://ubuntuforums.org/showthread.php?t=2440774&p=13947137&viewfull=1#post13947137)

You didn't tell if 20.04 was a clean install or an upgrade. Yesterday (25. of april) 20.04 was not in beta, it was an official release.

---

