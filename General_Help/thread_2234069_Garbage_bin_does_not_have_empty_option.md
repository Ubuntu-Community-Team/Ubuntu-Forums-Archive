---
title: "Garbage bin does not have empty option"
date: 2014-07-12
forum: General Help
---

### Post by aryakaran on 2014-07-12
I have installed Lubuntu 14.04 on a Lenovo Thinkpad T420.
I did add the icon for the trash bin on the Desktop, but I'm surprised to see that when I right click on the icon there is not an option to empty the bin!
Therefore I can't empty the trash bin.

Thank you!

---

### Post by Rex Bouwense on 2014-07-12
You still should be able to empty your trash from PCManFM or is that option not working either?

---

### Post by aryakaran on 2014-07-12
Yes it is possible from PCManFM, Thanks.
But it is weird it is not in the bin itself.

---

### Post by Dennis N on 2014-07-12
I added it to the desktop to see. You are right. No option to empty. You can double-click the icon to open, then in places, right-click on trash can where there is an empty option. Neither are there different icons for empty trash and non-empty trash to give you a clue.

If I remember correctly, someone a while back made a custom action to right click on the trash icon and get the empty trash option.

---

### Post by Rex Bouwense on 2014-07-12
I remember that as well but I cannot seem to find it either.  I have been living without a desktop trash icon since before Lubuntu was recognized so it doesn't even bother me any more.  If I find that thread I will post it.

---

### Post by Dennis N on 2014-07-12
Here is how to add the empty trash option to the right-click menu of the trash icon:

The empty trash option is included in the customs action package **madebits-pca_1.0.0-1.deb** which can be downloaded from this site:

[http://madebits.com/blog/?x=entry:entry140317-141947](http://madebits.com/blog/?x=entry:entry140317-141947)

I think you could skip installing the .deb if all you were interested in was the empty trash function, because he gives directions and the necessary .desktop file further down the page. Look for the section which begins:

> Empty Trash: PcMan added a new option in this version of the PcManFm to show the trash icon on desktop, but he forgot to add an Empty Trash context menu to it, making it completely useless. To fix that, we will install first:...

---

### Post by Dennis N on 2014-07-12
I tried it out. First, I was incorrect in the previous post about the icon not having two versions - one for trash present, one for empty - it does. I decided to just use the information at: [http://madebits.com/blog/?x=entry:entry140317-141947](http://madebits.com/blog/?x=entry:entry140317-141947) instead of the .deb file.

Steps:

Install the trash-cli package:

```
sudo apt-get install trash-cli
```

Create this file in a text editor, then save it as **[FONT=Courier New]empty-trash.desktop[/FONT]** in **[FONT=Courier New]~/.local/share/file-manager/actions[/FONT]**

```
[Desktop Entry]
Type=Action
Profiles=profile-zero;
Name[en_US]=Empty Trash
Name[en]=Empty Trash
Name[C]=Empty Trash

[X-Action-Profile profile-zero]
MimeTypes=inode/directory;
Basenames=trash:///
Exec=/usr/bin/trash-empty
Name[en_US]=Empty Trash
Name[en]=Empty Trash
Name[C]=Empty Trash

```

Log out and back in. Now there is a empty trash option on the desktop trash icon.

---

