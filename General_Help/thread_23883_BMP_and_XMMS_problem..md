---
title: "BMP and XMMS problem."
date: 2005-04-04
forum: General Help
---

### Post by Kimm on 2005-04-04
ok, yesterday I desided to upgrade to Hoary, so I followed the instructions on this webbsite and the upgrade went smoothly. Today when I booted into it (made the upgrade at 00:00 at night, was quite tired after) I noticed that BMP and XMMS have stoped working. I installed BMP from source so its not a backport package, so, its not becos of that. I dont know why XMMS wount work but they react the same way.

When I open the file, well, nothing happens the player just stands there then, when I try to press play it freezes and I have to terminate it from the console, this goes for both BMP and XMMS.

I tried uninstalling BMP and installing it with apt-get, didnt work
I tried uninstalling BMP (again) and recompile it from source, didnt work
I tried reinstalling XMMS, didnt work
I tried downloading and compiling XMMS from source, didnt work

I allways get the same error, the app doesnt do anything after I load the file and when I press play it freezes. I have to use Xine to play music atm there works ofcourse but I prefer to have that little handy BMP window in the upper right corner of my screen.

Can anyone help???

---

### Post by NeoChaosX on 2005-04-04
In Beep or XMMS, check the audio output plugins. For some reason, in Hoary,anything that tries to use the OSS sound system doesn't work. Set the audio output to either ALSA or ESD and then it will work.

---

### Post by Kimm on 2005-04-04
hm... I tried, but Beep cant find alsa, I can only select OSS, I tried installing most packages that had anything to do with alsa in Synaptic but there is no change :-k

---

### Post by NeoChaosX on 2005-04-04
Try chaning to eSound (that's ESD) instead. That's strange that there's no ALSA, though - Beep should have at least ALSA, OSS and ESD plugins.

---

### Post by Kimm on 2005-04-05
ah, I fixed it, aparently ESD wasnt installed... I installed it and after recompiling Beep it worked ^^ thanks for helping!! :)

---

