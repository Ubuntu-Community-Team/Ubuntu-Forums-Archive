---
title: "Home Folder has Puked All Over the Desktop"
date: 2020-10-07
forum: General Help
---

### Post by greatoffender on 2020-10-07
I was running Linux Mint but a class I was taking used the Gnome desktop so I partitioned and loaded Ubuntu 20. It seems that the home folder has spilled all over the desktop and I cannot remove the folders without affecting the Home folder. In other words, if I delete a folder off of the desktop it deletes it from the Home folder and it will not let me merge the folders back into Home. It appears that my desktop is now Home? Can this be undone?

---

### Post by CelticWarrior on 2020-10-07
Are you by any chance using the same /home as your other OS?

---

### Post by TheFu on 2020-10-07
Gnome3 has all sorts of unexpected design choices for the uninitiated. The desktop behavior is one.  There are many others.  If I used Gnome3, I'd seek out a recent 30 minute youtube video with all the highlights and shortcuts presented just to get my bearings.

I do vaguely recall that some DEs really want us to have a ~/Desktop/ directory.  I remove all those extra empty directories for my personal sanity, so some of the DEs aren't happy.  If that directory doesn't exist, they show all the files in the HOME.  Be certain that ~/Desktop/ exists.

Sorry I don't have anything more useful to share.

---

### Post by HermanAB on 2020-10-08
The visible on screen desktop is just a folder on the disk and can be set to anything.  Usually, it is set to /home/username/Desktop, but if it happens to be /home/username then you will get what you are experiencing.

---

### Post by Morbius1 on 2020-10-08
I can reproduce this symptom:

Run the following command:
```
cat $HOME/.config/user-dirs.dirs | grep DESKTOP
```
The output should look like this:
> XDG_DESKTOP_DIR="$HOME/Desktop"
If it looks like this it will display the entire contents of your home folder on the desktop.  :
> XDG_DESKTOP_DIR="$HOME/"

I can restore the normal desktop by:

Put a # before XDG_DESKTOP_DIR="$HOME/" in the $HOME/.config/user-dirs.dirs file and run:
```
xdg-user-dirs-update
```
Then logoff and login again.

---

### Post by greatoffender on 2020-10-08
Morbius1 - would quote but this would make my post longer than necessary. - I gave up and reloaded Ubuntu from the beginning. The initial installation became more and more unstable with each reboot starting with my buddy initramfs and building from there. Laptop is a old (Toshiba Satellite S75) but 2.4Ghz w/ 16MBs RAM so I don't know what the issue was. Bios errors run by so quickly I lost track. Never liked the Gnome desktop but the class continues to use it for demos so I'm stuck.Net time I'll use Virtual Box instead of partitioning but ... lesson learned.

I do appreciate everyone's help! Thank you.

---

