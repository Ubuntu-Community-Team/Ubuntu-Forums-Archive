---
title: "Geary: Add another account"
date: 2016-11-08
forum: General Help
---

### Post by ray42 on 2016-11-08
How do I add an extra account in Geary?

See the pic of the top bar I can't see any settings menu.

[https://dl.dropboxusercontent.com/u/66493937/Screenshot%20from%202016-11-08%2020-40-14.png](https://dl.dropboxusercontent.com/u/66493937/Screenshot%20from%202016-11-08%2020-40-14.png)

---

### Post by howefield on 2016-11-09
In Unity the menu is in the top panel but not sure about Gnome, however you could try the Ctrl + M keys to bring up the accounts dialogue.

---

### Post by ray42 on 2016-11-09
Excellent! Yes Ctrl+M works. I don't know why there is no menu. How do I navigate. I did a Google search for shortcut keys but this didn't return results.

Any other shortcut keys you know about?

Please be careful you might just become indispensable ;)

---

### Post by howefield on 2016-11-10
> **ray42 said:**
> Any other shortcut keys you know about?

Preferences is Ctrl + E
Help is F1

Also, not sure if these are current but you could try them..

Compose a new message : Ctrl+N or N
Reply to sender : Ctrl+R or R
Reply to all : Ctrl+Shift+R or Shift+R
Forward : Ctrl+L or F
Archive : A
Trash : Delete or Backspace
Delete : Shift+Delete or Shift+Backspace
Star : S
Unstar : D
Mark read : Ctrl+I or Shift+I
Mark unread : Ctrl+U or Shift+U
Toggle spam :Ctrl+J or !
Quit : Ctrl+Q
Zoom in : Ctrl+= or =
Zoom out : Ctrl+- or -
Reset zoom : Ctrl+0 or 0
Close composer window : Ctrl+W
Jump to search box : Ctrl+S
Find in current conversation : Ctrl+F
Find next in current conversation : Ctrl+G
Find previous in current conversation : Ctrl+Shift+G

---

### Post by ray42 on 2016-11-10
Oh dear, Geary now crashes after using a few of these shortcuts!

How do reset and clean, as unistall doesn't remove the accounts added originally

I searched for files left over files here is a screenshot:

