---
title: "Audacity error initializing audio layer"
date: 2007-01-04
forum: General Help
---

### Post by FuturePilot on 2007-01-04
Audacity gives me that error about initializing audio layer I/O error. But I only get that after I run a program like Amarok. It works fine before, but after I quit Amarok, I get that error. I go under the preferences menu and there's no sound device listed. Anyone know how to fix that or what's causing it?

---

### Post by FuturePilot on 2007-01-06
Ok, well it has nothing to do with other programs like I thought. It worked when I first installed it, but when I rebooted later it didn't work and now I can't get it to work at all. Same thing happened on Edgy too.

---

### Post by FuturePilot on 2007-01-06
Ok, well I've found a fix or workaround. I ran
```
aoss audacity
```
in the terminal and it worked. So I opened the menu editor and changed the command for Audacity from
```
audacity
```
to
```
aoss audacity
```
Now it works fine.

---

### Post by rowanparker on 2007-01-08
When I run aoss audacity it just does nothing and I must press Control-C to end it.
Any other alternatives?

---

### Post by konungursvia on 2007-01-10
I get the same I/O error and audacity can never find audio input and output devices (I've installed it and tried running it a few times). But aoss gives me nothing either.

---

### Post by rowanparker on 2007-01-11
> **konungursvia said:**
> I get the same I/O error and audacity can never find audio input and output devices (I've installed it and tried running it a few times). But aoss gives me nothing either.
Glad im not the only one, any fixes?

---

### Post by Zimmer on 2007-01-11
> **rowanparker said:**
> Glad im not the only one, any fixes?

try editing your esd.conf to read

[esd] 
auto_spawn=0
spawn_wait_ms=100
default_options= -terminate -nobeeps -as 2

---

### Post by rowanparker on 2007-01-11
Still happens, do I have to do anything before I try and open it (like killall something?).

---

### Post by Zimmer on 2007-01-11
> **rowanparker said:**
> Still happens, do I have to do anything before I try and open it (like killall something?).

the usual reason for this lack of sound is that another app is hogging the soundcard...  you can try disabling  ESD and system sounds in Preferences>Sound and , indeed

killall -9 esd  

Otherwise, post your soundcard specs etc. and see if any one else can offer suggestions

---

### Post by rowanparker on 2007-01-11
I'll get back to you, thanks.

---

### Post by konungursvia on 2007-01-11
> **konungursvia said:**
> I get the same I/O error and audacity can never find audio input and output devices (I've installed it and tried running it a few times). But aoss gives me nothing either.

I think I should add that I've been running Rythmbox, sound juicer and Skype a lot recently. Would they have hogged some port or something?

---

### Post by konungursvia on 2007-01-12
So, any ideas? :D

---

### Post by rowanparker on 2007-01-12
I don't think they'll have hogged the port (might be wrong) but I don't have any ideas, sorry.

---

### Post by Zimmer on 2007-01-12
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_configure_sound_to_work_properly_in_GNOME](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_configure_sound_to_work_properly_in_GNOME)

This is the guide I used to sort sound out.... have a look and see if that helps Audacity....

---

