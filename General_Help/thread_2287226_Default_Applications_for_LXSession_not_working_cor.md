---
title: "Default Applications for LXSession not working correctly Lubuntu 14.04.2"
date: 2015-07-17
forum: General Help
---

### Post by roler2 on 2015-07-17
Whenever I change a Default Application in LXSession from "Disabled" to a Program, such as LibreOffice Calc for the Spreadsheet, it always reverts back to "Disabled", or to some other Program, such as LibreOffice Math, which isn't even in the List. This also happens with the Image Viewer and the Audio Player. Both either revert back to "Disabled" or to some other Program which isn't even on the List. It doesn't matter if I reboot or log out and log back in or even if I change the Program manually, it still reverts back to "Disabled" or to some other Program not on the List.  

Is there a way to fix this so the correct Program displays and doesn't revert back to "Disabled"?

Thank you for any assistance you may be able to provide.

---

### Post by vasa1 on 2015-07-17
> **roler2 said:**
> Whenever I change a Default Applications for LXSession ...
Since it was first introduced, I found *Default Applications for LXSession* to be difficult to understand.

What happens if you right-click on a file (in your file manager or on the desktop) and try to set the default using the **Open with ...** option in the right-click context menu? I find that route quite efficient.

---

### Post by roler2 on 2015-07-18
Thank you for the suggestion. However it did not change anything in LXSession. Both the Image Viewer as disabled and the Spreadsheet section as LibreOffice Math stay the same. Maybe there is a LXsession file that needs to be modified?

---

### Post by vasa1 on 2015-07-18
> **roler2 said:**
> ... Maybe there is a LXsession file that needs to be modified?
I see there is ~/.config/lxsession-default-apps/settings.conf. But I'm not sure about modifying it directly.

I don't use LXSession at all. I login to the Openbox session option and so can't be of more help.

---

### Post by roler2 on 2015-07-18
In regards to: ~/.config/lxsession-default-apps/settings.conf

Any changes I make to this file are not being saved upon reboot or logging out and logging back in. Changes are saved prior to reboot or logout. However, upon logging back in or rebooting, no changes are saved and the entire file reverts back to the exact way it was prior to reboot or log out and so do the respective LXSession default Program issues. This may be a reason why I am not able to make the necessary default Program changes to LXSession. Is there a way to fix this?

---

### Post by roler2 on 2015-07-19
I also tried uninstalling LXSession-default-apps, then clearing out all relevant associated files and/or folders, then reinstalling. Didn't do anything. Same issues as stated. Could it be a bug in LXSession?

---

### Post by vasa1 on 2015-07-19
> **roler2 said:**
> I also tried uninstalling LXSession-default-apps, then clearing out all relevant associated files and/or folders, then reinstalling. Didn't do anything. Same issues as stated. Could it be a bug in LXSession?
I've gone through some of your other threads here and I appreciate the effort you take. So I hope I don't come across too negatively when I point you to this page: [https://wiki.ubuntu.com/Lubuntu/Testing/14.04](https://wiki.ubuntu.com/Lubuntu/Testing/14.04).

That said, I logged into a Lubuntu session after a long time and took the attached screenshot.

It lists
[LIST]
[*]sylpheed for Email ... but I uninstalled it a long time ago
[*]pidgin for Communication 1 ... but I uninstalled it a long time ago
[*]audacious for Audio player ... but I uninstalled it a long time ago
[*]Leafpad for text editor but text files open in Mousepad (which I've installed) even though Leafpad is also present
[*]abiword for Document but I uninstalled it a long time ago; I use LibreOffice's Writer instead.
[/LIST]

Just for a lark, I made a change from Gnumeric to LibreOffice Calc and pressed "Reload". That logged me out of the Lubuntu session!

Anyway, I'm back to my Openbox session.

The page I linked to gives me the impression that resources are pretty slim on the ground and that while you're free to file bugs, the resources that are available may be going into prepping the LXQt version of Lubuntu.

---

### Post by Dennis N on 2015-07-19
To set default applications, you have to set them by mime type. Vasa1's directions in post #2 is a way to do that (right-click menu for file:  properties > general > open with..).

Based on what I have read and noticed, Lubuntu uses the first application in /usr/share/applications/mimeinfo.cache as the default for each mime type, overridden by any entries in ~/.local/share/applications/mimeapps.list. This second file is changed by the method in post #2. 

mimeinfo.cache is built from the mime types listed in .desktop files. It's entries are mirrored into the right-click menu (modified by mimeapps.list) to give you the listed application options to open a file - the top one is the default. Changes made by the user to mimeinfo.cache are not permanent - it can be changed by the system. 

That settings dialog section you are trying to use is broken. It sometimes doesn't even make sense. Setting a default for "Document" as Abiword - what does that even mean? What mime types would that include?

---

### Post by vasa1 on 2015-07-19
> **roler2 said:**
> ... Could it be a bug in LXSession?
You can find more Lubuntu users here: [https://lists.ubuntu.com/mailman/listinfo/lubuntu-users](https://lists.ubuntu.com/mailman/listinfo/lubuntu-users)

Maybe someone can advise you about LXSession.

---

### Post by roler2 on 2015-07-19
Thank you so much for all of the advice and guidance! It does appear the LXSession-default-apps is broken to some degree. For example, the Image Viewer shows "Disabled" so I changed it to gpicview. I also clicked on reload and it logged me out as well. When I logged back in the Image Viewer was again showing as "Disabled". So I changed the Spreadsheets section to LibreOffice Calc (it was set at LibreOffice Math), and again clicked on reload and got logged out again. Logging back in the Spreadsheets section once again showed LibreOffice Math.

Would it be beneficial to uninstall just the LX-Session-default-apps and leave it uninstalled? Or would that mess up everything with LXSession components? The "Open With" right-click works fine but it also does not change the Default Application in the Default Apps LXSession.

Thank you all again for your awesome assistance! However, being that it is broken maybe it is best to uninstall it? Or just leave it alone? It doesn't seem to be affecting opening of any file types. I also agree I don't really see the need for it, especially if it is broken.

---

### Post by roler2 on 2015-07-20
UPDATE: I completely uninstalled lxsession-default-apps and removed all associated relevant files/folders. Everything still works just fine. Pictures open, documents open, MP3's play, even with the Default Programs that I have installed that are different from the Programs that were with the initial installation. I don't have to utilize "Open With" either. I am not saying uninstalling it will work for you, however it appears to me that the default-apps Application is really not needed and unnecessary.

---

### Post by vasa1 on 2015-07-20
> **roler2 said:**
> UPDATE: I completely uninstalled lxsession-default-apps and removed all associated relevant files/folders. Everything still works just fine. Pictures open, documents open, MP3's play, even with the Default Programs that I have installed that are different from the Programs that were with the initial installation. **I don't have to utilize "Open With" either.** I am not saying uninstalling it will work for you, however it appears to me that the default-apps Application is really not needed and unnecessary.
I use "Open With" only for specific purposes or to set a particular file type to open with a specific application.

As I wrote earlier, I didn't use the lxsession-default stuff after I found it not working as I expected. I haven't uninstalled it either. I just don't use it. In any case, an Openbox session doesn't use any lxsession/lxde stuff AFAICT.

---

