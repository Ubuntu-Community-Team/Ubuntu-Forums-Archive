---
title: "Desktop"
date: 2007-11-26
forum: General Help
---

### Post by nandorj78 on 2007-11-26
Hi, I have two questions:

1- How can I add a shortcut to a folder in the windows partition in the ubuntu desktop?

2- How can I add something like a performance applet in the desktop that shows how much free space I have, free memory and stuff like that?

thanks!

---

### Post by bingoUV on 2007-11-26
assuming gnome.
2. Right click on a panel. Add to panel. Look for load monitor. Add it. Right click on the monitor that appears in the panel. Select the stuff that you want.

If you want more advanced monitoring, install conky. Download one of the many good conky configuration files that are available (google it).

---

### Post by nandorj78 on 2007-11-26
Sorry for the ignorance (I'm very new to Linux), but what panel?

---

### Post by -grubby on 2007-11-26
the bars at the top and bottom

---

### Post by nandorj78 on 2007-11-26
Ok I found it, but the applets stay in the bar and not on the desktop, I tried to move it with no success... Help!!!

---

### Post by -grubby on 2007-11-26
they can't go on the desktop (as far as I know)

---

### Post by nandorj78 on 2007-11-26
I was looking for those which can go on the desktop. Anybody knows?

---

### Post by gjtoth on 2007-11-26
> **nandorj78 said:**
> I was looking for those which can go on the desktop. Anybody knows?

Try GKrellm

---

### Post by nandorj78 on 2007-11-26
What about my question number one:

how to add a shortcut to a folder in the windows partition in the ubuntu desktop?

---

### Post by bingoUV on 2007-11-26
Suppose the windows partition is mounted at /media/windows. And you want to create a shortcut to the folder /media/windows/path/to/folder. Do the following
```

cd ~/Desktop
ln -s /media/windows/path/to/folder

```

---

### Post by nandorj78 on 2007-11-26
Damn, this seems chinese to me :-/

---

### Post by bingoUV on 2007-11-27
I understand, but I could not find any graphical way to do this. Seems to be a serious limitation of nautilus. Let me try once more.

1. Right click on your desktop. 
2. Create Launcher. 
3. Choose type file. 
4. In "command" field, browse to a file in your windows partition. Note that it does not let you choose a folder, choose a file for now. Once you 
choose a file in your folder, see the text that has come up in the "command" field. Remove the rightmost part which is the filename. 
5. Click OK

---

### Post by nandorj78 on 2007-11-27
I did what you said and got the following error message:

Details: Failed to execute child process "/media/sda1/Users/royz/Desktop/fotos/" (Permission denied)

---

### Post by silviur on 2007-11-27
> **nandorj78 said:**
> Damn, this seems chinese to me :-/

Select the folder you want to create a link to, then drag it with the wheel button where you want the link, then select "Create link".

---

### Post by nandorj78 on 2007-11-27
> **silviur said:**
> Select the folder you want to create a link to, then drag it with the wheel button where you want the link, then select "Create link".

I'll try it next time I boot in Ubuntu, thanks! ;)

---

