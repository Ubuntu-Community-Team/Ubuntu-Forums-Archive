---
title: "Ubuntu mini remix"
date: 2013-03-19
forum: General Help
---

### Post by Ranvens on 2013-03-19
Hi all, 


I've taken to using UMR for some admin tasks at work. ive figured out how to use UCK to customise it and get my scripts in it that I need.


i want to retain the headless environment (dont need a gui) and have customised as such.


The problem im having is with the following script.
```


#!/bin/sh
clear
set +v
listdisk=`fdisk -l /dev/sda |grep /dev/ |grep -v Disk |cut -d " " -f1`
for i in $listdisk; do
	echo "working on partition: " $i
	val=`echo $i |grep sda |cut -d "/" -f3`
	mount /dev/$val /media/$val


	if [ ! -f /media/$val/boot.ini ];
	then
		echo "file not found"
	else
		echo "file found"
		rm /media/$val/boot.ini
		cp /media/$val/Temp/boot.ini.pe /media/$val/boot.ini
		break
	fi


wait
done

```
I need this script to run automatically, but I also need feedback from it to let me know it has functioned correctly. Ive tried to use cron, init.d, /etc/profile, /etc/profile.d/ and a few other things. There are two main problems, either I get no feedback, or it doesnt appear to be authenticated and can't mount. When I run the script manually it works perfectly.


Basically what I need is this. once my custom UMR build logs in (which it does automatically as user ubuntu) and at the $ prompt, I need the script to execute, and display the "echo" sections. 


Any thoughts?

---

### Post by Ranvens on 2013-03-19
[[IMG]http://farm9.staticflickr.com/8511/8573324408_eef10eb889_b.jpg[/IMG]]("http://www.flickr.com/photos/ranvens/8573324408/")
[Script Error]("http://www.flickr.com/photos/ranvens/8573324408/") by [Travis Lord]("http://www.flickr.com/people/ranvens/"), on Flickr

---

### Post by Ranvens on 2013-03-20
[h=5]If  this is near impossible to do, how do I go about setting up a command  shortcut to run the above script. Say if I were to type FIXBOOTINI at  the $ prompt and it were to run the above script?[/h]

---

