---
title: "Troubleshooting Firefox in 16.04"
date: 2016-07-25
forum: General Help
---

### Post by mlnease on 2016-07-25
Hello,

After a recent reinstallation, I'm unable to open Firefox normally--I receive the error message, ```
Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system.
```
If I look at System Monitor, there is no instance of Firefox until I try to start it, then two appear immediately followed by the error message.

I've tried completely removing and reinstalling FF, running killall firefox and trying again; I've deleted .mozilla/.firefox, then uninstalled/reinstalled and probably tried a few other things that are now crowded out of my gourd.

This 'feels' to me like a profile problem, but if it is I don't understand how to fix it.

I *can* start Firefox with ```
sudo firefox
``` after which it works perfectly but recall reading that this is highly inadvisable so I'm troubleshooting it from Epihany instead.

Any suggestions would be greatly appreciated.

Thanks in advance.

---

### Post by &amp;KyT$0P# on 2016-07-25
Try switching from Ubuntu package manager build of Firefox to official Mozilla build.

1) Terminal, run
```
sudo apt-get purge firefox*
```
2) download the latest Firefox from [https://www.mozilla.org/firefox/all]("https://www.mozilla.org/firefox/all")
3) extract the tarball to your home directory (so you'd have the Firefox executable ~/firefox/firefox)

Before running Firefox again, try to set up to avoid any pre-existing corruption:
1) delete ~/.cache/mozilla/firefox
2) move/rename ~/.mozilla (you'll need it later to migrate your user data)
3) start Firefox profile manager:
```
~/firefox/firefox -profilemanager
```
Create a new profile, give it a unique name, **leave the default folder location!**, and select to Start Firefox.
4) Copy in your user data and settings [http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox](http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox)

---

### Post by mlnease on 2016-07-25
> **halogen2 said:**
> Try switching from Ubuntu package manager build of Firefox to official Mozilla build.

1) Terminal, run
```
sudo apt-get purge firefox*
```
2) download the latest Firefox from [https://www.mozilla.org/firefox/all](https://www.mozilla.org/firefox/all)
3) extract the tarball to your home directory (so you'd have the Firefox executable ~/firefox/firefox)

Before running Firefox again, try to set up to avoid any pre-existing corruption:
1) delete ~/.cache/mozilla/firefox
2) move/rename ~/.mozilla (you'll need it later to migrate your user data)
3) start Firefox profile manager:
```
~/firefox/firefox -profilemanager
```
Create a new profile, give it a unique name, **leave the default folder location!**, and select to Start Firefox.
4) Copy in your user data and settings [http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox](http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox)

Thanks a million for the speedy response.  I'll give it a try and get back to you.

---

### Post by mlnease on 2016-07-25
> **halogen2 said:**
> Try switching from Ubuntu package manager build of Firefox to official Mozilla build.

1) Terminal, run
```
sudo apt-get purge firefox*
```
2) download the latest Firefox from [https://www.mozilla.org/firefox/all](https://www.mozilla.org/firefox/all)
3) extract the tarball to your home directory (so you'd have the Firefox executable ~/firefox/firefox)

Before running Firefox again, try to set up to avoid any pre-existing corruption:
1) delete ~/.cache/mozilla/firefox
2) move/rename ~/.mozilla (you'll need it later to migrate your user data)
3) start Firefox profile manager:
```
~/firefox/firefox -profilemanager
```
Create a new profile, give it a unique name, **leave the default folder location!**, and select to Start Firefox.
4) Copy in your user data and settings [http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox](http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox)

OK--I've completed steps 1, 2, 3; and 1,2--but when I run ```
~/firefox/firefox -profilemanager
``` the Create Profile Wizard, the option Use Default Folder is grayed out. Any suggestions?  Thanks very much for your time and attention.

---

### Post by &amp;KyT$0P# on 2016-07-25
I'd think that shouldn't be a problem as long as you didn't manually specify a folder location.

---

### Post by mlnease on 2016-07-25
> **halogen2 said:**
> I'd think that shouldn't be a problem as long as you didn't manually specify a folder location.Success!  I had to create a link to ```
/home/mn/firefox/firefox
``` and copy it to my xfce4-panel, but it seems to be working fine.  Do I need to restore the renamed  ```
[COLOR=#000000][FONT=Ubuntubeta]*~/.mozilla*[/FONT][/COLOR]
``` to its original filename?

Thanks again for your time and attention!

---

### Post by &amp;KyT$0P# on 2016-07-25
You're welcome!  :KS

> **mlnease said:**
> Do I need to restore the renamed  ```
[COLOR=#000000]~/.mozilla[/COLOR]
``` to its original filename?
No, do not restore it, that risks the original problem recurring.
Selectively transfer important data and settings from your old ~/.mozilla to your new ~/.mozilla per [http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox](http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox)

---

### Post by mlnease on 2016-07-25
> **halogen2 said:**
> You're welcome!  :KS   No, do not restore it, that risks the original problem recurring. Selectively transfer important data and settings from your old ~/.mozilla to your new ~/.mozilla per [http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox](http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox)  Very good, again, can't thank you enough.

---

