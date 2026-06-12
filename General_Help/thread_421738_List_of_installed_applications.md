---
title: "List of installed applications"
date: 2007-04-24
forum: General Help
---

### Post by matthewmatic on 2007-04-24
Hi,

Running Fiesty.

I recently installed Google Earth. As a recent convert from Windows, I expected that it would appear under 'Applications' on the taskbar. I know that I could open it up through the terminal, but for some apps I may not know the command to type. Sometimes I may forget what I have installed. Can I find a list of installed apps and shortcuts to fire them up?

Thanks

---

### Post by ThrobbingBrain66 on 2007-04-24
You can find a list of installed packages in Synaptic.  Use the Status button to look at Installed and Installed (local or obsolete).  If I remember correctly, Google Earth doesn't set up it's own launcher, so you'll have to do it manually.  IIRC, the command for GE is ```
google-earth
```

You can then open the menu editor (System > Preferences > Main Menu) and create a launcher for GE wherever you wish.

---

### Post by matthewmatic on 2007-04-25
Thanks.

I have tried using the menu editor, but it doesn't work. It starts up but none of the buttons do anything. Do I have to run it as root somehow? If so, how?

Also, if I don't know the code for an application, where can I find out what it is?

---

### Post by destr0y on 2007-04-25
on the slight chance you missed it - you sure its not in Applications --> Internet?

(alternatively -  what ThrobbingBrain66 said)

---

### Post by Aetherius on 2007-04-25
typing ```
ls /usr/bin
``` in a terminal will list pretty much every executable you have installed, however it will be a looooooong list and might be a bit overwhelming :lolflag:

---

### Post by indytim on 2007-04-25
The following is from a previous posting (not mine):

```

dpkg --get-selections > installed-software

```

And if you wanted to use the list to reinstall this software on a fresh ubuntu setup,

```

dpkg --set-selections < installed-software
dselect

```

Hope this helps,

IndyTim

---

### Post by jfinkels on 2007-04-25
As far as I can tell, there is not really any way to list commands and their associated software names. For the most part, you will 1. just have to know, 2. assume the name of the product is the name of the binary (executable) file, or 3. read the README for instructions on running if you install the program manually.

I suppose there is no listing because in the *nix world, we assume that you know exactly what you are installing on your system and therefore we assume that you know how to run it. :P

Of course, I don't really know anything, and I could be 100% wrong.

---

### Post by Aetherius on 2007-04-26
if you install something from synaptic (or apt it from the command line) and you can't find it in the menu (or work out what command to type to run it) you can go back into synaptic, look at the properties of the installed package in question and see a list of files the package installed and where they are.

whatever is /usr/bin/* is more than likely what you are after

---

