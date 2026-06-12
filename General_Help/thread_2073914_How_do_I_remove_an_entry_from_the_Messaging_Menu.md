---
title: "How do I remove an entry from the Messaging Menu?"
date: 2012-10-20
forum: General Help
---

### Post by DomB2012 on 2012-10-20
Hi,

Installed Ubuntu 12.10 two days ago on the release day, and have to say I'm very happy with it.

Only problem I have is with this Facebook entry within the Messaging Menu. 
I used Facebook to try the web apps feature, but didn't find a use for it so removed it from the launcher. But now I have this facebook entry within the Messaging Menu which I cannot get rid of, no matter what I try.

Is there somewhere I can go or code to type in the terminal, in order to force the entry to be removed?

Thanks

---

### Post by Toz on 2012-10-20
Have a look at this thread: [http://ubuntuforums.org/showthread.php?p=12267655]("http://ubuntuforums.org/showthread.php?p=12267655").

---

### Post by DomB2012 on 2012-10-20
Thanks but didn't help. Went to the folder that apparently stores all items within the Messaging Menu, but Facebook wasn't there.... Yet it's still on mine :(

> **Toz said:**
> Have a look at this thread: [http://ubuntuforums.org/showthread.php?p=12267655](http://ubuntuforums.org/showthread.php?p=12267655).

---

### Post by Toz on 2012-10-21
> **DomB2012 said:**
> Thanks but didn't help. Went to the folder that apparently stores all items within the Messaging Menu, but Facebook wasn't there.... Yet it's still on mine :(

Was this the ~/.local/share/applications folder? Can you open a terminal, run the following command, and post back the results?
```
ls ~/.local/share/applications/*.desktop
```

---

### Post by DomB2012 on 2012-10-22
> **Toz said:**
> Was this the ~/.local/share/applications folder? Can you open a terminal, run the following command, and post back the results?
```
ls ~/.local/share/applications/*.desktop
```


This is what the terminal replied back with:

/home/dominic/.local/share/applications/facebookfacebookcom.desktop
/home/dominic/.local/share/applications/fogger-26cae7718c32180a7a0f8e19d6d40a59.desktop
/home/dominic/.local/share/applications/Force_Quit.desktop
/home/dominic/.local/share/applications/userapp-Firefox-XK1WFW.desktop
/home/dominic/.local/share/applications/wine-extension-chm.desktop
/home/dominic/.local/share/applications/wine-extension-gif.desktop
/home/dominic/.local/share/applications/wine-extension-hlp.desktop
/home/dominic/.local/share/applications/wine-extension-htm.desktop
/home/dominic/.local/share/applications/wine-extension-html.desktop
/home/dominic/.local/share/applications/wine-extension-ini.desktop
/home/dominic/.local/share/applications/wine-extension-jfif.desktop
/home/dominic/.local/share/applications/wine-extension-jpe.desktop
/home/dominic/.local/share/applications/wine-extension-msp.desktop
/home/dominic/.local/share/applications/wine-extension-png.desktop
/home/dominic/.local/share/applications/wine-extension-rtf.desktop
/home/dominic/.local/share/applications/wine-extension-txt.desktop
/home/dominic/.local/share/applications/wine-extension-url.desktop
/home/dominic/.local/share/applications/wine-extension-wri.desktop
/home/dominic/.local/share/applications/wine-extension-xml.desktop


I don't know how to access the  ~/.local/share/applications folder... :(

Thanks, Dominic

---

### Post by Toz on 2012-10-22
Try deleting: > /home/dominic/.local/share/applications/facebookfacebookcom.desktop

To delete it from the terminal, type in the following command:
```
rm /home/dominic/.local/share/applications/facebookfacebookcom.desktop
```
...(you may need to log out and back in again for it to take effect)

> I don't know how to access the ~/.local/share/applications folder... 
When you are in the file manager (nautilus) press Ctrl+H and this will show hidden folders. Hidden folders are those that start with a . (period). Then you can traverse down to the correct location. Ctrl+H again will hide the hidden folders.

---

### Post by DomB2012 on 2012-10-22
> **Toz said:**
> Try deleting: 

To delete it from the terminal, type in the following command:
```
rm /home/dominic/.local/share/applications/facebookfacebookcom.desktop
```...(you may need to log out and back in again for it to take effect)


When you are in the file manager (nautilus) press Ctrl+H and this will show hidden folders. Hidden folders are those that start with a . (period). Then you can traverse down to the correct location. Ctrl+H again will hide the hidden folders.

Thank you! It's disappeared from the Messaging Menu! :)

---

