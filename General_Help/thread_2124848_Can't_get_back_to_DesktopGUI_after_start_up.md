---
title: "Can't get back to Desktop/GUI after start up"
date: 2013-03-12
forum: General Help
---

### Post by Jouten on 2013-03-12
Hi, I have a problem when starting up Ubuntu 12.04. It only shows the terminal and I can log in but I can't go to the GUI. I tried ctrl+alt+f7 but it stops at "checking battery state",  restarting doesn't help either. The problem came when my laptop shut down while the battery went empty

---

### Post by cortman on 2013-03-12
After you login, run

```
startx
```

If that gets you to your normal GUI, you may just need to fix/reinstall LightDM, the display manager. If it throws errors and doesn't start, please post the content of the errors.
Good luck!

---

### Post by Jouten on 2013-03-12
When I use startx it stops at "Checking battery state...", too

---

### Post by cortman on 2013-03-12
Could be that your graphics driver is messed up. Please post output of these commands-

```
cat /etc/xorg.conf
lspci | grep -i vga
lshw -C video
```

Thanks.
This [thread]("http://ubuntuforums.org/showthread.php?t=1859820") has a lot of different solutions as well.

---

### Post by rnerwein on 2013-03-12
hi
i ain't know why my system is checking the battery state too ? i got no battery - without that on the moterboard - i am using a desktop. would be nice to see where the message comes from. this is not the first thread about this problem. fact is i can't find this message in logfiles (or i didn't now where to search - but not in /var/log). i'll look at the /etc/acpi/power.sh that's
the last message i can see. will be back in some time.
ciao

---

