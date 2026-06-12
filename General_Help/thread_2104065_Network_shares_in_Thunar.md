---
title: "Network shares in Thunar"
date: 2013-01-11
forum: General Help
---

### Post by Stormlord on 2013-01-11
Hi,

On the image left it's Thunar and on the right it's Nautilus. I have placed an arrow on both file managers to show you that I can clearly see a mounted network share in Nautilus but it's nowhere to be seen in Thunar. "Expansion Drive" is an external USB hard disk which is visible in both managers. Does anyone know how I can make the network share visible in Thunar too please?

Thank you!  ;)

---

### Post by Toz on 2013-01-12
If I enter:
```
smb://server/share
```
...into the toolbar path, and authenticate when prompted, I get the link showing up under Network.

What version of *buntu and Thunar are you running?

---

### Post by Stormlord on 2013-01-12
> **Toz said:**
> If I enter:
```
smb://server/share
```
...into the toolbar path, and authenticate when prompted, I get the link showing up under Network.

What version of *buntu and Thunar are you running?

Xubuntu 12.04
Thunar 1.2.3

Thanks for the help.  I changed Thunar to toolbar view, I typed the path and it showed me the share contents on the right but nothing changed on the lists on the left.

---

### Post by Toz on 2013-01-12
I'm using a newer version of Thunar and Xfce and it works for me as indicated above. I fired up the Live CD of Xubuntu 12.04 and saw that the functionality doesn't exist there - so it must have be something new in Xfce 4.10 (and a later version of Thunar).

As a workaround, you can drag and drop the icon from the toolbar (to the left of the share path) to the left-pane bookmarks section. However, according to this bug ([https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/874618]("https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/874618")) the link won't survive a reboot. I'm not able to test this with the Live CD.

The other option is to use gigolo to bookmark and auto-connect to shares.

---

### Post by Morbius1 on 2013-01-12
Is it possible that we are talking about 2 different things?

One is a launcher that will seek out and mount the remote share.

The way I understand the original post though it's a link to the already mounted share. If I'm right open up Thunar to your home directory, make sure you have "show hidden files" enabled, and drag and drop your .gvfs folder to the left side panel. All of the remote shares are mounted in your .gvfs folder.

You can right click it > "Rename Shortcut " and change it to "Share Mounts" or something if you wish.

---

### Post by Toz on 2013-01-12
I understood this as having thunar display the share like nautilus (as per the OP's image from post #1). I'm using Thunar 1.6.2 and it displays like this:
[ATTACH]229948[/ATTACH]
The mounted share shows up automatically in the shortcuts (left) pane after I mount the share. I also have the option to unmount it straight from the shortcut as per other mounted devices.

I know this happened with a recent thunar update - just don't know which one.

---

### Post by Stormlord on 2013-01-12
Thank you all for your help.  I guess it's a Thunar 1.2.3 issue then.  Thunar 1.6 is fixed as I see.  :)

---

