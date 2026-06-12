---
title: "Flash Pluging install"
date: 2008-02-04
forum: General Help
---

### Post by waldrepdebater on 2008-02-04
Ok, I'm trying to install the firefox flash plugin.  I went to a site the required flash and used the "install missing plugins" feature to install flash.  I restarted firefox, nothing happened.  I used synaptic to remove the plugin and repeated the process.  Nothing happened.  I then went to the adobe site and tried to install the .tar file.  When I enter the commands in the terminal:

```
~/Desktop/install_flash_player_9_linux$
./flashplayer-installer
```

I get the following error message after each one:

```
bash: ./flashplayer-installer: No such file or directory

```

Any idea how to get flash installed?

---

### Post by Seisen on 2008-02-04
Did you happen to untar the file first?

---

### Post by waldrepdebater on 2008-02-04
I'm fairly new to this so I'm not exactly sure what you mean.  I downloaded the file and extracted it to the desktop with the archives manager.  Do I need to do something else too?

---

### Post by zvacet on 2008-02-04
In synaptic find** flashplugin-nonfree** and install it.

---

### Post by waldrepdebater on 2008-02-04
Tried that twice, firefox still won't play flash.

---

### Post by zvacet on 2008-02-04
```
sudo apt-get install ubuntu-restricted-extras
```

this will give you flash,java,plugins...

---

### Post by waldrepdebater on 2008-02-04
Ok, I tried that, same error.

---

### Post by seventhc on 2008-02-04
I think you are switching to it wrong, if you are certain that it is on your desktop then do this:
```

cd Desktop/install_flash_player_9_linux
./flashplayer-installer

```

---

### Post by zvacet on 2008-02-04
@ **waldrepdebater**

Do you have all repos open?Chek in system>admin>software sources>chek all boxes under Ubuntu software and under updates tab.Reload.Now you try 

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by FuturePilot on 2008-02-04
The flashplugin-nonfree is broken right now.
See this thread
[http://ubuntuforums.org/showthread.php?t=636397]("http://ubuntuforums.org/showthread.php?t=636397")

---

