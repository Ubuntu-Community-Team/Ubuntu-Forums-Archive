---
title: "Installing Liberte Linux from Ubuntu"
date: 2015-02-08
forum: General Help
---

### Post by trackmagic on 2015-02-08
I am trying to install Liberte onto a USB stick (I have formatted this as FAT32).

I copied the Liberte zip file and extracted its contents to the USB drive.

I logged in my root account and typed this is the terminal:

/media/q-unit/664B-056B/liberte-2012.3/liberte/setup.sh

the terminal returns bash: /media/q-unit/664B-056B/liberte-2012.3/liberte/setup.sh: Permission denied


Does anybody know what I am doing wrong?

---

### Post by trackmagic on 2015-02-08
q-unit is my root account name and the USB drive is the 664B-056B

FYI

---

### Post by oldos2er on 2015-02-08
According to [http://dee.su/liberte-install](http://dee.su/liberte-install) you need to run setup.sh as root, so try ```
sudo bash /media/q-unit/664B-056B/liberte-2012.3/liberte/setup.sh
```

---

### Post by trackmagic on 2015-02-08
Thanks Ann, This does appear to have gotten me farther .I noticed that I am supposed to add "auto" to the end so it would be:

"sudo bash /media/q-unit/664B-056B1/liberte-2012.3/liberte/setup.sh auto"

When I type that I get this error:
/media/q-unit/664B-056B1/liberte-2012.3 is not a mount point

FYI, I changed the permissions to the folder /media/q-unit/664B-056B1 by using:
sudo mkdir /media/drive_name
sudo chmod 777 /media/drive_name
(I did this after removing the drive of course)

I am not sure if that would have caused the mount point issue.

---

### Post by trackmagic on 2015-02-08
Solved!

I needed to move the files out of the "liberte-2012.3" folder and make the "liberte" folder just below the mount point. Then you run:
"sudo sh /media/q-unit/664B-056B1/liberte/setup.sh auto"

---

### Post by mastablasta on 2015-02-09
might have been easier to just use the ISO+startup disk creator. as I know liberte is ment to be run as live OS.

also I wonder how relevant it is since it is so old. was just wondering the other day. it is nice and very light. on newish hardware and even a bit older one it works really snappy. at  least if we compare it to Tails. now Tails gets updates, security patches, various other things and issues resolved while Liberte just stayed at that version. strange.

---

