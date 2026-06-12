---
title: "Lost sound with today's update"
date: 2007-12-19
forum: General Help
---

### Post by feydrutha on 2007-12-19
Today there was an update to the kernel version i think (didn't read the info carefully, anyhow it asked me to restart).

On reboot, sound was not working at all. Not a sound coming out of my laptop.

It seems I am not the only one who has this problem, it is also mentioned in [this other thread]("http://ubuntuforums.org/showthread.php?t=644632")

I have a dell inspiron 1501 where i did a clean install of gutsy shortly after release.

I was trying to boot with the previous kernel version to verify if that is the problem (and as a workaround for now) but:

-[LIST]
[*]There is no entry for older kernel version in grub boot menu (as used to happen for older ubuntu versions)
[*]There are no vmlinuz and initrd files for older kernel versions in /boot, both of which would be needed for me to write a grub entry.
[/LIST]

anyone know why this is the case?

---

### Post by feydrutha on 2007-12-19
There seem to be some sound (and kernel version)-related error messages in dmesg:

snd_hda_intel: disagrees about version of symbol snd_ctl_add
snd_hda_intel: Unknown symbol snd_ctl_add
snd_hda_intel: disagrees about version of symbol snd_pcm_new
snd_hda_intel: Unknown symbol snd_pcm_new
...

and so on.

The snd_hda_intel module does not show in lsmod.

I get these errors all over again if I try 'sudo modprobe snd_hda_intel'

sudo modprobe snd_hda_intel
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

---

### Post by TheLions on 2007-12-19
no sound here either after update, it just says that there is no  soundcards found, but when i go to system inforemtion i can see my sc! :confused:

---

### Post by geirha on 2007-12-19
> **feydrutha said:**
> There seem to be some sound (and kernel version)-related error messages in dmesg:

snd_hda_intel: disagrees about version of symbol snd_ctl_add
snd_hda_intel: Unknown symbol snd_ctl_add
snd_hda_intel: disagrees about version of symbol snd_pcm_new
snd_hda_intel: Unknown symbol snd_pcm_new
...

and so on.

The snd_hda_intel module does not show in lsmod.

I get these errors all over again if I try 'sudo modprobe snd_hda_intel'

sudo modprobe snd_hda_intel
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

Could you paste the output of these two commands?
```
dpkg -S snd-hda-intel.ko
find /lib/modules/2.6.22-14-generic/ -name "snd-hda-intel.ko"

```
On my Gutsy install, that module is located at /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko, so I'm guessing the one in kernel/ is a module for the previous version of the kernel.

Have you compiled alsa modules yourself?

---

### Post by geirha on 2007-12-19
> **feydrutha said:**
> 
I was trying to boot with the previous kernel version to verify if that is the problem (and as a workaround for now) but:

-[LIST]
[*]There is no entry for older kernel version in grub boot menu (as used to happen for older ubuntu versions)
[*]There are no vmlinuz and initrd files for older kernel versions in /boot, both of which would be needed for me to write a grub entry.
[/LIST]

anyone know why this is the case?

The update was just a minor patch of the kernel, so it simply replaced the previous kernel. Had it been a greater change, you would have a new ubuntu entry in your grub menu with version 2.6.22-15-generic.

You can see the changelogs with: ```
aptitude changelog linux-image-2.6.22-14-generic
aptitude changelog linux-ubuntu-modules-2.6.22-14-generic
```

---

### Post by TheLions on 2007-12-19
> **geirha said:**
> Could you paste the output of these two commands?
```
dpkg -S snd-hda-intel.ko
find /lib/modules/2.6.22-14-generic/ -name "snd-hda-intel.ko"

```
On my Gutsy install, that module is located at /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko, so I'm guessing the one in kernel/ is a module for the previous version of the kernel.

Have you compiled alsa modules yourself?

i get this
```

marko@Zvjer:~$ dpkg -S snd-hda-intel.ko
[COLOR="DarkOrange"]linux-ubuntu-modules-2.6.22-14-generic[/COLOR]: [COLOR="DarkOrange"]/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko[/COLOR]
marko@Zvjer:~$ find /lib/modules/2.6.22-14-generic/ -name "snd-hda-intel.ko"
[COLOR="DarkOrange"]/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
/lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko[/COLOR]
 
```

also i just recompiled alsa and alsa found my soundcard(Realtek nforce chipset) but still no sound!:(

---

### Post by geirha on 2007-12-19
> **TheLions said:**
> i get this
```

marko@Zvjer:~$ dpkg -S snd-hda-intel.ko
[COLOR="DarkOrange"]linux-ubuntu-modules-2.6.22-14-generic[/COLOR]: [COLOR="DarkOrange"]/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko[/COLOR]
marko@Zvjer:~$ find /lib/modules/2.6.22-14-generic/ -name "snd-hda-intel.ko"
[COLOR="DarkOrange"]/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
/lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko[/COLOR]
 
```

also i just recompiled alsa and alsa found my soundcard(Realtek nforce chipset) but still no sound!:(

Do you get the same error after recompiling alsa, or new error message(s)?

You have two modules with the same name in there, one of them should probably not be there, though I wouldn't know which one. When recompiling alsa, does it display where it installed the new module(s)?

---

### Post by TheLions on 2007-12-19
ok  i managed to get a sound!!!

i recomplied alsa from realtek page!:):):)

