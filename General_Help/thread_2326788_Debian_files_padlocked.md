---
title: "Debian files padlocked"
date: 2016-06-04
forum: General Help
---

### Post by rosswmcgee on 2016-06-04
I downloaded Debian to my Unity desktop and extracted the files. They are all padlocked. How to delete them?

---

### Post by howefield on 2016-06-04
Thread moved to the "*General Help*" forum.

---

### Post by oldrocker99 on 2016-06-04
> **rosswmcgee said:**
> I downloaded Debian to my Unity desktop and extracted the files. They are all padlocked. How to delete them?

You downloaded "Debian?" Debian is a whole distribution, on which Ubuntu is based. You probably downloaded a file which bends in .deb. Why? Is it a program which isn't available from the repositories? All Ubuntu software is installed that way.

.deb files are installed, not extracted with an archive manager:```
sudo dpkg -i nameofprogram.deb
```

If you need to delete padlocked files, try this:```
cd Desktop
sudo rmdir [nameofdirectory]
```

---

### Post by X-RED_Tech on 2016-06-04
Let me see if I can understand what's going on...
So, right after you (apparently) solved [this]("http://ubuntuforums.org/showthread.php?t=2326665"), you manage to get yourself in trouble again just after a few hours? :biggrin:
You know, trouble usually gets those who deliberately seek it.

> [COLOR=#000000]I downloaded Debian to my Unity desktop and extracted the files.[/COLOR]
What have you downloaded (and why?) and why do you extracted it? Assuming you downloaded an installation ISO that is supposed to be used "as is".
Perhaps it's better you tells us what your goal is, i.e., what are trying to do/achieve with that Debian you downloaded so we can figure out the best course of action.

---

### Post by X-RED_Tech on 2016-06-04
> **oldrocker99 said:**
> You probably downloaded a file which bends in .deb.

Apparently not, just the regular ISO image file: [http://ubuntuforums.org/showthread.php?t=2326790](http://ubuntuforums.org/showthread.php?t=2326790)
(Again, why?)

---

### Post by rosswmcgee on 2016-06-04
What I did was download the iso for debian gnome, and extracted it to the desktop. So I now have 14 padlocked folders. I did not do it twice. Moderator of linux chat moved the post to general, when I looked for the post I and did not see it I thought I had some how not submitted the post. So I posted it again. Sorry for the mix up. I just want to get the folders off the desktop and into trash.

Example :Folder says Debian, another is tools, install, and so forth. the terminal command  mentioned does not do it. I feel like a fool today.

---

### Post by X-RED_Tech on 2016-06-04
Instructions for removal already provided in post#3. Didn't it work for you?
The "why you did that" remains... ISOs usually aren't to be extracted. Namely installation media is to be either burned to CD/DVD or a USB flash drive.

---

### Post by X-RED_Tech on 2016-06-04
> **X-RED_Tech said:**
> Instructions for removal already provided in post#3. Didn't it work for you?
The "why you did that" remains... ISOs usually aren't to be extracted. Namely installation media is to be either burned to CD/DVD or a USB flash drive.


PS - On the command mentioned in post#3 you're supposed to replace the [nameof...] with the full path to the folders/files you want to delete.

---

### Post by rosswmcgee on 2016-06-04
Mark it solved: I did this chmod -R +rw

moved all files to trash emptied trash, re-booted folders and files vamoosed. Sorry for all the trouble. All is well that ends well. Which means I should leave well enough alone.

---

### Post by X-RED_Tech on 2016-06-04
You can mark it as such using the thread tools.
Then, perhaps it's a good idea to open a new thread asking for help or suggestions regarding what you intend to do with that Debian ISO.

---

