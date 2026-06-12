---
title: "Volume control showing as muted but sound still playing"
date: 2017-04-14
forum: General Help
---

### Post by alexswilliams on 2017-04-14
Hi all,

I upgraded a laptop to Zesty this morning - one has a curious problem:  the volume control widget in the tray area is showing as muted and won't let you change volume.

There are a few things which confuse me about this:
 - sound still plays (e.g. you can open rhythmbox and hear the music you play, and you hear the ubuntu drum when it finishes booting)
 - the volume control still works on the login screen (though not on the lock screen) - and if you log out (to go back to the login screen) you get the volume control back until you log in again.
 - plugging in headphones whilst logged in stops all audio, but doesn't stop it playing.  Unplugging them resumes audio coming out of the speakers.  You can still get the ubuntu drums at login through headphones though.
 - I can hear the sound card power being turned on and off whilst headphones are plugged in.

I'm stumped by this!  I've found similar problems from several years ago (caused by 32-bit pulse drivers being installed on a 64-bit system) but nothing like this reported recently.

Some details about my system:

```

lspci | grep Audio
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)

alsactl init
Found hardware: "HDA-Intel" "Realtek ALC255" "HDA:10ec0255,10431c7d HDA:80862809,80860101,00100000" "0x1043" "0x1c7d"
Hardware is initialized using a generic method

cat /etc/default/grub | grep CMDLINE_LINUX_DEFAULT
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=intel pci=nomsi"

```

Has anyone seen anything similar or have any ideas about how to troubleshoot this?

Thanks!

---

### Post by alexswilliams on 2017-04-14
A quick reply to say I'd solved it - I tried restarting the pulseaudio daemon with ```
pulseaudio -k; pulseaudio -D
``` and watched syslog.  That showed that it was trying to load module-ladspa-sink and mbeq_1197.  Some googling said this was because I'd removed the pulseaudio-equalizer package (I didn't think I had, but sure!) and that I needed to go into the default.ca file (which has ended up in ~/.config/pulse/) and remove the lines that package added that referenced that library.  I got my volume control back :).
Thanks!

---

