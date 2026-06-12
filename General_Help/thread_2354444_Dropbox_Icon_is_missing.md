---
title: "Dropbox Icon is missing"
date: 2017-03-02
forum: General Help
---

### Post by dunya on 2017-03-02
A total newbie just trying to make Xubuntu work. I have installed Dropbox from Ubuntu software center. At the beginning Dropbox worked as usual, started synching but in the next reboot the icon is gone, and though I am pretty new I do not know if it runs at the background and syncs or not. Tried to uninstall and reinstall but the problem persists. Does anyone has an advice for solving the problem?

---

### Post by howefield on 2017-03-02
Thread moved to the "*General Help*" forum.

Not sure what you downloaded from the Software Centre as I don't see dropbox as a package although there is a nautilus-dropbox package ? I'd generally download the deb package from the dropbox website and install that. 

Have you checked the preferences to see that drop is starting at boot ?

[ATTACH=CONFIG]273959[/ATTACH]

Failing that you could try installing the daemon again by deleting the following folders

```
~/home/.dropbox
```
and
```
~/home/.dropbox-dist
```

Launch the application and dropbox should download the daemon again and set itself back up.

---

### Post by dunya on 2017-03-03
I uninstalled, deleted the folders you mentioned, downloaded .deb file from the dropbox site and opened/installed it via Ubuntu Software Center. I was able to see Dropbox, but the problem is it is running at the background now but I can not open the dropbox graphic interface by clicking the icon and there is no dropbox icon seen in the tray. So practically the folders are synched, but I can't use it.

edit: I was able to make the icon work again by this command: 
dropbox stop && dbus-launch dropbox start

edit2: The command below needs in every new reboot, so it is not a permanent solution.

---

### Post by speartip on 2017-03-03
What you have experienced is a common problem on Xubuntu.
You may have already done this, but you need to add the command as a custom startup command, and also untick the original Dropbox entry in session & startup.
Then when Dropbox appears in your system tray, go to your Dropbox Preferences and untick "start Dropbox on system startup" otherwise you will have 2 instances running.
This saves you running the command everytime you login.

---

### Post by dunya on 2017-03-03
> **speartip said:**
> What you have experienced is a common problem on Xubuntu.
You may have already done this, but you need to add the command as a custom startup command, and also untick the original Dropbox entry in session & startup.
Then when Dropbox appears in your system tray, go to your Dropbox Preferences and untick "start Dropbox on system startup" otherwise you will have 2 instances running.
This saves you running the command everytime you login.

Do you mean that I should add "dropbox stop && dbus-launch dropbox start" command as a startup command? If yes, I did it and the other things you have written, yet all is the same. I have to reenter this command everytime upon new boot to make the icon work.

Edit: The command "dbus-launch dropbox start -i" as a startup command solved the problem and allowed Dropbox to start automatically with an icon on tray.

---

