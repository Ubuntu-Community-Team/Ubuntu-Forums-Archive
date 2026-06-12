---
title: "Sound Problem"
date: 2007-05-29
forum: General Help
---

### Post by Pipboy2000k on 2007-05-29
hi, this is my first post 

I'm very new to Ubuntu and Linux as well, I'm just switching over from vista. 

Ive got a HP pavilion dv2312us laptop 

Anyways, ive been having problems with my sound. It works on and off, and I can't figure out whats doing it. Sometimes the sound works on boot, and sometimes it dosent. Thats generally how i tell if its not working for the moment.

anyone have any idea how i can fix this?

---

### Post by liberalist on 2007-05-29
I am new to Linux as well, but I think it is a driver issue. Have you tried the restricted drivers manager (it is somewhere in the menus above or below, depending on your Desktop Environment)? In Ubuntu, you can find it in the menu System > Adminstration > Restricted Drivers Manager (or something like this). I hope that helps.

---

### Post by Pipboy2000k on 2007-05-29
well i tried the restricted drivers manager already, and it says "your hardware does not need any restricted drivers"

so yeah, :(

i spoke to a friend who is a network technician and Gentoo savvy and he said it could be that my onboard wireless and my onboard sound could be conflicting...i have no idea what hes talking about though because it dosent sound like that is really possible...

---

### Post by GingerAlex on 2007-05-29
The problem may be simpler..

If I run a media player e.g. Audacity, then try to get sound from another application, say, a YouTube clip in Firefox, the second app makes no sound. Try some experiments and see if this is what is happening to you,

I think the first app to use the sound interface "locks" it for personal use, and then subsequent apps go without sound. 

I believe I have read that this behaviour is by design, but I for one would be grateful of a way to change it - if anyone out there could suggest something? 
When I was in W*ndows I could listen to as many sound sources as I liked - it may sound silly but I don't want have to close Audacity, or miss vital overs on Test Match Special, just to watch a quick clip whilst browsing.

---

### Post by Pipboy2000k on 2007-05-29
it seems to be only, a boot problem honestly. Such as if I dont hear the ubuntu noise at the login screen. Then that means there is no sound for that session im running.  However it seems that if I switch off my network card and let the computer boot up. It has sound, and then i can just turn my network card back on. however i dont think that solves it...

I'm gonna boot it a few more times and see what happens with certain patterns...

---

### Post by quinnten83 on 2007-05-29
> **GingerAlex said:**
> The problem may be simpler..

If I run a media player e.g. Audacity, then try to get sound from another application, say, a YouTube clip in Firefox, the second app makes no sound. Try some experiments and see if this is what is happening to you,

I think the first app to use the sound interface "locks" it for personal use, and then subsequent apps go without sound. 

I believe I have read that this behaviour is by design, but I for one would be grateful of a way to change it - if anyone out there could suggest something? 
When I was in W*ndows I could listen to as many sound sources as I liked - it may sound silly but I don't want have to close Audacity, or miss vital overs on Test Match Special, just to watch a quick clip whilst browsing.

I actuallyu also noticed this. If I am running, or did run, another application that uses sound, than I would no longer get a sounds warning in Amsn. 
This is very annoying indeed. If I'm listening to music, I still want to hear a sound notifying me that a contact has come online.
Any suggestions on fixing this??? Anybody, anybody?

---

### Post by Pipboy2000k on 2007-05-30
ive solved the problem, it seems that my onboard wireless conflicts with my sound card on startup.

---

### Post by GingerAlex on 2007-06-02
> **quinnten83 said:**
> I actuallyu also noticed this. If I am running, or did run, another application that uses sound, than I would no longer get a sounds warning in Amsn. 
This is very annoying indeed. If I'm listening to music, I still want to hear a sound notifying me that a contact has come online.
Any suggestions on fixing this??? Anybody, anybody?

OK - early indications are that I've found the solution to this - the sound locking not pipboy2000's issue he looks like he's fixed that himself and we're now just hijacking an otherwise deceased thread..

The following comes from [http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

> Getting more than one application to use the soundcard at the same time

    * You might want to play a game and listen to music on your favorite music player at the same time. To do this successfully, you will have to use ALSA since it supports this feature the best. On all the music players I know of, you can configure the sound engine, to any module that is available.

    *
      The setting is usually found under something like Tools >>> Configure >>> Player Engines.

    *
      For games, it is a bit more tricky since there is not always a way to configure the player engine directly. Most games, however, do support the OSS. ALSA has an OSS module that allows OSS applications to use the ALSA driver.

    *
      To do this you will need the alsa-oss package
      Code:

      sudo apt-get install alsa-oss

    *
      After doing this step, it is very easy to use alsa-oss. In the shell, you can type 'aoss' then the name of the program name you want to use with alsa-oss.

I have installed the above library, and it seems to have fixed the problem without me having to do anything else.

Thank you to the author of the above guide and quinnten83 I hope it works as well for you..

---

### Post by Pipboy2000k on 2007-06-02
well honestly, it seemed like nobody knew what i was talking about, because the problem occurred before i even hit the desktop!

 which makes me question the community...

---