[https://dl.dropboxusercontent.com/u/66493937/Screenshot%20from%202016-11-11%2010-18-04.png](https://dl.dropboxusercontent.com/u/66493937/Screenshot%20from%202016-11-11%2010-18-04.png)

---

### Post by CantankRus on 2016-11-11
To start afresh, delete the folder @ **~/.local/share/geary** (ctrl+h to show hidden files in the file browser)
You may want to delete any saved passwords as well.
Open Passwords and Keys, select the login keyring and type geary in the search box.
Right clicking on an entry gives you a delete option.

You may want to also reset geary preferences via terminal...
```
dconf reset -f /org/yorba/geary/
```

User configs are always created in your home directory.
Uninstalling an application doesn't affect user configs.

---

### Post by ray42 on 2016-11-11
Thanks,yes that did work BUT! The same error happens again, an internal error see pic.

[https://dl.dropboxusercontent.com/u/66493937/Screenshot%20from%202016-11-11%2022-09-23.png](https://dl.dropboxusercontent.com/u/66493937/Screenshot%20from%202016-11-11%2022-09-23.png)

Maybe I have bigger problems

---

### Post by CantankRus on 2016-11-12
Don't normally use geary, but testing in Ubuntu and Ubuntu-Gnome do not get errors.
Run a system update and check for errors...
```
sudo apt update
sudo apt upgrade
```

Reboot and test geary.

You can also try the latest ppa version...
```
sudo add-apt-repository ppa:geary-team/releases
sudo apt update
sudo apt upgrade  
```
Test geary.
In Gnome you can access geary preferences from the geary panel icon at the top left. 

If you want to go back to previous geary version...
```
sudo apt install ppa-purge
sudo ppa-purge ppa:geary-team/releases
```

---

### Post by ray42 on 2016-11-12
All checks out fine.

I can't access menu as there isn't one. See my original post.

It did work originally. I have only been using Geary for about a week. Shouldn't I try to fix the internal error. Isn't this indicative of something bigger?

---

### Post by CantankRus on 2016-11-12
Appears to be a system fault.
Have you added ppas?
What's your output from...
```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*.list
```


You could also create a new user account(system settings > user accounts),  and test geary in that account.

> **ray42 said:**
> All checks out fine.

I can't access menu as there isn't one. See my original post.


In Gnome, the preferences menu should be available after you have added an email account.

---

### Post by ray42 on 2016-11-12
```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*.list/etc/apt/sources.list:deb http://gb.archive.ubuntu.com/ubuntu/ xenial main restricted
/etc/apt/sources.list:deb http://gb.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
/etc/apt/sources.list:deb http://gb.archive.ubuntu.com/ubuntu/ xenial universe
/etc/apt/sources.list:deb http://gb.archive.ubuntu.com/ubuntu/ xenial-updates universe
/etc/apt/sources.list:deb http://gb.archive.ubuntu.com/ubuntu/ xenial multiverse
/etc/apt/sources.list:deb http://gb.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
/etc/apt/sources.list:deb http://gb.archive.ubuntu.com/ubuntu/ xenial-security main restricted
/etc/apt/sources.list:deb http://gb.archive.ubuntu.com/ubuntu/ xenial-security universe
/etc/apt/sources.list:deb http://gb.archive.ubuntu.com/ubuntu/ xenial-security multiverse
/etc/apt/sources.list:deb http://gb.archive.ubuntu.com/ubuntu/ xenial-backports multiverse restricted universe main
/etc/apt/sources.list.d/opera-stable.list:deb https://deb.opera.com/opera-stable/ stable non-free #Opera Browser (final releases)

```

I did use a PPA I think it was the Grub Customiser. I found that this could be a problem from: 

[https://sites.google.com/site/easylinuxtipsproject/fatalmistakes](https://sites.google.com/site/easylinuxtipsproject/fatalmistakes)
**[SIZE=2]6.0 Never use installation scripts or third-party tools like Ultamatix, Ubuntu Tweak, Ubuntu Sources List Generator, Grub Customizer and Ubuntuzilla[/SIZE]**

But I removed it and did a clean.

Also  the preferences menu doesn't appear, and the Geary isn't shown in the top bar when running. Hmmm!

---

### Post by CantankRus on 2016-11-12
No looks ok.
You may mess up your boot with Grub Customiser...that's about all.
May be just a geary error that happens with certain emails or a database error over time.
I don't really know.

Just odd you don't get the preferences menu unless you have added a Gnome extension that removes it.
Testing geary in a new user account could indicate if it's a user config error or application error.

---

### Post by ray42 on 2016-11-12
> **CantankRus said:**
> Just odd you don't get the preferences menu unless you have added a Gnome extension that removes it.

No I checked

---

### Post by mj0g on 2016-11-14
> **ray42 said:**
> How do I add an extra account in Geary?

See the pic of the top bar I can't see any settings menu.

[https://dl.dropboxusercontent.com/u/66493937/Screenshot%20from%202016-11-08%2020-40-14.png](https://dl.dropboxusercontent.com/u/66493937/Screenshot%20from%202016-11-08%2020-40-14.png)

From that screenshot it looks like you may be running the XFCE desktop instead of GNOME? If so, then it's a problem with XFCE's default settings fot GTK+ applications. This post on the mailing list may help: [https://mail.gnome.org/archives/geary-list/2016-September/msg00042.html](https://mail.gnome.org/archives/geary-list/2016-September/msg00042.html)

---

### Post by ray42 on 2016-11-14
> **mj0g said:**
> From that screenshot it looks like you may be running the XFCE desktop instead of GNOME? If so, then it's a problem with XFCE's default settings fot GTK+ applications. This post on the mailing list may help: [https://mail.gnome.org/archives/geary-list/2016-September/msg00042.html](https://mail.gnome.org/archives/geary-list/2016-September/msg00042.html)

Thanks, but no... definitely Ubuntu Gnome 3

---

### Post by mj0g on 2016-11-14
> **ray42 said:**
> Thanks, but no... definitely Ubuntu Gnome 3

Oh okay. Well then the shell should display a menu labelled "Geary" up on the top bar next to Activities, and clicking on that should reveal the standard app menu items, including Accounts, where you can add a new account.

If you have configured gnome-shell to not display the app menu, then GTK should display the app menu for you in the Geary header bar. However, that requires the setting org.gnome.desktop.wm.preferences button-layout to include the string "menu" somewhere. E.g. for me the value is "menu:close".

Does any of that help?

---

### Post by ray42 on 2016-11-16
> **mj0g said:**
> Oh okay. Well then the shell should display a menu labelled "Geary" up on the top bar next to Activities, and clicking on that should reveal the standard app menu items, including Accounts, where you can add a new account.

If you have configured gnome-shell to not display the app menu, then GTK should display the app menu for you in the Geary header bar. However, that requires the setting org.gnome.desktop.wm.preferences button-layout to include the string "menu" somewhere. E.g. for me the value is "menu:close".

Does any of that help?

Unfortunately no. I think I have bigger probs. I'm going for a fresh install.

> Thank for everyone's input. It is appreciated. It takes time and effort. It is not always what is required, if this is so then at least you were generous enough to contribute. A thank you all I can do at present. One day I may be able to contribute myself.


"Go in peace and not in pieces"

---

