---
title: "Right-click unmount as root"
date: 2007-05-22
forum: General Help
---

### Post by tma_it on 2007-05-22
On the Gnome desktop i get icons for each mountpoint mounted in /media. I have som network mounts defined in /etc/fstab which also appears on the desktop. I want to be able to unmount these by right-clicking and choosing "unmount" - i need to be root though to do that. Is there a way to do an "unmount as root" or something - can you integrate gksudo into the nautilus right-click menu?

/Thomas

---

### Post by AZzKikR on 2007-05-22
Yes you can. It is possible through nautilus scripts. I am not at my Ubuntu box at this moment, but a search through the forums on "nautilus scripts" will give you a few results to begin with. It's quite easy to make your own scripts that way! :)

---

### Post by AZzKikR on 2007-05-22
Oh, here's a good one: [http://g-scripts.sourceforge.net/index.php](http://g-scripts.sourceforge.net/index.php).

---

### Post by dannyboy79 on 2007-05-22
#!/bin/bash
#
for I in `echo $*`
do
  foo=`gksudo -u root -k -m "enter your password for root terminal
access" /bin/echo "got r00t?"`
sudo umount $I
 done
done
exit0

Just add the above to a file called whatever you like, make sure it's executable, and place it within the nautilus scripts. However, this won't work from the desktop right click menu because your not in nautilus whne you're doing that. I am not sure how to add scripts to your desktop right click menu.

---

### Post by tma_it on 2007-05-22
None of those scripts work when right-clicking icon for the mounted drive on the desktop. It works only on folders/files... You can right-click that icon and choose unmount, but not as root...

---

### Post by dannyboy79 on 2007-05-22
all those scripts he linked to are for nautilus just as mine is. I am not sure how to add a script to the right click menu for the desktop. You could always add a panel applet that can mount and unmount stuff. OR you can use the script that I have provided which will only work within Nautilus BUT it will ask you for root's password.

---

