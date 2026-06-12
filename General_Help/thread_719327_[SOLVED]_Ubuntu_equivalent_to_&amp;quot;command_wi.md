---
title: "[SOLVED] Ubuntu equivalent to &amp;quot;command window here&amp;quot;?"
date: 2008-03-09
forum: General Help
---

### Post by startling on 2008-03-09
The Windows powertoy "Open Command Window here" is a very useful and quick way to get to a command line in any folder. In Explorer, you simply right-click on a folder and select "Open Command Window here" from the context menu, which then opens a DOS command line with the prompt set to the full path to that folder.

Is there an equivalent for Ubuntu? Once I've found the folder I need in Nautilus, I find it tedious and tiresome to then have to CD to that same path again in a Terminal - it just seems silly having to navigate twice, once in Nautilus and then again in Terminal. There must be a better way. Is there?

---

### Post by banewman on 2008-03-09
I saw a nautilus script for that at gnome-look if I remember correctly.
:)

---

### Post by adityakavoor on 2008-03-09
```
sudo apt-get install nautilus-open-terminal
```

---

### Post by Oldsoldier2003 on 2008-03-09
> **startling said:**
> The Windows powertoy "Open Command Window here" is a very useful and quick way to get to a command line in any folder. In Explorer, you simply right-click on a folder and select "Open Command Window here" from the context menu, which then opens a DOS command line with the prompt set to the full path to that folder.

Is there an equivalent for Ubuntu? Once I've found the folder I need in Nautilus, I find it tedious and tiresome to then have to CD to that same path again in a Terminal - it just seems silly having to navigate twice, once in Nautilus and then again in Terminal. There must be a better way. Is there?
in a terminal:
```
sudo aptitude install nautilus-open-terminal
```

then:
```
sudo killall nautilus
```

you're set!

---

### Post by lespaul_rentals on 2008-03-09
When I use Gnome, I can usually press F4 and display a Terminal at the current location.

---

### Post by Oldsoldier2003 on 2008-03-09
> **adityakavoor said:**
> ```
sudo apt-get install nautilus-open-terminal
```

have to killall nautilus for it to take effect...

---

### Post by adityakavoor on 2008-03-09
> **Oldsoldier2003 said:**
> have to killall nautilus for it to take effect...

Yeah I forgot that, :)

---

### Post by yaknowwat on 2008-03-09
&& command can be used here for a lazy single line copy paste.
```
sudo aptitude install nautilus-open-terminal && killall nautilus
```

---

### Post by breaking on 2008-03-09
This may sound more complicated than necessary, but I thought I mind as well point it out:
If what you're trying to do is open a file with sudo, all you have to do is right-click on the file, 'open with...', 'open with other application', choose gksudo. If it's not on the list, choose 'use a custom command' and type in gksudo (in front of whatever you actually want to use). If you've already run that file with sudo, you can directly right-click and click 'open with sudo' (or gksudo, whichever is the case). 
Note that 'sudo' might not work here because, since you're not using a terminal, you won't be able to type in your password when the command-line asks for it. Use gksudo instead.

---

### Post by startling on 2008-03-09
Thanks everyone!

> **yaknowwat said:**
> && command can be used here for a lazy single line copy paste.
```
sudo aptitude install nautilus-open-terminal && killall nautilus
```

I ran that command, and it installed so that now I have the line "Open in Terminal" in the context menu, but when I click on "Open in Terminal" no terminal appears, and it also crashes Nautilus! (Nautilus goes grey, says it's not responding and I have to force quit it).  :(

---

### Post by ugm6hr on 2008-03-09
I like Thunar (in XFCE / Xubuntu), since it can do this as default.

Since switching to Gnome, I have had to use a custom script.

I have attached it here as a .txt file (just rename without the .txt), ensure it is an executable script, then put it in /username/.gnome2/nautilus-scripts

OpenTerminalHere will then appear on right click->Scripts

---

### Post by startling on 2008-03-09
> **ugm6hr said:**
> 

OpenTerminalHere will then appear on right click->Scripts

Thanks ugm6hr. I followed your instructions but when I right-click in Nautilus there is no option for Scripts nor for OpenTerminalHere. Do I have to restart or something? Or enable scripts in Nautilus or something like that?

---

### Post by startling on 2008-03-09
It works, thank you ugm6hr!

I don't know what changed, (I had tried renaming the script with a .sh extension but I have no idea if that affected it or not), but when I just went back to Nautilus and right-clicked there was a menu item called Scripts and when I ran your script I got the correct Terminal. (I can't believe I missed it before because I was careful to check every line before making my previous post, although I have been known to be quite dim at times!)

Thanks again!

---

### Post by ugm6hr on 2008-03-09
No worries.

It isn't really my script - I found it somewhere on the wild web.

Glad it works, however it happened!

---

### Post by yaknowwat on 2008-03-10
> **startling said:**
> Thanks everyone!



I ran that command, and it installed so that now I have the line "Open in Terminal" in the context menu, but when I click on "Open in Terminal" no terminal appears, and it also crashes Nautilus! (Nautilus goes grey, says it's not responding and I have to force quit it).  :(

Its suppose to do that as nautilus restarts itself automatically then its completely refreshed.

---

### Post by A$h X on 2008-03-12
This is an extremely useful tip and makes using terminal that much easier. Is there a way I could run a script via right click with different scripts being run according to what file type was right-clicked on?

---

### Post by startling on 2008-03-13
> **yaknowwat said:**
> Its suppose to do that as nautilus restarts itself automatically then its completely refreshed.

I don't think it was supposed to crash Nautilus every single time I tried to use it! Even after an uninstall and reinstall, in case something was corrupted, and then a complete system reboot, it kept crashing. For some reason it was never going to work on my system. The script posted by ugm6hr, on the other hand, works flawlessly.


> **A$h X said:**
> This is an extremely useful tip and makes using terminal that much easier. Is there a way I could run a script via right click with different scripts being run according to what file type was right-clicked on?

Is this the sort of thing you mean? 
[http://www.howtogeek.com/howto/ubuntu/add-open-with-gedit-to-the-right-click-menu-in-ubuntu/](http://www.howtogeek.com/howto/ubuntu/add-open-with-gedit-to-the-right-click-menu-in-ubuntu/)

---

### Post by rickyrockrat on 2008-05-02
Use Thunar - it has it built-in, Right-click, then open terminal here.

---

