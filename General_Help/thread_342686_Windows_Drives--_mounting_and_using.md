---
title: "Windows Drives-- mounting and using?"
date: 2007-01-20
forum: General Help
---

### Post by Cheesemold on 2007-01-20
For some reason I need to post this from a separate computer, as the one that I was on keeps crashing when I try to make this post.

I need to be able to mount my windows drives and be able to transfer my much needed files from the broken computer to a more stable one.

i use:
sudo mount -t ntfs /dev/hdb1 /windows/c/ -o ro

to mount it. And I've been using:
sudo nautilus

to access it.

I can browse the files, and it seems like i could open them, But I CANNOT drag one folder into a network computer, or even onto my desktop in linux.  This, as one could imagine, is a HUGE PROBLEM.
I think it may be something to do with file/folder permissions, but then there's another problem.  I CANNOT change permissions, or rather, there is no coherent explanation HOW one goes about changing permissions in linux's manuals or help files.

Please, somebody help me with this so that I can get on with my life and stop tearing the hair out of my flesh.

---

### Post by teaker1s on 2007-01-20
I'm imagining that the drive is mounted read only look here it has mounting guide
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Hard_Drive]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Hard_Drive")
secondly in terminal
[COLOR="Red"]gksudo /usr/bin/nautilus[/COLOR]
will give root browser access

---

