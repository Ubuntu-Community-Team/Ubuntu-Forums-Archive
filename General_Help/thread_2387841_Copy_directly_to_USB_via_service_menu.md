---
title: "Copy directly to USB via service menu?"
date: 2018-03-24
forum: General Help
---

### Post by Chip88 on 2018-03-24
Hi there,

I'm running KDE 16.04 and would like to have a service menu in Dolphin to copy files directly to a specific folder (*drucken*) on a specific pendrive (*CHIP T*).

I know, there is already a service menu "Copy to / Move to", but I want to have the *copy to* - option directly on "Top Level". Furthermore, I want to save some time and avoid searching through the whole menu which opens.

So, I really would like to make a right click on a file and then be able to send directly a file to my USB,
I tried it with **kioclient**, but it didn&#8217;t work to send a file to USB with: *Exec=kioclient cp %U /media/mark/CHIP T/drucken*.
On the other hand, I tried it with *Exec=kioclient cp %U /$HOME/ *and it really sent the chosen file to my home folder.


So what am I doing wrong? Does anyone has any suggestions?!

Thank you very much for your help!

Kind regards,
Chipy

---

### Post by #&amp;thj^% on 2018-03-24
Just a thought is the path a valid mount? I had to create that first. ;)
I was also playing with KDE for a short period.
The following worked for me on Ubuntu 16.04 after you figure your initial path problem.

place your scripts in the directory [B]"~/.local/share/kservices5/ServiceMenus/"
[/B]
run 
```
kbuildsycoca5
```

scripts will be visible in new dolphin instances.

one appropriate directory for *.desktop files is>> /usr/share/kservices5/ServiceMenus/

(compare the output of dpkg -L ark to find similar file locations concerning the ark submenus)
Hope this is useful, BTW No KDE here anymore so I won't be any further use to you. :(

---

### Post by Chip88 on 2018-03-24
Hi 1fallen,

thank you very much for your fast reply.
Unfortunately, I didn’t understand what you mean with "is the path a valid mount"
How can I check this or create it?

All my *.desktop - files are in *~/.local/share/kservices5/ServiceMenus/*.

EDIT:
[COLOR=#111111][FONT=Ubuntu]Output of command ```
sudo lsblk -f
``` is:[/FONT][/COLOR]
```
[FONT=monospace][COLOR=#000000]sdc                                                               [/COLOR]
&#9492;&#9472;sdc1 vfat   CHIP T        B106-FB53                            /media/mark/CHIP T
[/FONT]
```

Thanks in advance!
Chipy

---

### Post by slickymaster on 2018-03-24
*Thread moved to **General Help**.*

---

