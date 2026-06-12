---
title: "[SOLVED] How to create shortcuts for remote folders (smb shares)"
date: 2013-08-02
forum: General Help
---

### Post by julien-dal-col on 2013-08-02
Hello,

I am running 13.04 and I need to create shortcuts pointing to folders located on smb shares. These shortcuts could be on the desktop or on the sidebar, I don't really care, but for now, I can't make any.

This is probably a "stupid" question, sorry about that.

Thank you very much in advance for your help.
Best,
-J-

ps: I can connect to the remote servers, but when trying to "make link" on a specific folder it tells me : "The target doesn't support symbolic links."

---

### Post by sudodus on 2013-08-02
Hello :-)

Which flavour of Ubuntu are you running (Lubuntu, Xubuntu, Ubuntu, Kubuntu)?

In most file browsers you first connect to the smb share (you seem to know how to do that already). Then, when connected, you ***bookmark*** it (using the menu item for it). It will show on the left panel, and you can edit the name of the bookmark afterwards.

---

### Post by julien-dal-col on 2013-08-02
Thank you so much :)
I am running Ubuntu 13.04.
Thanks to your explanations I can now bookmark (ctrl+d) any remote folder to the sidebar of the "explorer" (it is called "Files" I thought it was "Nautilus"... I need to catch up with the evolution of Ubuntu I guess)...

Now, any idea on how to place these shortcuts on the desktop or on the sidebar of the desktop (the Launcher)

Best,
-J-

---

### Post by sudodus on 2013-08-02
You are welcome :-)

It is called Files, but it is good old Nautilus in Ubuntu (which you see if you click 'Help -- About')

I don't think you should waste space on the sidebar of Unity for those bookmarks. There is an icon from Nautilus. Click on that, and then on the bookmark in the sidebar of Nautilus. An alternative is to make a ***desktop launcher*** (a clickable icon, that starts Nautilus, maybe possible to directly open that shared folder).

---

### Post by julien-dal-col on 2013-08-02
> **sudodus said:**
> It is called Files, but it is good old Nautilus in Ubuntu (which you see if you click 'Help -- About')
Well, when I click
Files->about files
it says : "Files 3.6.3"
:S

> **sudodus said:**
> I don't think you should waste space on the sidebar of Unity for those bookmarks.
I have plenty of it...

 > **sudodus said:**
> An alternative is to make a ***desktop launcher*** (a clickable icon, that starts Nautilus, maybe possible to directly open that shared folder).
:D great! How can I do that? there's no right-click -> new launcher anymore...

Tx again
-J-

---

### Post by sudodus on 2013-08-02
I must admit, that I have not tried Ubuntu 13.04 very much, I'm running Ubuntu 12.04.2 LTS as my main system (which still has Nautilus), and Lubuntu 13.04 and 13.10 for testing. You taught me something :-)

I don't know if it will work, but you can always test if the old kind of desktop file would work

I have a file in my Desktop directory with this name

**[FONT=courier new] Nautilus.desktop[/FONT]**

and the following content (it is a text file)

```
[Desktop Entry]
Encoding=UTF-8
Type=Application
Name=Nautilus
Name[sv_SE]=Nautilus
Exec=/usr/bin/nautilus --no-desktop
Comment[sv_SE]=kraftfull filhanterare
Icon=/usr/share/icons/hicolor/scalable/apps/nautilus.svg
```

I guess you can change the Exec line to contain **[FONT=courier new]files[/FONT]** instead. Probably it will work to add the shared folder as a parameter.

Find the path like this

```
which files
```

```
/path-you-found/files smb://server-address/shared
```

I think it works because the following works for me using Nautilus (for a shared folder at the server 192.168.0.2 in my LAN)

```
/usr/bin/nautilus --no-desktop smb://192.168.0.2/shared
```

---

### Post by julien-dal-col on 2013-08-02
It works! :D
You're the best!

I can even drag and drop those on the launcher ;)

Best,
-J-
ps: Guess what... There is still a file call Nautilus in /usr/bin... and when I launch it, "Files" pops up...

---

### Post by sudodus on 2013-08-02
I'm glad it works for you :KS

So Files is an alias of Nautilus or vice versa :-)

---

### Post by dvn3ch on 2013-09-22
I know that this is resolved and somewhat older post but I have been working on this for the last hour and realized that the Samba share doesn't care about a space in the folder names but the desktop shortcut [iconName.desktop] code does.  When I had a folder named "Shared Videos" I could point and click my way directly to it.  However, I needed a direct link for my HTPC that is not XBMC but just a stripped down version of Ubuntu 12.04 LTS.  When I tried the above solution it was giving me a "spelling error" error.  After retyping a few times I tried removing the space in between words Shared and Movies on the share drive.  Well wouldn't you know, it worked perfectly.  I recreated it on another samba share folder that had a space and it performed exactly the same way.  Removed the space and it worked as advertised.

In short, folder names should not have spaces in them if the smb: command is used.  Example smb://myNAS/folder1/Shared%20Videos/Movies does not play well, smb://myNAS/folder1/SharedVideos/Movies does play well.  Even if you remove the percent-encoding (%20), and just put in a space you will get an error.

---

### Post by imrumpf on 2014-04-10
Just wanted to say thank you for that little tidbit of info regarding the spaces, it actually was the final piece to a puzzle I was trying to figure out, thank you!! :P

---

### Post by eduard-budai on 2015-03-02
> **sudodus said:**
> I must admit, that I have not tried Ubuntu 13.04 very much, I'm running Ubuntu 12.04.2 LTS as my main system (which still has Nautilus), and Lubuntu 13.04 and 13.10 for testing. You taught me something :-)

I don't know if it will work, but you can always test if the old kind of desktop file would work

I have a file in my Desktop directory with this name

**[FONT=courier new] Nautilus.desktop[/FONT]**

and the following content (it is a text file)

```
[Desktop Entry]
Encoding=UTF-8
Type=Application
Name=Nautilus
Name[sv_SE]=Nautilus
Exec=/usr/bin/nautilus --no-desktop
Comment[sv_SE]=kraftfull filhanterare
Icon=/usr/share/icons/hicolor/scalable/apps/nautilus.svg
```

I guess you can change the Exec line to contain **[FONT=courier new]files[/FONT]** instead. Probably it will work to add the shared folder as a parameter.

Find the path like this

```
which files
```

```
/path-you-found/files smb://server-address/shared
```

I think it works because the following works for me using Nautilus (for a shared folder at the server 192.168.0.2 in my LAN)

```
/usr/bin/nautilus --no-desktop smb://192.168.0.2/shared
```

I can confirm that this works: in Lubuntu 12.04 I created on the desktop  a simple file without extension, (with the name of the target machine),  with the following content:

[Desktop Entry]
Encoding=UTF-8
Type=Application
Name=[name of the target machine]
Name[en_US]=[name of the target machine]
Exec=/usr/bin/pcmanfm smb://[remote machine hostname]
Comment[en_US]=[name of the target machine]
Icon=/usr/share/icons/lubuntu/devices/48/drive-harddisk.svg

When double-clicked, it opens the remote share exactly like the filemanager (PCMan in this case) does  when the Samba link (smb://[remote machine hostname]) is written in its  addressbar. This way, double-clicking the shortcut from the desktop  opens the same location like the click on the bookmark for the remote  location saved in the filemanager, but you don't have to open the  filemanager first to access the bookmark.

Instead of [name of the target machine] you can write "remote computer" or "remote share" (without the ")

My source of inspiration for the syntax (besides the upper quote, of course) was the content of the shortcut file to Firefox (shortcut found on the desktop)

I really hope this could help someone. :)

---

