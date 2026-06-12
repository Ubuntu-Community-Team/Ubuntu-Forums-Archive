---
title: "The right path for Flash Player"
date: 2008-05-16
forum: General Help
---

### Post by Alberto2 on 2008-05-16
Hello,
I have just installed **Kubuntu 8.04** (beautiful!) and **Firefox 3 Beta 5**, too. Then I tried to install **Adobe Flash Player**, downloading it and unpacking it on my home directory, typing:
**sudo ./install_flash_player_9_linux/flashplayer-installer**
The command ran all right, but at the end, I was requested to type the path where Firefox is (e.g. /usr/lib/mozilla).
So, I tried to find out where mozilla is by means of the command **locate** and found that it is in several places, and that just the path /usr/lib/mozilla given as an example is not the right one, as the procedure doesn't end successfully.
I'll be grateful to you, then, if you let me know what's the right path to type.
Best Regards

---

### Post by ibuclaw on 2008-05-16
You can install the most recent flash plugin from the repositories...
```
sudo apt-get install flashplugin-nonfree
```

But if you want to know where Firefox is installed:
```
dpkg -L firefox-3.0 | less
```
Press up and down arrow keys to scroll and "q" to quit the app.

It should tell you that it is in the "/usr/lib/firefox3.0b5" directory.

Regards
Iain

---

### Post by Alberto2 on 2008-05-17
> **tinivole said:**
> You can install the most recent flash plugin from the repositories...
```
sudo apt-get install flashplugin-nonfree
```

But if you want to know where Firefox is installed:
```
dpkg -L firefox-3.0 | less
```
Press up and down arrow keys to scroll and "q" to quit the app.

It should tell you that it is in the "/usr/lib/firefox3.0b5" directory.

Regards
Iain
Hello,
The command "sudo apt-get install flashplugin-nonfree" obtained this answer:
-Impossible to obtain the lock /var/lib/dpkg/lock-open and
-Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Any suggestion?
Best Regards

---

### Post by rbmorse on 2008-05-17
You have to close Synaptic or whatever package manager you're using before you can search the files that have been downloaded from repository.

The answer you want to your original quesion is:

/usr/lib/firefox3.0b5

That will make the Adobe installer happy and install the plugin as requested.

---

### Post by Alberto2 on 2008-05-17
Hello,
It seemed to me not to have any package manager open, however I started a new Kubuntu session in Console mode, typed the command sudo apt-get install flashplugin-nonfree and, at last, **I succeded in installing it**.
Thanks a lot to **tinivole** and **rbmorse**.

---

