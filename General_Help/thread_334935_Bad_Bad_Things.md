---
title: "Bad Bad Things"
date: 2007-01-09
forum: General Help
---

### Post by penguinchrissy on 2007-01-09
I restarted my computer eariler today because I was having trouble with gftp and was wondering if it was connection issues. I was trying to move files off my xbox and onto my harddrive. After I restarted everytime I logged in my computer would reboot on its own I tried a couple of restarts and nothing different finally I got a message about my harddrive being full and it being unable to write to the log file. This could be the case and the reason for my ftp problems. So I need a way to access and delete files off my linux partations either through rescue mode or windows. I don't know enough of the command line to do it through rescue mode on my own so if you know how to do it that way code would be of great help but any ideas would help I really need to get this up for school.

---

### Post by taurus on 2007-01-09
Boot into recovery mode from GRUB menu and at the prompt, do

```
apt-get clean
rm ~/.Trash
```
What would buy you some space.

```
df -h  <-- check on space
shutdown -r now  <-- reboot your machine
```

---

### Post by majoridiot on 2007-01-09
or boot with the livecd and poke around and delete with nautilus in a gui environment if you like

---

### Post by penguinchrissy on 2007-01-09
Thanks for both of those I got ext2IFS to work I had it installed before but it kept on saying i needed to format the drive. I figured out that I need to restart linux properly for it to work which I didn't because I was getting impatient. So if you use ext2IFS shutdown properly

---

