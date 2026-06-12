---
title: "How can I start a program at boot time?"
date: 2007-02-17
forum: General Help
---

### Post by joann on 2007-02-17
Hello, all.

I was wondering if there is any way that I could start a program before I login? The program that I would like to start is called SVGATextMode. I use this program to enhance the appearance of the linux console.

Any help would be just great. :)
Joann

---

### Post by kerry_s on 2007-02-17
Yes, just put it in /etc/rc.local and it will start at boot. It will run as root, so if you need it to run as you, you need to use> sudo -u (you) command &
Here's what mine looks like, with the commands in using->

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

athcool on &
sudo -u user find /usr/lib/firefox ! -type d | xargs cat > /dev/null &
sudo -u user  find /home/user/.mozilla/firefox ! -type d | xargs cat > /dev/null &
hdparm -W1 -c3 -m16 /dev/hda &


exit 0

```

Mine says "user" because that is the name of my test account. :)

---

### Post by joann on 2007-02-18
I am still having a little bit of trouble getting the program to start correctly. I made a few changes to my /etc/rc.local file, and added /sbin/SVGATextMode. But when I boot it starts the rc.local file, but it does not start SVGATextMode. If it helps any here is a copy of my rc.local file.

#!/bin/sh 
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# To enable SVGATextMode with BIG FONT :)

sudo /sbin/SVGATextMode

exit 0

# End of rc.local

Oh... and here is the error

Invoking SVGATextMode... /sbin/SVGATextMode: ERROR: stdin is not a tty.

Any help on this subject would be greatly appreciated
Joann

---

### Post by kerry_s on 2007-02-18
Your entry in rc.local is wrong.  

sudo /sbin/SVGATextMode <- this is in complete

If it needs to run as root, just put->

/sbin/SVGATextMode &

If you need it running as a user->

sudo -u putnamehere /sbin/SVGATextMode &


You have to use sudo -u (user) to tell it what user to run the app under. You need the "&" on the end so when it's starting up it will just start it and continue, instead of waiting for it to finish.

---