10x geirha for your concern

 to answer your question:
didn't report any error.

---

### Post by detroit/zero on 2007-12-19
I lost sound on my Feisty install.

Not a peep from anywhere. Should I just recompile alsa?

---

### Post by s3r1al on 2007-12-19
after the update, i had sound, but lost jack sensing. after i plugged in my headphones in sound was still coming from laptop speakers...
i just recompiled alsa, and everything works again...

---

### Post by uconvert on 2007-12-19
I lost sound after today's update. i have an Asus Z62FM (the same as the System76 Gazelle Value).

After update, I downloaded System76 Drivers to try to fix and still nothing. I am in the middle of a project that is sound dependent, so I am not happy right now and too tired to try to fix on my own.

Any help on a quick fix would be greatly appreciated.

Thanks

---

### Post by empty_spaces on 2007-12-19
I had ALSA version 1.0.15 on my computer and everything was going great until I too lost my sound and mic this morning after the update.
So I reran the ALSA driver install process shown in the link below, but replacing 1.0.14 with 1.0.15 wherever applicable, ***and now I have everything working again.***

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

You can get the ALSA 1.0.15 driver, lib, and utils from this link

[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)


Cheers.

---

### Post by detroit/zero on 2007-12-20
I'm with empty-spaces. I found that hdaintel how-to and recompiled alsa 1.0.15 and everything works fine.

i notice that when I plug in a pair of headphones the laptop speakers don't shut off, but I remember having to deal with that before once, too, and there's a fix for it floating around here somewhere.

[HdaIntelSoundHowto - Community Ubuntu Documentation]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

---

### Post by stealthc on 2007-12-20
funny, I lost sound.  My sound card is no longer detected :(

---

### Post by empty_spaces on 2007-12-20
> **stealthc said:**
> funny, I lost sound.  My sound card is no longer detected :(

I had the same problem yesterday. Have you tried the solution from my previous post?

---

### Post by uconvert on 2007-12-20
It's a new day. 

I tried the fix, every step seemed successful, but still no sound.

I pulled down the preferences menu, and the option for speaker volume is missing.

Any other suggestions would be appreciated

Thanks

---

### Post by fuzzypig on 2007-12-20
please reinstall linux-ubuntu-modules-2.6.22-14-generic, run "sudo depmod" and reboot.

It seems that the developers forgot to add the depmod command to the end of this package, so the new kernel can't find the modules. This breaks many modules, including alsa and ndiswrapper.

---

### Post by uconvert on 2007-12-20
I was so hoping that would do it, but it didn't :(:confused:

I'm going to restore to my last backup (11/30), update and try that first.

---

### Post by uconvert on 2007-12-20
Well shoot! 

That didn't work either I'll try the Alsa recompilation again.

---

### Post by uconvert on 2007-12-20
OK - Heres' what worked for me.

using this command: cat /proc/asound/card0/codec#* | grep Codec

I found that my soundcard is an AD1986A

A fellow member mcmc had posted a fix in a previous unrelated thread
[http://ubuntuforums.org/showthread.php?t=231032](http://ubuntuforums.org/showthread.php?t=231032)

check it out - it works!

(I entereed the "options...3stack" line at the end of /etc/modprobe.d/alsa-base)

Good luck

---

### Post by Bingulim on 2007-12-21
Man...

I though my sound card was gone... Almost cry over here. ;-)

I am compiling again the alsa sources. Let's hope everything works.

---

### Post by stealthc on 2007-12-22
> **empty_spaces said:**
> I had the same problem yesterday. Have you tried the solution from my previous post?

What I ended up doing to get it working again was 

Redownload alsa drivers and extract, using get.apt and gzip extractor
then do the ./configure , make, make install
did this for drivers, library and utils folders and everything was good as new.

I figured that would work because there was a "bad character" coming up with various messages that had led me to believe that the drivers had become corrupted, and thus were crashing as opposed to loading.

Before that I did try a few other things though which failed miserably.  :(  Tried resetting xconf.org (which obviously wasn't the problem now that I've figured it out).  Tried reloading alsa components in synaptic (which reloaded the same defective builds I had on the system before, so it didn't work).

---

### Post by stealthc on 2007-12-22
> **detroit/zero said:**
> I'm with empty-spaces. I found that hdaintel how-to and recompiled alsa 1.0.15 and everything works fine.

i notice that when I plug in a pair of headphones the laptop speakers don't shut off, but I remember having to deal with that before once, too, and there's a fix for it floating around here somewhere.

[HdaIntelSoundHowto - Community Ubuntu Documentation]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

yeah for me it was in xconf.org, in /etc/modprobe.d/
I inserted line that had model as xyz, but this is for lg p1 laptop.

---

