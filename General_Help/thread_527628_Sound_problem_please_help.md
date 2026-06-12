---
title: "Sound problem please help"
date: 2007-08-16
forum: General Help
---

### Post by lugnut_9754 on 2007-08-16
Hello. I've been using ubuntu for about 7 months now and love it. Sound worked fine before, then I reinstalled so I could dual boot with windows and sound worked fine. Now I'm back to just ubuntu because i can't stand windows. Problem is my sound no longer works. It i go into sound options and test it works fine and on Gaim it works fine. i've tried a ton of different stuff from othersites/posts and nothing has worked. i have 2 sound cards, one onboard and other addon. BIOS is correct, sound controls are set to addon, but when I open alsamixer it is set to onboard. i have tried a ton of suggestions from other site/posts to change order of cards but nothing has worked. Please help. thanks.

--
LuGnUt

---

### Post by kyphi on 2007-08-16
Your onboard sound chip is just that, a chip.  My preferred option in a similar situation has always been to disable the onboard sound and use the add on soundcard (this really is a card).

To have both enabled can lead to conflicts as you have discovered.

You can disable the onboard sound device via the BIOS.

---

### Post by lugnut_9754 on 2007-08-16
As stated in original post it is already disabled in BIOS

---

### Post by lugnut_9754 on 2007-08-16
also sound worked when I installed before, and it works when i test it and in gaim. just not on websites or vlc

---

### Post by kyphi on 2007-08-16
Have you tried to disable the "addon"?

---

### Post by lugnut_9754 on 2007-08-16
onboard sound doesnt work, that is why i bought soundcard, so there would be no point to disable the addon

---

### Post by kyphi on 2007-08-16
Try it.  Disable onboard sound even though it does not work.  There is no point in having the BIOS accessing an incomplete circuit.

When you go to your sound preferences, what is identified as your default sound card?

---

### Post by lugnut_9754 on 2007-08-16
the addon

---

### Post by kyphi on 2007-08-16
What is your soundcard?

---

### Post by jusmurph on 2007-08-16
From [**here**]("http://ubuntuforums.org/newreply.php?do=newreply&p=2829011")

> **jusmurph said:**
> Fixed.

the " Configuring default soundcards / stopping soundcards from switching" freaked me out. I saw the alternative and found it here [https://bugs.launchpad.net/ubuntu/+bug/57141](https://bugs.launchpad.net/ubuntu/+bug/57141)

>  Originally Posted by **Gabriel Pastor**
I had the same problem with feisty and solved it.
I have 2 sound cards, and it seems that sometimes the wrong sound card is the default sound device.

$ sudo asoundconf list
Names of available sound cards:
Intel
CA0106

The first one is integrated on the motherboard, and the second one (an audigy) is the one I use.

To solve the problem, I just set the default sound card to the audigy:
$ sudo asoundconf set-default-card CA0106

Then the sound works !
Hope it helps.


Thank you thank you thank you!

---

### Post by lugnut_9754 on 2007-08-16
nForce2
CMI8738MC6

Tried suggestion and it didnt work. Skype sound and gaim sound both work, just not vlc or websites (Flash)

---

### Post by jusmurph on 2007-08-17
when you open the terminal alsamixer, what does it say is the device?

Because I'm back in the same boat. Mine is saying the device is onboard... though i want my Audigy2 back.

---

