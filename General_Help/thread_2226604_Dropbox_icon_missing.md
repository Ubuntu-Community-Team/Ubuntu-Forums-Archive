---
title: "Dropbox icon missing"
date: 2014-05-28
forum: General Help
---

### Post by sebastian16 on 2014-05-28
Hi,

i am using Ubuntu 12.04, and since earlier today, the Dropbox icon in the system tray is missing. I tried what seems to be the standard solution to this problem (install the libappindicator1 package), but after rebooting the icon did not come back. What I do get however, is a message that the Ubuntu One service is being shut down (reading some bug reports, I think there might be some kind of coincidence).

During the whole time, Dropbox is automatically started with the PC and working in the background, the only thing missing is the icon. How can I get it back?

Thanks in advance

---

### Post by dragonfly41 on 2014-05-28
If you see the greyed out icon for dropbox launcher in top toolbar 

click on this to select properties

and in the Launcher Properties window click on the dropbox icon and navigate to ..

/usr/share/icons/hicolor/48x48/apps/dropbox.png

If the launcher is not seen then you can drag Dropbox from Applications > Internet to top toolbar.

---

### Post by sebastian16 on 2014-05-28
> **dragonfly41 said:**
> If you see the greyed out icon for dropbox launcher in top toolbar 

click on this to select properties

and in the Launcher Properties window click on the dropbox icon and navigate to ..

/usr/share/icons/hicolor/48x48/apps/dropbox.png

If the launcher is not seen then you can drag Dropbox from Applications > Internet to top toolbar.

I did not see any grayed out icon.

