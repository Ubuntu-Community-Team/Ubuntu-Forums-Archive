---
title: "Two questions concerning resolution and settings"
date: 2007-07-24
forum: General Help
---

### Post by JMO707 on 2007-07-24
1th: I use the Digital Vibrance color enchancement from my Nvidia videocard, however, it only applies when I open, manually, nvidia-settings. Not at the X start.

2nd: I want to change Shell resolution, but dont know where to look. I used some gnome-boot tool, and now it is of 640x480 or something like that.

Thanks!

---

### Post by DagMan on 2007-07-24
1.  I have an NVIDIA card and I don't know what it is.  This has me thinking "What is it?  Do I have it?  Is it enabled?  How do I use it?"  

2. You want to add vga=somevalue to your kernel boot line in the file /boot/grub/menu.lst like in this post except this guy is having a differant issue, it's still the route to accomplish what you want [http://ubuntuforums.org/showthread.php?t=104097&highlight=virtual+terminal+resolution](http://ubuntuforums.org/showthread.php?t=104097&highlight=virtual+terminal+resolution)

---

### Post by JMO707 on 2007-07-25
[Digital Vibrance]("http://www.nvidia.es/object/feature_dvc.html")

There should be a control for you too ;)

And the resolution thing... I used 792, to have a 1024x768 at 32bpp, then made a sudo update-grub, and..., nothing. Its still in some crappy resolution. Is that the format that the resolution thing has to have?, 'cos I remember problems with that where I was asked for an input in some kind of alphanumeric code, like 0F07 or something like that.

---

### Post by DagMan on 2007-07-26
You dont have to update your grub.  It might have actually taken the value out since it isn't a default value.  I think the best way is to jot down all the values and then at boot time when the grub menu comes up hit 'e' then put it at the end of the kernel line and when you do it this way it doesn't get saved to the grub file so when you find something that works, you can then add it to menu.lst 
This might screw up the usplash from diplaying now that I think of it.  Dont know what to say about that :confused:
Anyhow, the values that will survive a grub update are elsewhere in the file and you dont need to update it, it's as if you're doing it manually when you edit the file.

The digital vibrance looks pretty neat.  I looked in my settings sort of breifly yesterday and didn't see it.  I think I'll have a harder look.

I just remembered this from an older computer I had.  Run nvidia-settings like this when Gnome starts by putting it in sessions->startup programs
**nvidia-settings --load-config-only**

---

