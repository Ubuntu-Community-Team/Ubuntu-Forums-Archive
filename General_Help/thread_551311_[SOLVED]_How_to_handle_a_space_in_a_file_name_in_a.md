---
title: "[SOLVED] How to handle a space in a file name in abash script?"
date: 2007-09-15
forum: General Help
---

### Post by BillDozer on 2007-09-15
Hi,

I have the following script to retrieve the latest gutsy release.
```
#!/bin/bash
#Script for updating individual ISO image at cdimage.ubuntu.com (daily/current versions).
#Script written by Henrik Omma

ISO="gutsy-desktop-i386.iso"
DIR="/media/My Book/distros"
ISOPATH="cdimage.ubuntu.com/cdimage/daily-live/current"

cd $DIR
echo Retrieving $ISO.
rsync -Lvv --progress rsync://$ISOPATH/$ISO .
echo Creating checksum...
md5sum $ISO | sed -e "s/  / */" > $ISO.md5.local #create identical formatted md5sum file from local copy
echo Retrieving checksum for $ISO from server.
wget http://$ISOPATH/MD5SUMS 
grep $ISO MD5SUMS > $ISO.md5.server
rm MD5SUMS
```

But I have a problem changing the directory correctly because there is a space in the file name. I also tried using the normal command line syntax with a \ before the space but that does not help either.

Probably a very simple solution, so thanks in advance :)

---

### Post by FuturePilot on 2007-09-15
I take it this is the directory giving you problems?
```
DIR="/media/My Book/distros"
```
Try
```
DIR="/media/My\ Book/distros"
```
Oops, read too fast, you already tried that. Hmmm

---

### Post by bodhi.zazen on 2007-09-15
You need to "protect" you variable ;)

> #!/bin/bash
#Script for updating individual ISO image at cdimage.ubuntu.com (daily/current versions).
#Script written by Henrik Omma

ISO="gutsy-desktop-i386.iso"
DIR="/media/My Book/distros"
ISOPATH="cdimage.ubuntu.com/cdimage/daily-live/current"

cd **[color=blue]"$DIR"[/color]**
echo Retrieving "$ISO".
rsync -Lvv --progress rsync://"$ISOPATH"/"$ISO" .
echo Creating checksum...
md5sum $ISO | sed -e "s/  / */" > $ISO.md5.local #create identical formatted md5sum file from local copy
echo Retrieving checksum for "$ISO" from server.
wget http://"$ISOPATH"/MD5SUMS 
grep "$ISO" MD5SUMS > $ISO.md5.server
rm MD5SUMS

I think I got them all (I only added color and bold to the first instance).

You could also use a _ in your directory rather the a <space>

---

### Post by BillDozer on 2007-09-15
Thank you, just what I was looking for.

I knew it had to be something simple, just couldn't find it. Works like a charm now.

---

