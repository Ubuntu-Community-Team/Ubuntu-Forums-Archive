---
title: "Why doesn't this bash dscipt work"
date: 2019-06-01
forum: General Help
---

### Post by mibadt on 2019-06-01
Hi,
I'm on an Lubuntu 18.04 (32b) (old) laptop.
I have written the following bash script (Added below) aimed at backup a memory card (from one out of three cameras) to two SSD USB external drives.
I have mounted SSD_BACKUP1 and a (D5500 created) memory card. 
Each memory card contains several folders under the DCIM folder  with multiple files in those folders.
Running the script it begins OK and asks me to select the source camera.
Once i press 2 and {ENTER] the script exits with the following  errors (which I can't understand).
I'd appreciate any help fixing these (and potentially more..) errors in the script.

Thanks a lot upfront

Miki

-------------the errors I get--------------------
```

$ ./photo
Select  1, 2 or 3:  1-D810, 2-D5500 3-D7500  2
Selected CAMERA number is    2
./photo: line 6: syntax error near unexpected token `SOURCE="/media/miki/NIKON\ D810/DCIM"'
./photo: line 6: `1  SOURCE="/media/miki/NIKON\ D810/DCIM"'
[miki@miki-notepad ~]$

```
--------------------------------------------------------

----------------my script--------------------------
```

#!/bin/bash
echo -n   "Select  1, 2 or 3:  1-D810, 2-D5500 3-D7500  "
read CAMERA
echo  "Selected CAMERA number is   "  $CAMERA
case $CAMERA in 
1  SOURCE="/media/miki/NIKON\ D810/DCIM"
;;
2  SOURCE="/media/miki/NIKON\ D5500/DCIM"
;;
3  SOURCE="/media/miki/NIKON\ D7500/DCIM"
;;
esac
echo
echo  "Selected source  is " $SOURCE
echo


TARGET1="/media/miki/SSD_BACKUP1/"
TARGET2="/media/miki/SSD_BACKUP2/"

echo
echo "TARGET1 is   " $TARGET1
echo
echo "TARGET2  is   " $TARGET2
echo

rsync -avW $SOURCE $TARGET1

echo  SSD_BACKUP1 copied
echo

rsync -avW  $SOURCE  $TARGET2

echo
echo  "Photos copied   "
echo
echo "remaining space
echo"
df -h | grep home

df -h | grep $SOURCE
df -h  | grep  /media/miki/SSD_BACKUP1
df -h  | grep  /media/miki/SSD_BACKUP2


```
------------------------------

---

### Post by The Cog on 2019-06-01
You are missing a close bracket after the numbers in the case statements. Try:
```
case $CAMERA in
1)  SOURCE="/media/miki/NIKON\ D810/DCIM"
;;
2)  SOURCE="/media/miki/NIKON\ D5500/DCIM"
;;
3)  SOURCE="/media/miki/NIKON\ D7500/DCIM"
;;

```
[https://www.tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_03.html](https://www.tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_03.html)

---

### Post by mibadt on 2019-06-01
Thanks  a lot.
I'll try (later) and update

---

### Post by mibadt on 2019-06-01
Thanks,

Solved by:
1) adding close bracket as proposed
2) removing the back slash from the SOURCE statements
3) Adding double quotes to the string variables in the rsync commands

Take care

---

### Post by HermanAB on 2019-06-02
Note that with a backup script, it is usually better to select most everything and then exclude more specific things.  The script will then be mostly maintenance free over time.

---

