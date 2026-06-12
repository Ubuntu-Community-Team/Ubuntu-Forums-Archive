---
title: "Blank Beige Screen after login"
date: 2008-05-16
forum: General Help
---

### Post by vmantva on 2008-05-16
Hopefully this is the right section for this:

The other day I logged into my computer. All seemed normal in the beginning. I logged in without a problem. After login though, the screen stayed beige, the top menu bar never appeared, my folders and files did not load. Curious I waited to no avail. Then I remembered the Ctrl+Alt+L/R hotkey to switch desktops. I used this and it worked correctly. That is, in the middle of the screen they light bar showed that I had changed desktops. However it was still beige without any hope of change.

Reading another post(i have a windows partition and was able to switch over),ubuntuforums.org/showthread.php?t=730427
I decided to try and log into fail safe gnome. I did this and this time the heron graphic appeared in the backround but nothing more. I wasn't paying attention before but I do believe there were a lot of updates to install but I can't say for sure after what session in particular it stopped working as I work on the windows partition a lot as well. I had also recently been trying to download Amule and so messing around with GTK dependencies and other minor packages but nothing that I would consider major.

Anyone have any ideas. Im running Ubuntu 8.04 on the latest kernel.

Thanks,

keywords: login blank screen hardy heron Ubuntu 8

---

### Post by vmantva on 2008-05-17
Bump,
Also, The heron comes up regardless of whether i login using failsafe Gnome or normal startup. This is kind of a rough problem I was hoping someone could help....

---

### Post by AlbertTatlocksCap on 2008-05-19
Ok - I posted this possible solutin in another thread but heer it is again



Ok - I had the same problem after a fresh install install of 8.04 onto a scsi disk (apparently it seems to affect scsi and USB devices)

I used this to get around it for now

CTRL+ALT+F1 (or CTRL+ALT+F2 if that doesn't work)

Login in text mode

sudo rm /tmp/.X0-lock

startx

It should then start up OK

Then set Automatic login by:

System>Administration>Login Window>Security and then check Automatic Login

Ok - this means that you can only login with one username and it will be automatic so no login window for password - but it works and I suspect/hope there will be a fix in the near future

Hope it helps

---

