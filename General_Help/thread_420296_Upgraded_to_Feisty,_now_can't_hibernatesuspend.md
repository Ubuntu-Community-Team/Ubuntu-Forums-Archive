---
title: "Upgraded to Feisty, now can't hibernate/suspend"
date: 2007-04-23
forum: General Help
---

### Post by Matt Petrie on 2007-04-23
I just upgraded from Edgy to Feisty, and now I can't hibernate or suspend any more. Both of these things worked just fine under Edgy, but now in Feisty it won't hibernate when I shut the lid on my laptop, or when it has been sitting idle for the prescribed amount of time. If I manually tell it to hibernate, it hangs on a black screen with a cursor blinking in the corner. Anyone know how I can fix this?

Now I think there are a few pertinent details that may be helpful:

1. When I was installing Feisty, I changed my settings in gnome-power-manager so that my computer would not go to sleep after being idle. I did this so it would not try to hibernate in the middle of the install, which took quite a while.

2. During the install, gnome-power-manager crashed. I'm not sure if this has anything to do with the current problem.

3. In Edgy, gnome-power-manager had a button that let me select what happened when the computer went to "sleep", which I had set to "hibernate". Now in Feisty that button is gone.

I tried reinstalling gnome-power-manager, but to no avail. Any ideas?

my computer: Dell Inspiron 5150 laptop

---

### Post by uelansh on 2007-04-24
I cannot offer any advice however I am having a problem involving hibernate and gnome.

I placed my computer into hibernate, ate lunch, then came back. Once I came back numerous menu options no longer functioned, all giving a "gnome not found" error. I did a hard restart and now when I try to login gnome is not found. As if it all has been deleted or something. Any ideas? Thanks.

---

### Post by jputman01 on 2007-04-24
> **uelansh said:**
> I cannot offer any advice however I am having a problem involving hibernate and gnome.

I placed my computer into hibernate, ate lunch, then came back. Once I came back numerous menu options no longer functioned, all giving a "gnome not found" error. I did a hard restart and now when I try to login gnome is not found. As if it all has been deleted or something. Any ideas? Thanks.

you may want to start a new topic

---

### Post by jputman01 on 2007-04-24
> **Matt Petrie said:**
> I just upgraded from Edgy to Feisty, and now I can't hibernate or suspend any more. Both of these things worked just fine under Edgy, but now in Feisty it won't hibernate when I shut the lid on my laptop, or when it has been sitting idle for the prescribed amount of time. If I manually tell it to hibernate, it hangs on a black screen with a cursor blinking in the corner. Anyone know how I can fix this?

Now I think there are a few pertinent details that may be helpful:

1. When I was installing Feisty, I changed my settings in gnome-power-manager so that my computer would not go to sleep after being idle. I did this so it would not try to hibernate in the middle of the install, which took quite a while.

2. During the install, gnome-power-manager crashed. I'm not sure if this has anything to do with the current problem.

3. In Edgy, gnome-power-manager had a button that let me select what happened when the computer went to "sleep", which I had set to "hibernate". Now in Feisty that button is gone.

I tried reinstalling gnome-power-manager, but to no avail. Any ideas?

my computer: Dell Inspiron 5150 laptop


i am having a similar issue if anyone can help, if i tell it to hibernate it will but it will not come back from hibernate it gets stuck on the black screen with blinking cursor. 

however this did work for me in feisty beta, and it would even let me assign suspend or hibernate to the laptop lid closing, thanks for the help guys

---

