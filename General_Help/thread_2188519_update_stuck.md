---
title: "update stuck"
date: 2013-11-17
forum: General Help
---

### Post by mike555 on 2013-11-17
My updater is stuck and won't let me update because of this:

[IMG]http://i42.tinypic.com/160ea0g.jpg[/IMG]

 I tried fixing broken packages, but it didn't work, any ideas how to fix?

---

### Post by sanderj on 2013-11-18
I would open a terminal and run

```
sudo apt-get update
sudo apt-get upgrade
```

and then Google the error message.

---

### Post by fantab on 2013-11-18
Kill the update manager. Try what sanderj has adviced. If you still get errors:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by mike555 on 2013-11-18
Thanks but I'm still getting error code 1 in terminal

[IMG]http://i41.tinypic.com/senh41.jpg[/IMG]

---

### Post by fantab on 2013-11-18
I think your '/' partition is full. You need to create some space. If you have older kernels remove them.

Run:
```
sudo update-grub
```
This should tell you how many 'unused' kernels you have. Make note of the topmost/latest kernel version.

Run:
[/code]uname -r[/code]
This should tell you what kernel version you are using. If this is not latest then REBOOT. Check again and confirm that you are using latest kernel.

Run:
```
sudo dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get -y purge
```
This should remove all the 'unused' kernels.

Also check in the '/' directory to see if you have saved any data, and which you can remove.

Then run:
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by mike555 on 2013-11-18
I'm using 42% of space, so that is not problem .... and I'm using 3.2.0-56-generic

---

### Post by ian-weisser on 2013-11-18
What about that logfile in the error message? Does it exist?   If it exists, check it's permissions. Or try moving or renaming it, so the uninstall script will create a fresh logfile. If the logfile does not exist, try creating one for the script to write to.

---

