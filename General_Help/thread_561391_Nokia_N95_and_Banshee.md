---
title: "Nokia N95 and Banshee"
date: 2007-09-27
forum: General Help
---

### Post by trevorv on 2007-09-27
I have a Nokia N95 which acts as a USB mass storage device, and I use it as a portable music player. When plugged in though, Banshee (or Rhythmbox for that matter) don't recognise it. It works fine under GNOME, but these apps obviously just don't realise it's a music player. How can I make them see it?

Cheers, 
Trevor

---

### Post by tgalati4 on 2007-09-27
What version of Banshee are you using?  (If not at 0.13.1 then you should try it.)

Update:  I can't get my old 1 GB sandisk USB player to show up in Banshee 0.13.1, so I doubt if it will work with the Nokia N95.

Try running:

>bashee --debug --dap /dev/sda1

And see what error messages you get.

I get: (for device "PLAYA" located at /dev/sda1)

Debug: [9/28/2007 3:05:26 PM] (Testing device for DAP support) - /org/freedesktop/Hal/devices/volume_label_PLAYA
Debug: [9/28/2007 3:05:26 PM] (DAP has not been added) - /org/freedesktop/Hal/devices/volume_label_PLAYA

I'm not sure what is going on.

---

### Post by tgalati4 on 2007-09-28
Here's something to try:

SSS007 Having Rhythmbox/Banshee recognize Sansa player

Here is the post from the ABi forum, I give complete credit to this guy:

Quote:
Originally Posted by Cgil View Post
Just added support to banshee... It's quite easy:

1.Set your sansa in MSC mode.
2.Connect it to the computer.
3. In the root folder of your sansa create a text file( If you are using GNOME use the following in nautilus: right click-> Create a document-> empty file. This might work for KDE but I'm not sure...)
4.Now, name your file as .is_audio_player

Start Banshee and it should recognize it:

My player shows up in Banshee as:

SDMX1 MP3 Player

I was able to copy 53 songs to it in 3 groups.  It choked for some reason when I tried to copy the entire playlist at once.  Not sure why.

As others have said, it's buggy but it works.  Usually.

---

