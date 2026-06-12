---
title: "Autoscript at Statup"
date: 2016-08-19
forum: General Help
---

### Post by rbscairns on 2016-08-19
I wish to run the following script automatically at the startup of Ubuntu 16.04
```
xrandr --newmode "1280x768_60.00"   79.50  1280 1344 1472 1664  768 771 781 798 -hsync +vsync
xrandr --addmode VGA1 1280x768_60.00
```

How do I do this?

---

### Post by speed... on 2016-08-19
Hi,

it should be possible with crontab. Try with:
crontab -e
Add following line to the cron
```
@reboot /path/to/script
```

---

### Post by SeijiSensei on 2016-08-19
The file /etc/rc.local is run last during boot.  Just add "/path/to/your/script" to that file above the "exit 0" line.

---

### Post by rbscairns on 2016-08-20
Thank you SeijiSensei. That I can do, however how do I put the code in a file that will execute in rc.local?

I can write the code in gedit.Do I just save it as a text file?

---

### Post by SeijiSensei on 2016-08-20
Yes, you can save it as a text file, then make the file executable with "chmod u+x /path/to/the/file".  I put all such scripts into /usr/local/sbin, a directory that is never touched by installations and upgrades.  The file should be owned by root:root; using "u+x" grants only the root user the right to run the script.

I recommend using the "nano" text editor from the terminal rather than gedit.  Open a terminal and enter "sudo nano /usr/local/sbin/script_name".  You'll see a handy menu of commands at the bottom of the screen.  You'll then need to use "sudo nano /etc/rc.local" to add the path to the script into that file.

However this is all overkill for just two lines of code.  I suggest just editing rc.local directly and adding the two xrandr commands there above the "exit 0" line.

---

### Post by sisco311 on 2016-08-20
xrandr is a tool which allows you to dynamically change screens. To make the changes persistent, you should create an xorg.conf file.

For more information, please check out the official documentation:
[https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

