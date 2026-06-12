---
title: "System broken by a snap"
date: 2018-01-31
forum: General Help
---

### Post by romzy on 2018-01-31
Hi, I'm on Kubuntu 17.04, I was installing spotify snap using : 
```
sudo snap install spotify
```
but my computer shutdowned, I hadn't mind enough the lack of battery warning..
Now, I can't access my session: it freezes each time I put my password in..
But it's like if spotify installation had left no sign, : sudo snap refresh&remove spotify do nothing

I tried then to reinstall spotify using the same code but it returns an error :
"cannot open <<spotify>> " followed by a link to get it

... begging for help

---

### Post by cruzer001 on 2018-01-31
Hello

I have a suspicion that its not snap or spotify hanging up your system, but the failure to update has hung it up.  17.04 has reached end of life and the software sources have been removed.  Meaning you cannot install anything or update your system.  So I would first suggest reading this:

[https://ubuntuforums.org/showthread.php?t=2382832](https://ubuntuforums.org/showthread.php?t=2382832)

And come back with any questions.

---

### Post by romzy on 2018-02-01
Hi, 

I've upgraded my system to 17.10 last night (succesfully) but the problem isn't fix at all, it freezes the same when I type my password..
Moreover when I open a terminal using Ctrl+Alt+F1, it prints :

[   36.354342] Could not find key with description :[17914f526a85fc1b]
[   36.354369] Could not find valid key in user sessions keyring for sig specified in mount option: [17914f526a85fc1b]
[   36.354406] Error parsing options: rc  = [-2]

---

### Post by cruzer001 on 2018-02-01
You say upgrading to 17.10 was successful, but you cannot get into your system or tty.  How have you verify this?

A power loss while installing a package will simply drop the package, not the desktop and not the tty.  You have other unknown problems going on.  I think your one step away from a reinstall.

What about recovery mode, will that let you in?  At boot in the grub menu.

---

### Post by romzy on 2018-02-01
Think I'm going for the restart...
How can I save my files ? (I don't have much, very new to ubuntu)

---

### Post by cruzer001 on 2018-02-01
You can use the ubuntu live dvd (usb) to mount the file system and recover your files.

Use the option to try ubuntu without installing, Then bring up the file manager and use it to mount your hdd/ssd and navigate to to your files.  More details here:

[https://askubuntu.com/questions/78691/recovering-user-files-with-a-live-cd](https://askubuntu.com/questions/78691/recovering-user-files-with-a-live-cd)

---

### Post by romzy on 2018-02-01
Thanks a lot !

---

