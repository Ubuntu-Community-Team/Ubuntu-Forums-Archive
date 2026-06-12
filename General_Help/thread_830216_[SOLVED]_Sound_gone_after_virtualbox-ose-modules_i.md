---
title: "[SOLVED] Sound gone after virtualbox-ose-modules install? Help!"
date: 2008-06-15
forum: General Help
---

### Post by ChildOfMana on 2008-06-15
Help!

I'm running Hardy.

I installed Virtualbox (from the repositories) with a view to virtualising Windoze XP (just for an experiment).

I created a new virtual machine and then attempted to fire it up... at which point it told me it couldn't start the virtual machine as I don't have the "virtualbox-ose-modules" package installed.

I installed the "virtualbox-ose-modules" package for the "2.6.24-18-386 kernel" and re-booted.

Now I have no sound!! :(

Everything else seems to work perfectly (so far) but I just can;t get my speakers to emit even the tiniest beep.

When I click on the speaker icon I get the following message:

> The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plug-ins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

I duly fired up synaptic and removed the virtualbox package I'd just installed and then rebooted... but still no sound.

What have I done, and can it be fixed?

Please help.

Thanks.

---

### Post by Happy_Man on 2008-06-15
Try installing alsa-utils, and then running the command ```
alsaconf
``` and seeing if that fixes it.

---

### Post by ChildOfMana on 2008-06-15
According to Synaptic I've got alsa-utils installed but when I type alsaconf into a terminal it gives me the old:

> bash: alsaconf: command not found

error message.

Am I missing something?

---

### Post by Happy_Man on 2008-06-15
Huh, I could have sworn alsa-utils did that. **goes to google** Ah, apparently the upstream devs have recently removed it from the package, and it is no longer available on Debian/Ubuntu. That sucks. 


As another solution, run ```
alsamixer
``` and see if something needs to be turned up or unmuted there.

---

### Post by ChildOfMana on 2008-06-15
Another ominous error message:

> alsamixer: function snd_ctl_open failed for default: No such file or directory

I hope I can fix this as I really, REALLY don't want to have to re-install the OS just to get my sound working again :(

Thanks for your help so far.

---

### Post by Happy_Man on 2008-06-15
Oh dear... see this page, down at the bottom: [http://beranger.org/index.php?page=diary&2008/03/12/13/12/34-confirming-a-sound-hardy-bug-](http://beranger.org/index.php?page=diary&2008/03/12/13/12/34-confirming-a-sound-hardy-bug-)

---

### Post by ChildOfMana on 2008-06-15
Oh, dear indeed :( :( :( :(

Does this mean what I think it means?

---

### Post by Happy_Man on 2008-06-15
Well, try booting an earlier kernel first, and see if you can get sound like that. If not, then, yes, I'm afraid it is what you think it is...

---

### Post by ChildOfMana on 2008-06-15
How do I boot an earlier kernel?

I tried editing the GRUB menu to see if I could default to another kernel on boot but it doesn't appear to exist... at least not where it used to under 7.04 (in /etc/grub).

---

### Post by Happy_Man on 2008-06-15
You can always change the order of kernels (which is the same thing as setting a new default kernel) in /boot/grub/menu.lst. ```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by ChildOfMana on 2008-06-15
Lol, I'm such an idiot - I was looking for menu.lst under /etc/grub and not /boot/grub.

I don't know why - I've edited the GRUB menu many a time on my other rig (that dual boots with XP).

Must just be one of "those" days!!

Thanks man. I'll let you know how I get on.

---

### Post by ChildOfMana on 2008-06-15
Eureka!

First I commented out the 'hiddenmenu' section of menu.lst and re-booted - just to see if I could pick the 2.6.24-18-generic kernel.

I could and when I booted into it the sound was fine.

I've just now edited menu.lst to default to the 2.6.24-18-generic kernel so all should be fine from now on.

The only problem that may arise is if a future update adds a new kernel to the list (which is the cause of me having to edit menu.lst on my dual boot once or twice in the past), which will throw out my default.

Even so, it's a simple matter to re-edit and make a new default so a minor, on-off inconvenience at worst!

Thanks for all your help Happy_Man - I wouldn't have thought to do this without your help and would probably have ended up giving up and re-installing.

---

### Post by rarsa on 2008-11-11
Thanks for the tip.

After reading your advise it made sense so I actually uninstalled the corrupted kernel.

I hope that on the next kernel update everything will be OK.

---

### Post by cmittle on 2008-12-30
I appear to be having the same problem as you.  I was booting to 2.6.24-22 until today I had to start using the -21 kernel for my xp install in virtualbox.  I now have no sound when I boot to the -21 kernel.  If I boot to the -18 kernel I have sound.  Did you ever get anything to work out for you?

> **ChildOfMana said:**
> Eureka!

First I commented out the 'hiddenmenu' section of menu.lst and re-booted - just to see if I could pick the 2.6.24-18-generic kernel.

I could and when I booted into it the sound was fine.

I've just now edited menu.lst to default to the 2.6.24-18-generic kernel so all should be fine from now on.

The only problem that may arise is if a future update adds a new kernel to the list (which is the cause of me having to edit menu.lst on my dual boot once or twice in the past), which will throw out my default.

Even so, it's a simple matter to re-edit and make a new default so a minor, on-off inconvenience at worst!

Thanks for all your help Happy_Man - I wouldn't have thought to do this without your help and would probably have ended up giving up and re-installing.

---

### Post by ChildOfMana on 2009-01-01
In the end there was another kernel update which seemed to fix all the problems. Can't remember what kernel it was now as it was a while ago and back when I was running Hardy.

I'm running Intrepid now and so far so good *crosses fingers*

---

