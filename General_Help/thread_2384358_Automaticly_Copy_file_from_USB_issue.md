---
title: "Automaticly Copy file from USB issue"
date: 2018-02-06
forum: General Help
---

### Post by grinn2 on 2018-02-06
Hello,

I am trying to copy autocratically the total content of USB data to a folder and then remove the USB content.
I created a rule in /etc/udev/rules.d/ that calls a custom script. 
The script is called but  the "cp" command fails with : cannot stat '/media/toto/IRIS/DCIM/100MEDIA/* No such file or directory'
I felt the script was called before the USB being mounted so I tried to cp from /dev/sdb1 instead but got the same kind of error : 
 'cp: cannot stat '/dev/sbd1/DCIM/100MEDIA/*': Not a directory'

Do you know you what could I do to ask the system to mount the USB before calling this script ?
Or globally, do you have another solution for copying automatically USB data when the stick is plugged ?

Thank you

---

### Post by sudodus on 2018-02-06
Please show your script in a reply! It will help us help you.

Post the output between code tags like this
 
[noparse]```

output

```[/noparse]
 
to get output like this
 
```

output

```

---

### Post by grinn2 on 2018-02-06
ok here is /etc/udev/rules.d/iris_scan.rules :
```

ACTION=="add|change", KERNEL=="*", ATTRS{model}=="MagicScan       ", RUN+="/etc/script/iris_scan.sh"


```

and here is /etc/script/iris_scan.sh :
```

#!/bin/bash

 cp  /media/toto/IRIS/DCIM/100MEDIA/* /home/toto/Documents/

 rm /media/toto/IRIS/DCIM/100MEDIA/*

  
```

---

### Post by sudodus on 2018-02-06
I suggest that you unmount (if automounted) and mount the partition in the external drive in the script (before the copy command)

It is a good idea to **identify the UUID of the partition**, that contains the data you want to copy.

```

sudo lsblk -o model,name,uuid,fstype

```

and then use this UUID in a mount command to a pre-defined mountpoint, it can be 'any directory' for example /mnt/iris.

```

sudo mkdir /mnt/iris

```

Then you can mount it and copy the files with the following commands

```

sudo umount  <UUID>
sudo mount -U <UUID> /mnt/iris
sudo cp /mnt/iris/* /home/toto/Documents/ && sudo rm /mnt/iris/*
sudo umount  <UUID>

```

**<UUID>** should be replaced with the actual UUID string (for example **E14D-9F10** for a FAT32 file system) to match the partition as identified with the lsblk command.

**&&** makes the rm command run only if the cp command was successful.

It is a good idea to unmount before finishing in order to avoid unplugging a mounted partition. You may need to modify the script, if there are more partitions that are automounted.

---

### Post by HermanAB on 2018-02-06
Hmm, some things to bear in mind:
If you give a removable media device a Volume Name, then it will always mount with the same path.
The volume name also makes it easier to script the mount command.
If you add mention of that device in fstab, then you can ensure that it is mounted with mount -a
If you want to delete data after copying it, then you need to be absolutely sure that the data copied OK, otherwise you will eventually be sorely disappointed.
One way to make reliable copies, is with the rsync command.  It is a better kind of copy command in many respects.

---

### Post by grinn2 on 2018-02-06
It works well. Thank you!

---

### Post by sudodus on 2018-02-06
You are welcome :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

