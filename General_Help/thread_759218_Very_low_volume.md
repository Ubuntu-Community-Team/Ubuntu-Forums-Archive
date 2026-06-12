---
title: "Very low volume"
date: 2008-04-18
forum: General Help
---

### Post by luisjorge on 2008-04-18
Hello! I just installed Ubuntu hardy beta in my Inspiron 1525, which has an Intel HDA sound card, and I'm getting very low volume. I already have all the bars at the max in the ALSA mixer, and I can only get "usable" sound out of the speakers when the volume level is above 50%. Anything below, is really really low, almost unnoticeable. Is there a way to make the volume louder?

Thanks in advance!

Luis Jorge.

---

### Post by ibuclaw on 2008-04-18
That's one very cool-looking laptop.

Erm... 
Have you try the Console Mixer?

Type in
```
alsamixer
```
Use the up/down arrow keys and the tab key to navigate.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=66393&stc=1&d=1208570475[/IMG]

---

### Post by ramjet_1953 on 2008-04-19
Just right click on the volume icon in the task bar.
Left click on open volume control
Check the levels for both "Master" and "PCM"

Regards,
Roger :cool:

---

### Post by luisjorge on 2008-04-19
Hi! Thanks a lot for the replies! I already tried both solutions, and I already have PCM and Master and everything else I could find in the terminal mixer to the maximum. I changed the volume control so that my volume keys control PCM instead of Master, and I can control volume a bit better, but still is not as loud as it was with windows. Is there a file or something that I could change to make the sound louder? 

Thanks a lot!

Luis Jorge.

---

### Post by luisjorge on 2008-04-19
Hi! Just an update, I tried this solution: 

> adding to /etc/modprobe.d/alsa-base

options snd-hda-intel model=3stack

I found that in this thread: [http://ubuntuforums.org/showthread.php?t=373287&highlight=low+volume](http://ubuntuforums.org/showthread.php?t=373287&highlight=low+volume)

But this didn't work for me either. I read about someone that added "sony" instead of "3stack" because he owned a Vaio, but I don't know if I could add "dell" or something similar?

---

### Post by ibuclaw on 2008-04-19
First, to quote the thread:
Your file should look like this at the bottom.
> 
options snd-usb-caiaq index=-2
**options snd-hda-intel model=3stack**
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388


Second, you have rebooted your system, have you not?

Third, someone in the thread you posted found this [Ubuntu Doc]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller") helpful.

Regards
Iain

---

### Post by Shadowfire on 2008-04-23
Tinivole,

Thanks for the alsamixer idea... I didn't even think of that, since I figured I was dealing only with Pulseaudio.  After thinking about it... PulseAudio really hooks everything together.

Thanks for the post.. It worked for me...

---

### Post by CheesyPuffs144 on 2008-04-24
Though not quite related I don't think, changing the volume control to PCM made the sound work as expected for me. Before it was following almost an exponential curve, being really quiet for the first half, then earsplitting between one or two increases. Thanks for the idea!

---

### Post by kaunofrantas on 2008-04-27
ok, when i try to add this

options snd-hda-intel model=3stack

and try to save the file, i get the message

"You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."

I am really new to Ubuntu - this is my day 1 actually. How do I save the file?

---

### Post by manusharma on 2008-04-28
> **kaunofrantas said:**
> ok, when i try to add this

options snd-hda-intel model=3stack

and try to save the file, i get the message

"You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."

I am really new to Ubuntu - this is my day 1 actually. How do I save the file?

The reason you cannot save is that the file is owned by root and no one else has write privileges to it.  To get around this, use: 
  
[INDENT]sudo gedit /etc/modprobe.d/alsa-base[/INDENT]

The 'sudo' executes the rest of the command as root; in this case opening the file for editing.

---

### Post by kaunofrantas on 2008-04-28
manusharma,

thanks for reply. i will try this when i get back home from work

---

### Post by luisjorge on 2008-04-28
Hi! Kaunofrantas, I also found the same solution in another thread (I can't remember where, sorry), but it added *options snd-hda-intel model=**laptop*** instead of 3stack. This didn't work for me either, but maybe it can help you.
I still haven't been able to make the sound volume work properly.

Any help will be greatly appreciated! 

Luis Jorge.

---

### Post by kaunofrantas on 2008-04-28
luisjorge,

i tried this from this post...

[http://ubuntuforums.org/showthread.php?t=765126&highlight=low+volume]("http://ubuntuforums.org/showthread.php?t=765126&highlight=low+volume")

> Point to: System > Administration > Synaptic package manager, then open Synaptic. If you haven't been in Synaptic yet I'd click on reload and then see if there are any upgrades available (it'll tell you in the bar at the bottom of the screen) and if there are upgrades available I'd accept them by clicking on Mark All Upgrades ............

Then click on Search and type in: alsamixer

You'll likely see 3 items listed with alsa-utils already installed as indicated by a "green box". Now, 90% of the time I've found that installing "gnome-alsamixer" gives me the adjustments I need to solve the problem, so tick on the box next to "gnome-alsamixer" and the package manager will ask you if you want to install it .............. yes, you do! (it's removable if it doesn't solve the problem)

When you're done just click on Apply. When the installer is done just close synaptic.

Now go to Sound&Video and you should see Gnome Alsamixer in the menu, just open it and adjust away! Usually one of the last four toggles will let you increase the proper output.


... and it worked for me. I went to Gnome Alsamixer under Audio & Video,  and raised the bar Front to the top, which did the trick.

i hope this helps you as well.

cheerz

---

### Post by Sleestack on 2008-04-29
> **tinivole said:**
> That's one very cool-looking laptop.

Erm... 
Have you try the Console Mixer?

Type in
```
alsamixer
```
Use the up/down arrow keys and the tab key to navigate.


Thanks for this solution. I have a Dell Inspiron 531 and when I upgraded from Gutsy to Hardy I too had a low-volume problem. It looks like something in the upgrade reset the sound mix, but fiddling the alsamixer brought my volume back to the normal levels.

---

