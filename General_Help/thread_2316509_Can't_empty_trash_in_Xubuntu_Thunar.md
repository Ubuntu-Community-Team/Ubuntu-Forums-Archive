---
title: "Can't empty trash in Xubuntu Thunar"
date: 2016-03-08
forum: General Help
---

### Post by Ralph L on 2016-03-08
I am running Xubuntu 14.04LTS.  For some reason I can't find the Trash folder in order to empty it using Thunar.  Anybody know how to do that???

---

### Post by Dennis N on 2016-03-08
Yes, look for the trash icon in Places section of the Thunar side pane. Right click on it and select "Empty Trash".

---

### Post by Ralph L on 2016-03-08
I don't find anything labeled Trash under Places.

---

### Post by yancek on 2016-03-08
I don't use Xubuntu but, many Linux systems have the Trash directory in the user /home directory as a hidden file.  Open Thunar and click on the View tab and then show hidden files and look for .local and see if you have a Trash directory there.  Might be in a sub-directory as it varies with different systems.

---

### Post by Ralph L on 2016-03-08
You are correct.  The Trash folder is there.  This seems to be a very awkward place to go to empty trash.  I think it used to appear in a more usable position before.  Anybody know how to to fix Thunar so it is easier to empty trash??

---

### Post by ajgreeny on 2016-03-08
It's called Rubbish Bin in thunar.

If it is still not showing have a look in ~/.local/share/Trash where there are three subfolders and one file in my version.  The files themselves are in the /files subfolder.

It should also show in the **Go** menu item as Rubbish Bin.

---

### Post by Ralph L on 2016-03-08
Thanks for the response!!  No Rubbish Bin under the Go menu in Thunar.  Do you know how to install it???

---

### Post by Dennis N on 2016-03-08
You can also have the Trash icon on the Desktop. If you don't see it there, check the Desktop Settings > Icons > Default Icons, and mark the check box for Trash (or Rubbish Bin, if that's the term you have) to be shown. You perhaps can add the icon to side pane by going to the Trash folder in ~/.local/share, right-click and choose "send to side pane". Once its there, maybe that will give you an "empty trash" option as well in it's right-click menu.

---

### Post by Ralph L on 2016-03-08
Thanks again for the reply.  I can do as you suggested and put my own shortcut in the Go Menu, but it doesn't have the special box for "Empty Trash".  I do have a Trash icon on my desktop and that works correctly, but I usually have windows all over my desktop, so I prefer having a Trash icon in Thunar.  I brought up Nemo (another file manager) and it has the Trash folder fine.  So somehow I must have screwed up Thunar.  Maybe I'll discover what I did some time, or maybe I will install the new Xubuntu LTS system coming out soon.

Again, thanks to everybody who replied.  If anybody comes across anything that tells how to repair Thunar please post it here.

---

### Post by Dennis N on 2016-03-08
You can also empty the trash with a command: **trash-empty**

If you want to get creative, add a launcher in the menu that runs the command.

---

### Post by ajgreeny on 2016-03-09
Just to try to round the circle properly, do you have any other file-managers installed?  It is possible that if you have nautilus installed it might have taken over management of your desktop, which is why you have to start nautilus in xubuntu with command **nautilus --no-desktop** or set nautilus not to manage the desktop in dconf.

See [http://askubuntu.com/questions/237953/how-to-open-nautilus-without-a-desktop](http://askubuntu.com/questions/237953/how-to-open-nautilus-without-a-desktop) for more detail.

I do not know if this might have some effect as far as your problem is concerned of losing Trash, but wondered if it might be the cause.

---

### Post by Ralph L on 2016-03-13
Somehow "Trash" came back to the Thunar "GO" menu.  I did do a launching of nautilus --no-desktop, so that may or may not have been the problem.  Anyway things are fine again.

Thanks again,

---

