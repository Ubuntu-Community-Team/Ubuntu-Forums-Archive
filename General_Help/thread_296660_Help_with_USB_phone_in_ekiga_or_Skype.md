---
title: "Help with USB phone in ekiga or Skype"
date: 2006-11-09
forum: General Help
---

### Post by Shay Stephens on 2006-11-09
I have a working ekiga install.  With a headset plugged into my soundcard all works well.  But if I try to use a USB phone, all I can get is the audio from the earpiece, but no audio is recorded from the microphone.

This is the case in both ekiga and skype, both the latest versions.  If anyone has this working, or has any tips I love to try them out.

I have tried a number of variations of alsa, oss, etc and turning on various capture and microphone settings to no avail.  So maybe there is a special combination I have not yet tried ;)

---

### Post by Shay Stephens on 2006-11-09
I got it working!  I had to do two things specifically:

1) System - Preferences - Sound - Sounds - Default sound card = Voip USB Phone.

2) Opened the /boot/menu.lst file and removed the command in red
## ## End Default Options ##

title Ubuntu, kernel 2.6.17-10-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash [COLOR="Red"]acpi=force[/COLOR]
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

acpi=force allows my computer to shut down normally.  Without that, it just hangs on shutdown and I have to push the power buttun in 7 seconds to turn it off.  With it in place however, it kills the USB phone audio.

This combo doesn't ring any bells with me, but maybe one or more of you know what this means.  Is there any way I can have my cake and eat it too?!?!

---

### Post by Shay Stephens on 2006-11-10
Well now I am not so sure.  After a reboot, now I can't get it working again, either from the ear piece or mic. ](*,)

(edit) The saga continues.  I changed the default sound card back to what it was, rebooted, and now it's working again.  I don't know if it will work after another reboot, but we'll see.

---