### Post by strabes on 2007-04-24
[http://www.thinkwiki.org/wiki/ATI_Mobility_FireGL_V5200](http://www.thinkwiki.org/wiki/ATI_Mobility_FireGL_V5200)

> Finally, the perhaps most important change goes into /etc/default/acpi-support. Change the line POST_VIDEO=true to read POST_VIDEO=. This was the point when it started working on my system.

---

### Post by gamma on 2007-04-24
I'm also on a Dell Inspiron 5150 and I don't have any issues hibernating. I've got an NVIDIA GeforceFX GO5200 card in mine. If I do use the nvidia drivers I have to blacklist a few modules so that NVAGP loads instead of AGPGART and I can resume from hibernate.

Thread poster your lid switch was working before? I think I had it working 3 years ago, but then a BIOS firmware update broke it. It can be reenabled with some GRUB flag, but when I used that flag I wasn't able to burn CDs. So it's a tradeoff :P.

---

### Post by AVH on 2007-04-25
I lost the ability to resume from suspend/hibernate (not sure which because power management only gives me a choice of 'sleep') on both desktops  I upgraded. 

The macines go to 'sleep' with no problem but attemps to resume for the keyboard get no response at all, and using the power switch gets a blank screen with a cursor that moves in response to keystrokes but won't do anything else. I have to reboot.

Playing with the s1/s3 options in the bios didn't help.

---

### Post by strabes on 2007-04-25
Did the technique I posted above not help you guys or something? It isn't getting much feedback. It worked for me with my Dell E1705 with an ATI x1400.

---

### Post by gamma on 2007-04-25
> **AVH said:**
> I lost the ability to resume from suspend/hibernate (not sure which because power management only gives me a choice of 'sleep') on both desktops  I upgraded. 

The macines go to 'sleep' with no problem but attemps to resume for the keyboard get no response at all, and using the power switch gets a blank screen with a cursor that moves in response to keystrokes but won't do anything else. I have to reboot.

Playing with the s1/s3 options in the bios didn't help.

What type of video card are you using? If you have the NVIDIA drivers you're going to have to make some changes to get it to resume properly.

---

### Post by gamma on 2007-04-25
To get the lid working and the other ACPI features add 'irqpoll' to GRUB's boot parameters. People say performance decreases, so try and see if you have this issue. I'd tried this on Dapper and with this parameter I couldn't burn CDs. I have yet to try in Feisty.

[http://bugzilla.kernel.org/show_bug.cgi?id=1752](http://bugzilla.kernel.org/show_bug.cgi?id=1752) is the kernel bug report.

---

### Post by mfield on 2007-04-26
> **strabes said:**
> Did the technique I posted above not help you guys or something? It isn't getting much feedback. It worked for me with my Dell E1705 with an ATI x1400.

I tried this, and it did not change anything (system hibernates fine but does not wake up -- instead of resuming, it does a fresh reboot).  In my case, dropping back to the last Edgy kernel (2.6.17.11) fixed the problem.  So either the new kernel requires different settings (and I've been playing with this unsuccessfully), or has a bug.

Marc

---

### Post by AVH on 2007-04-27
> **gamma said:**
> What type of video card are you using? If you have the NVIDIA drivers you're going to have to make some changes to get it to resume properly.

One is an old 3DForce2 MX 64mb, the other is a not quite as old GeForce MX 440 64mb. They seem  to work fine, th old one  with either one of the nVidia drivers. Unfortunately, I tried to unload the restricted driver for the older one  to go back to th os driver and am now stuck with the 'White Screen of Death'.  Fixing that has become my first priority, but I would very much like to know how to make suspend and hibernate work properly.

---

### Post by DouglasK on 2007-04-28
> **strabes said:**
> [http://www.thinkwiki.org/wiki/ATI_Mobility_FireGL_V5200](http://www.thinkwiki.org/wiki/ATI_Mobility_FireGL_V5200)

I tried the POST_VIDEO= ... but it didn't help...  

This is with a "nVidia Corporation NV28 [GeForce4 Ti 4200 Go AGP 8x] (rev a1)" in a Dell Inspiron 8500 [Edit: Corrected model number of the dell]

---

### Post by alpha2zulu on 2007-04-28
I am having a similar problem, but mine is a bit more specific. When I click Hibernate, a black screen appears and at the bottom of the screen is a message concerning my WLAN card. It says "bcm43xx.fw could not be found". Then it locks my screen, and from there I can resume my session.

Also, my power and restart buttons are gone. And after all this takes place a notification pops up saying "HAL failed to hibernate".

---

### Post by faust99 on 2007-04-30
> **strabes said:**
> [http://www.thinkwiki.org/wiki/ATI_Mobility_FireGL_V5200](http://www.thinkwiki.org/wiki/ATI_Mobility_FireGL_V5200)

I got suspend to work on my Dell 710m after following the steps outlined in the link above (although the third step regarding POST_VIDEO=true/false seems to make no difference). The only thing is, when it wakes up from suspension, it is still in terminal mode so I have to turn it on manually (Ctrl+alt+F7). Other than, at least it works.

:guitar:

---

### Post by strabes on 2007-04-30
You should undo the first two steps in that link then, I think.

---

### Post by faust99 on 2007-04-30
> **strabes said:**
> You should undo the first two steps in that link then, I think.

Yes but if I do then it won't go into suspend. The screen just turns off. I tried just the third step but it seems to do nothing either way.

---

### Post by joy83 on 2007-05-01
Yes, I have the same problem. When I suspend the computer then it freezes after I come back. There is a black screen with just a very small white rectangle in it. Whats going on?

---

### Post by Cauda_Draconis on 2007-05-01
When  I wake my laptop up from hibernate or suspend, gnome comes up fine with all the windows, but the cursor is stuck in the corner or on the left side. I can still click functionally anywhere on the screen, but the cursor stays in the corner or moves up and down on the right side. It did this in Edgy too. 
Anyone know anything about this?

---