If I drag Dropbox from applications to the toolbar, then a Starter icon for Dropbox is added. What I want and what I am missing is the icon shown for example here: [http://itsfoss.com/solve-dropbox-icon-ubuntu-1310/](http://itsfoss.com/solve-dropbox-icon-ubuntu-1310/), which also allows to access the Dropbox options like pause the synchro and so on

How it looks right now: [IMG]http://abload.de/img/2cfjdh.png[/IMG]

How it looked yesterday and is supposed to: [IMG]http://abload.de/img/1xgj40.png[/IMG]

---

### Post by dragonfly41 on 2014-05-28
Try an "advanced search" in this forum looking for just "dropbox" in titles (not posts)
and you will see others with same problem.

It seems that uninstall dropbox followed by reinstall has worked for some users.

I have dropbox next to connections in top bar ... and other dropbox launchers as well with full blue icon.

---

### Post by sebastian16 on 2014-05-28
Which is the best way to do that? I do not exactly remember how I installed Dropbox, but the Software Center does not seem to recognize that I have Dropbox installed at all. 

Btw: I still get notifications, for example when someone edits documents in a shared folder. Just the Dropbox icon has disappeared and refuses to come back

---

### Post by dragonfly41 on 2014-05-28
That's odd .. my Ubuntu 12.04 Software Centre shows dropbox ..

However .. [https://www.dropbox.com/help/41/en](https://www.dropbox.com/help/41/en)

Incidentally I would suggest trying Spideroak instead of Dropbox.

[https://spideroak.com/](https://spideroak.com/)

---

### Post by waitem on 2014-06-01
I was having the same problem. 
I fixed this by using **dconf-editor** to add an entry for Dropbox into the "whitelist" for the Unity panel as follows:

$ **sudo apt-get install dconf-tools**
$ **dconf-editor**

**desktop** -> **unity** -> **panel**

Add an entry **[FONT=courier new]'Dropbox'[/FONT]** into the **systray-whitelist** value field (before the closing bracket, and preceded by a comma).

( Mine looks like:    [FONT=courier new]['JavaEmbeddedFrame', 'Wine', 'Update-notifier', 'Truecrypt', 'Dropbox']  )[/FONT]

Log out and in again and you should have your icon back.

Tested using Ubuntu 12.04 LTS and Dropbox client v2.8.2

---

### Post by dmtparker on 2014-06-06
[QUOTE=waitem;13039186]I was having the same problem. 
I fixed this by using **dconf-editor** to add an entry for Dropbox into the "whitelist" for the Unity panel as follows:

$ **sudo apt-get install dconf-tools**
$ **dconf-editor**

**desktop** -> **unity** -> **panel**

Add an entry **[FONT=courier new]'Dropbox'[/FONT]** into the **systray-whitelist** value field (before the closing bracket, and preceded by a comma).

I, too, am having the same problem (Ubuntu Studio 13.10). In addtion, every time I boot the computer, I get the messaage that Dropbox needs Super User permission and I have to enter the password. Still no icon. I tried the dconf-editor, but get a totally different set of options (desktop->[gnome, gstreamer, ibus] The only item with 'panel' is ibus, but it does not have the systray-whitelist. Can't find that anywhere. 
Note, Studio uses Xfce instead of Unity so I assume that is the reason for the differences. Any suggestions on what to do?

---

### Post by fungie55 on 2014-06-08
Having the same issue with the Dropbox system tray icon in Ubuntu 12.04. After getting a permissions message on starting the machine a few weeks ago, the tray icon now only rarely appears when I boot up my machine, but Dropbox itself is still running. However, the icon appears when I open the command line and stop and restart Dropbox.

---

### Post by fungie55 on 2014-06-08
> **sebastian16 said:**
> Which is the best way to do that? I do not exactly remember how I installed Dropbox, but the Software Center does not seem to recognize that I have Dropbox installed at all. 

Btw: I still get notifications, for example when someone edits documents in a shared folder. Just the Dropbox icon has disappeared and refuses to come back

If the Dropbox installer in the Software Center is not marked as installed, it means you used the .deb installer file from the Dropbox website instead of the Dropbox installer already provided within the Software Center. I did the same thing.  

Open the Software Center and click on the drop down arrow next to the **All Software** button. You'll see **Dropbox Ubuntu Repository** in the list.

---

### Post by Atitudes on 2014-06-09
> **waitem said:**
> I was having the same problem. 
I fixed this by using **dconf-editor** to add an entry for Dropbox into the "whitelist" for the Unity panel as follows:

$ **sudo apt-get install dconf-tools**
$ **dconf-editor**

**desktop** -> **unity** -> **panel**

Add an entry **[FONT=courier new]'Dropbox'[/FONT]** into the **systray-whitelist** value field (before the closing bracket, and preceded by a comma).

( Mine looks like:    [FONT=courier new]['JavaEmbeddedFrame', 'Wine', 'Update-notifier', 'Truecrypt', 'Dropbox']  )[/FONT]

Log out and in again and you should have your icon back.

Tested using Ubuntu 12.04 LTS and Dropbox client v2.8.2

Thanks a lot waitem, this solved the issue straight away.

I do have a question related to the installation. When trying to solve the issue my previous steps were to remove Dropbox and re-install it. I tried the 'nautilus-dropbox' install and got the following message: 
> [I]
The following packages have unmet dependencies: nautilus-dropbox : Depends: dropbox but it is not going to be installed 
E: Unable to correct problems, you have held broken packages.[/I]
And when trying via software center:
> [I]The following packages have unmet dependencies:

nautilus-dropbox: [/I]

The only working installation is simply installing via **sudo apt-get install dropbox **which works pretty fine. What annoys me is the drop-down menu, it is in grey colour instead of the usual black from the other integrated menus. Therefore, I assume Dropbox is running under Wine, is there any other way? Can I fix my "integrated" installation removing the correct packages and doing a fresh install? (my apologies, I know this is a bit off topic but it would be nice not to open another thread I guess:confused:)

Thanks a lot for the help.

Cheers!

---

### Post by n.hinton on 2014-07-26
In a terminal:

```
sudo apt-get install python-pkg-resources python-setuptools --reinstall
```
```
sudo easy_install --upgrade requests
```

---

