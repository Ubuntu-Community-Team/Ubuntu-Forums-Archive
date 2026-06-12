---
title: "Low brightness at startup"
date: 2008-05-08
forum: General Help
---

### Post by _godbout_ on 2008-05-08
Sorry if there are already some solutions about this problem, but I've checked the forum (and not only) and I didn't find any solution or any new topic related. I've got this trouble since Gutsy and I thought that Hardy would solve it but no. Actually, Hardy doesn't save my brightness options. It always starts at the lowest level possible. I have then to change it manually. Is there any way to set the brightness to 100% automatically?

I know that many people had the trouble before, but I don't see any post about that for Hardy. Do people solve it by themselves?

edit: I've checked for like 45 minutes, and just now I've found a topic related for Hardy... :D

---

### Post by retrow on 2008-05-08
In terminal type in:
gconf-editor

Then: apps > gnome-power-manager > backlight

Set the numbers for brightness as per your liking :)

---

### Post by tacutu on 2008-05-08
i had the same problem... tried everything to solve it but eventually it turned out somehow the bios settings were wrong. so i just set the brightness from the bios and voila, it's fine.
the odd thing, though, it that the bios settings got (misteriously) changed at about the same time i installed Hardy...

---

### Post by _godbout_ on 2008-05-08
Hey,

Thanks, but it actually doesn't help me that much :D
I set both values for backlight to 100, but when I restart the computer, it comes to 0 again!

---

### Post by Catalyst2Death on 2008-05-08
[http://ubuntuforums.org/showthread.php?t=784683&page=2](http://ubuntuforums.org/showthread.php?t=784683&page=2)

you want post 15

I would retype it all again, but its just as easy to go to the page and read it.

---

### Post by tacutu on 2008-05-08
so wait... which one did you try? The bios settings or the gconf-editor one?

---

### Post by _godbout_ on 2008-05-08
> **Catalyst2Death said:**
> [http://ubuntuforums.org/showthread.php?t=784683&page=2](http://ubuntuforums.org/showthread.php?t=784683&page=2)

you want post 15

I would retype it all again, but its just as easy to go to the page and read it.
Ah! I've read this post before but I was not able to find it back!
I'm gonna try that and let you know, thanks!
Actually I've tried before to sudo vi the brightness file, but I couldn't save it. Each time vi tells me that the file has been updated while reading and doesn't allow me to save it. I don't have any VGA folder by the way, I have to get the file from a IGUF or something like this, or Z004 something like that. But I'll try your tip, thanks. 

> **tacutu said:**
> so wait... which one did you try? The bios settings or the gconf-editor one?
I've tried the gconf. I didn't see anything in the BIOS about the brightness, and everything works fine with Vista, so I guess that it's ok :)

---

### Post by Catalyst2Death on 2008-05-08
so if you use "# echo - n 50 >"

it pipes/streams (i'm not sure which word is appropriate) the number 50 into the brightness file, so you shouldn't need to use another editor like vi... the command works (at least for me, and other people).

most importantly you MUST be root!!!

---

### Post by _godbout_ on 2008-05-10
Unfortunately it seems that it doesn't work for me!
I'm root and I changed the value, but at the next start the screen is still dim and the value in the file has been set back to 10. I've tried to have a look in the proc/acpi/acer folder, but I can't append something to the brightness file, don't know why yet.

---

### Post by _godbout_ on 2008-05-21
Ok, I've checked the acer folder, it doesn't work neither. Or let's say that it doesn't work as I want it to work. If I change the number, the brightness is changing, but at each restart, it gets back to his low value.
Any solution?

---

