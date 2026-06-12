---
title: "rsync flash drive before dismounting"
date: 2007-07-18
forum: General Help
---

### Post by srunni on 2007-07-18
Hi,

I'm trying to figure out how to make rsync automatically back up my flash drive to my hard drive when i dismount it (by clicking 'safely remove' in kde). Right now I have to do it manually, which is kind of annoying. Does anyone know how to do this?

Thanks in advance for the help!

---

### Post by machoo02 on 2007-07-18
Check out [this tutorial]("http://developer.kde.org/documentation/tutorials/dot/servicemenus.html") and [this one]("http://legroom.net/2007/04/20/adding-custom-actions-kde-context-menus") on adding custom items to context menus.  All it looks like you need to do is to write a script containing the rsync command and then the eject command for your flash drive, and then set up the .desktop entry.

---

### Post by srunni on 2007-07-20
Thanks, I'll check those out.

---

### Post by der_joachim on 2007-07-21
I made a very simple rsync script, which mounts an encrypted external HDD, makes an rsync backup and unmounts it again. Some time, I will add some extra options, (like searching for the correct device for my HDD. Bad me for hardcoding that device #-o). 

Anyhoo, here's the script. I hope it helps you along a bit.

```

#!/bin/bash
# @Param h) Show helpful message and quit
# @Param n) Chicken mode: do not do anyhting. Instead show what needs to be done.

# @TODO: find correct device 
# @TODO: command line parameter to suppress unmounting HDD
echo "--- Starting automatic backup script ---"
echo "--- Current date is `date` ---"

rsyncopt="-avz --delete"

# command line parameters
case $1 in
	     h) echo "h : print this help message" 
		 	echo "n : do nothing. Just show what would be done if you hadn't chickened out"
			exit
		;;
	     n)  
		 	echo "Invoking chicken mode. No actual synchronization will occur."
		 	rsyncopt="-avzn --delete"
		;;
esac
# Mount encrypted HDD. Notice that a password will be prompted
echo ""
echo "-- Trying to mount external HDD --"
truecrypt /dev/sdg2 /media/lin

if [ -d /media/lin/home ]; then
	echo ""
	echo "--- External HDD mounted ---"
	echo ""
	echo "--- syncing home directories ---"
    sudo rsync $rsyncopt /home /media/lin/
	echo ""
	echo "--- syncing etc ---"
	sudo rsync $rsyncopt /etc /media/lin

	echo "-- Done --"
	echo ""
	echo "-- Unmounting external HDD --"
	truecrypt -d
else 
	echo "--- No external HDD mounted. Exiting...---"
fi


```

---

### Post by srunni on 2007-07-21
Thanks for posting your script, it will no doubt help me when I'm trying to set up my script.

---

