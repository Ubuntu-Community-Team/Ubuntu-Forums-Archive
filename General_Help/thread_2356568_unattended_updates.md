---
title: "unattended updates"
date: 2017-03-24
forum: General Help
---

### Post by arnieb2 on 2017-03-24
When updating I get a message on the black screen as follows,"50 unattended updates ucf-dist in directory 'etc/apt/apt conf'd as it has an invalid file extension". Would someone explain this to me please?:confused:
I have 16.04 installed on a compaq laptop

---

### Post by fastbyte01 on 2017-03-24
Try to give ```
sudo mv /etc/apt/apt.conf.d/*.old  /root
``` and after ```
sudo apt -f install
```.

This can solve your problem and for security after that try to give the command:```
 sudo apt autoremove
```

---

### Post by deadflowr on 2017-03-24
Ignore it or remove the file, it's only a warning and does not affect the outcome of the updater.
The file is the result of a new config being installed and rather than overwriting the old config the system renamed/repurposed it using the ucf method.
read *man ucf* to see what that is all about.
Easy enough to just remove it with
```
sudo rm /etc/apt/apt.conf.d/50unattended-upgrades.ucf-dist
```
if you want to.
I mean, if you do not know what the file is, then there is no need to keep it.
Since you never did anything to warrant keeping it in the first place.

Also,
the first two commands shown it post #2 will do nothing to help you.
The mv command will not move that file.
And there was never anything wrong so the fix broken packages command(apt -f install) does not have any reason to run.
The last command can be helpful but that really depends on whether or not you have any obsolete packages installed.
(typical obsolete packages include older kernels)

---

### Post by arnieb2 on 2017-03-27
message received "cannot remove, no such file or directory2  ???

---

### Post by oldos2er on 2017-03-27
I suggest you reread deadflowr's post, particularly the last paragraph.

---

### Post by arnieb2 on 2017-03-28
Sorted, many thanks!

---

