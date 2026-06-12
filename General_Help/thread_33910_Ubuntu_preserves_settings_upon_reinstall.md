---
title: "Ubuntu preserves settings upon reinstall???"
date: 2005-05-12
forum: General Help
---

### Post by DutchLau on 2005-05-12
I recently reinstalled my Ubuntu base system after I had a kernel breakdown. (I tried to compile a kernel and I failed miserably, X wouldn't even start!) I have 4 partitions I think (15 GB for /root, 2 GB for swap, 15 GB free - unallocated space - and 128 GB for my /home) 

Today I reinstalled my system (I reformatted the 15 GB root partition and the 2 GB swap partition and left the other partitions as they were (I told Ubuntu to use the 128 GB partition for /home which had a few files on it). Amazingly, when I loaded into my Ubuntu system ALL my favorite settings (such as Firefox favorites, bookmarks, desktop background, window themes, cookies, and many more settings) were preserved!  :razz:  

How is this possible? Where are my settings saved? I don't want to complain, this is great! All my files are intact also! Is this normal? Ubuntu installs have never been so easy before. If anything happens or becomes unstable I just reinstall Ubuntu on one of the 15GB partitions and set the 128GB as /home, but will this happen every time?

Thanks Ubuntu!

DutchLau

---

### Post by tread on 2005-05-12
/home wouldn't be formatted unless you told the installer to do it. So when you created a new user (prolly with the same name) there was a home directory already there. 

This is one of the main reasons /home should be on a separate partition .. as you have here. You don't lose data if you ever reinstall.

Edited to add: my /home partition has survived Redhat to Mandrake to Ubuntu transitions .. hopefully there is no need ever to make another transition :)

---

### Post by Laemel on 2005-05-12
[QUOTE=DutchLau]I recently reinstalled my Ubuntu base system after I had a kernel breakdown. (I tried to compile a kernel and I failed miserably, X wouldn't even start!) I have 4 partitions I think (15 GB for /root, 2 GB for swap, 15 GB free - unallocated space - and 128 GB for my /home) 

Today I reinstalled my system (I reformatted the 15 GB root partition and the 2 GB swap partition and left the other partitions as they were (I told Ubuntu to use the 128 GB partition for /home which had a few files on it). Amazingly, when I loaded into my Ubuntu system ALL my favorite settings (such as Firefox favorites, bookmarks, desktop background, window themes, cookies, and many more settings) were preserved!  :razz:  

How is this possible? Where are my settings saved? I don't want to complain, this is great! All my files are intact also! Is this normal? Ubuntu installs have never been so easy before. If anything happens or becomes unstable I just reinstall Ubuntu on one of the 15GB partitions and set the 128GB as /home, but will this happen every time?

Thanks Ubuntu!

DutchLau[/QUOTE]
 There are two main places that settings are stored in GNU/Linux.  General system-wide settings are stored in /etc (X settings, stuff like that).  All your personal settings are usually stored in hidden files in your /home/username directory.  Since you didn't format your /home 128GB partition, your personal settings weren't erased.  Your /etc probably was, so stuff like custom X settings or startup scripts are gone now. 

 If you want to poke around your home directory in Nautilus, hit Ctrl-H and you'll see a bunch of folders and files that start with a period (like .mozilla-firefox or something).  Those are all the hidden files that hold your settings.

---

### Post by DutchLau on 2005-05-12
Pretty cool stuff. I've been using Linux for a bit now, but I never knew it was *so* useful with reinstalls  :grin: 

I just have a little problem, if anyone would like to help me. When I rebooted after installing my 686 kernel (I have to install the 686 kernel because I have more than 900 MB of Ram), it said something about the gnome-panel notifier being corrupt or something like that. I foolishly said that it could delete it and now my "system tray" doesn't work. What is the package to install to get this working again? *Please* It's a pain in the butt not to be able to see running programs (like GAIM) or the CD player in the tray there.

Can I apt-get the "gnome panel" notifier?

Thanks again,

DutchLau

---

### Post by Laemel on 2005-05-12
The notification area applet is included in the package "gnome-panel", so you should be able to reinstall that package.  You can find info about all the packages in the official repositories on the handy [http://packages.ubuntu.com](http://packages.ubuntu.com).

---

### Post by DutchLau on 2005-05-12
Alrighty then,

I'm reintalling the packages via Synaptic (yes I'm lazy) and I will inform about the progress. But was I right about thinking that the problem was in the Gnome-panel? 

Thanks,

DutchLau

EDIT: No, reinstalling the gnome-panel packages DID NOT fix the "system tray" problem. What is the file I have to apt-get in order to fix this problem? ( I pressed that it was OK to delete it when it was giving me a tough time, foolish me. I didn't write down the filename either, even more stoopid)

[[IMG]http://img63.echo.cx/img63/5985/nosystray4ib.th.jpg[/IMG]](http://img63.echo.cx/my.php?image=nosystray4ib.jpg)

As you can see in the screenshot, programs are not appearing in the system tray although I reinstalled the gnome-panel via synaptic. Regular items such as the CD player and GAIM just don't appear there and they close automatically (GAIM) when I press the "x" at the top of the window instead of minimizing to the systray.

*Please* help!

---

### Post by tread on 2005-05-12
Before you reinstalled the packages, did you try adding the notification area to the panel? Sometimes thats all that is needed .. after all, an applet is as likely to crash as any other application :)

---

### Post by DutchLau on 2005-05-12
[QUOTE=tread] [Add] the notification area to the panel. Sometimes thats all that is needed [/QUOTE]

There is just NO WAY that this problem was so simple, yet it is! I googled myself to the moon and back again, but after your post I simply pressed "Add to panel" and added the notification panel. Wow, you're a genius! (and you make me look like the über noob - which I am) 

Thanks a million,

DutchLau

P.S. now all of you have a beautiful picture of my Ubuntu desktop  :grin:

---

### Post by Laemel on 2005-05-12
[QUOTE=DutchLau]There is just NO WAY that this problem was so simple, yet it is! I pressed "Add to panel" and added the notification panel.[/QUOTE]


Heh.. I guess we were thinking too hard  :wink:

---

