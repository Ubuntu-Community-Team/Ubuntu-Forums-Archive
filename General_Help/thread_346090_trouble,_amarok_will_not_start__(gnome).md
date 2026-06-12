---
title: "trouble, amarok will not start  (gnome)"
date: 2007-01-25
forum: General Help
---

### Post by caterin6 on 2007-01-25
Had very good luck with amarok up until recently.  After a system re-install for unrelated housekeeping purposes I have not been able to get amarok to start.  The splash screen appears and then... nothing.  I am able to run it as root form the terminal (sudo amarok) but I believe that I have some serious problems. I have checked that there are no missing or out of date packages, removed, reinstalled (both amarok and OS), and yet I got nowhere

  this is the output i get when i attempt to start amarok from the terminal

```
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running..
```.
  
I also ran strace but that only served to highlight how damn little I know about linux

Any ideas / additional helpful info? thanks in advance

---

### Post by gwpritch on 2007-01-25
The problem with running an X app with sudo is that it hijacks the config. files in your home directory so that they can only be accessed as root. This is why you should use gksudo rather than sudo when executing xapps as root.
I am not directly familiar with amarok but look at your hidden files in you home directory for something like .amarok 
Then in a terminal:

```
sudo rm -r ./.amarok
```

Then try starting amarok again as user.

---

### Post by caterin6 on 2007-01-26
thanks for the insight, I deleted the config files and sure enough amarok started up.  you learn something everyday

thanks again

---

### Post by russell.h on 2007-01-28
Where were the config files? I'm having the same problem, but can't seem to find any config files.

---

### Post by klilja on 2007-01-28
I just installed amarok, and am having the same problem, and I also can't find any config files.

---

### Post by rainwalker on 2007-01-28
The config files are probably hidden; you have to go to View -> Show Hidden Files to see them

---

### Post by russell.h on 2007-01-28
Yeah, I did that and there was still nothing in my home directory. I reverted to 1.4.3 and now it works fine (and I just looked and I still dont see any config files).

---

### Post by gwpritch on 2007-01-29
The config file will probably not show up until you have run the app at least once and set your preferences.

---

### Post by scifi76 on 2007-02-14
For those who might need to know the config files you should delete if you are having similar problems to the original poster are:

```

sudo rm ./kde/share/config/amarokrc
sudo rm -r ./kde/share/apps/amarok

```

worked for me anyway

---

### Post by russell.h on 2007-02-15
Thanks! I had forgotten all about it, but I still needed that.

---

