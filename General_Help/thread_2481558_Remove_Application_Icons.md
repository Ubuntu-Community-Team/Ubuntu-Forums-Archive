---
title: "Remove Application Icons"
date: 2022-12-03
forum: General Help
---

### Post by Acharn on 2022-12-03
I've just newly installed ubuntu 22.04.1, completed restoring my data, and am now in the process of reinstalling the programs. I have, in my Applications window, six icons from a Windows program I tried in Wine several months ago. I've been trying to uninstall them. The program was uninstalled, purged, autoremoved long ago, but these darned icons remain. Can anyone tell me how to remove them?

---

### Post by mIk3_08 on 2022-12-05
> **Acharn said:**
> I've just newly installed ubuntu 22.04.1, completed restoring my data, and am now in the process of reinstalling the programs. I have, in my Applications window, six icons from a Windows program I tried in Wine several months ago. I've been trying to uninstall them. The program was uninstalled, purged, autoremoved long ago, but these darned icons remain. Can anyone tell me how to remove them? If the application is from the snap applications you can just run this command below in your terminal,
```
ls /var/lib/snapd/desktop/applications/*.desktop
```
then choose what desktop icon is to be deleted. Regards and cheers.

---

### Post by Acharn on 2022-12-05
Alas, the only snap I have installed is Firefox. The icons I want to remove are from a program I installed from a DVD.

---

### Post by mIk3_08 on 2022-12-06
> **Acharn said:**
> Alas, the only snap I have installed is Firefox. The icons I want to remove are from a program I installed from a DVD.
Okay, maybe you will find it here. Regards and cheers.
```
ls '/usr/share/applications'
```
```
ls '/usr/share/icons' 
```

---

### Post by Acharn on 2022-12-06
Nope, not in either one. /usr/share/icons looks like the names of themes for ubuntu. Thanks, anyway.

---

### Post by ajgreeny on 2022-12-06
If not in** /usr/share/applications** have a look in your home at **~/.local/share/applications**.

I'm not sure how they will have got there unless wine does that automatically; I haven't used wine for about 13 years and didn't use it much even then so I'm no expert but any launchers in your home **.local/share/applications** folder (ie, .desktop files) will always show in your menu system and I think will take precedence over those in **/usr/share/applications**

---

### Post by ne29914 on 2022-12-06
> **Acharn said:**
> Nope, not in either one. /usr/share/icons looks like the names of themes for ubuntu. Thanks, anyway.
The .desktop files are in:
     /usr/share/applications
Only delete the files belonging to uninstalled programs. If you want to hide other icons from the menu there are better ways.

---

### Post by Tadaen_Sylvermane on 2022-12-06
> ~/.local/share/applications/wine

Is where Wine puts .desktop files. As far as hiding others you don't see a reason to keep but don't want to eliminate altogether you can copy the proper .desktop from /usr/share/applications and put it in /usr/local/share/applications and add ```
NoDisplay=true
``` to the bottom of the files. I did that on my most recent arch install because some of the stuff just clutters up my menu.

---

### Post by ne29914 on 2022-12-06
Why copy?
Just add NoDisplay=true to the original files. No harm done.
/usr/local/share is the last place I'd put something.

---

### Post by Tadaen_Sylvermane on 2022-12-06
Because if the package is upgraded it may replace the modified file with the shipped one and you have to do it again

---

### Post by ne29914 on 2022-12-06
> **Tadaen_Sylvermane said:**
> Because if the package is upgraded it may replace the modified file with the shipped one and you have to do it again
Umm. If you read the thread, you'll see that the apps have been purged. This is only about the leftover .desktop entries.

---

### Post by Tadaen_Sylvermane on 2022-12-06
> The .desktop files are in:
     /usr/share/applications
Only delete the files belonging to uninstalled programs. If you want to hide other icons from the menu there are better ways.

I was elaborating on this statement by yourself.

---

### Post by mIk3_08 on 2022-12-06
> **Acharn said:**
> I have, in my Applications window, six icons from  a Windows program I tried in Wine several months ago. I've been trying  to uninstall them. The program was uninstalled, purged, autoremoved long  ago, but these darned icons remain. Can anyone tell me how to remove  them? Are you sure you have installed it properly using wine?
> **Acharn said:**
> Nope, not in either one. /usr/share/icons looks like the names of themes for ubuntu. Thanks, anyway. Can you name those application icons that you want to remove? If you have just used wine try ajgreeny says. Maybe the icons are located there. Regards and cheers.

---

### Post by Acharn on 2022-12-07
Yeah, that's where they were. There was a long path to the icons, but I'm so glad to finally be rid of them. Thanks a lot.

---

