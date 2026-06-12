---
title: "MOUNT SCRIPT using BLKID OUTPUT"
date: 2012-11-23
forum: General Help
---

### Post by rhss6-2011 on 2012-11-23
Hello there, I am working on creating a script that will mount all my labeled partitions after I log in.
I have a script from a friend that finds the **/dev/sda???** and then creates a folder with the results in which to mount a partition.

**THIS SCRIPT**

```

BASEDIR="/mnt"

for PARTITION in `fdisk -l | grep -v swap | egrep -o /dev/sd.[0-9]+` ; do
mount | grep -q "$PARTITION"
if [ $? -eq 1 ] ; then
blkid $PARTITION > /dev/null
if [ $? -eq 0 ] ; then
MOUNTPOINT=$BASEDIR/`echo $PARTITION | egrep -o sd.[0-9]+`
mkdir -p $MOUNTPOINT
mount $PARTITION $MOUNTPOINT
fi
fi
done
exit 0

```
***_FOR EXAMPLE*_ /dev/sda5** would be mounted in **/mnt/sda5**

I basically want to do exactly that, **except** I want to **use the partition label and not sda???**.

**I got this far**:
```

pswd="MY-PASSWORD"
BLKID=$(echo $pswd | sudo -S blkid)
echo $BLKID > ~/my_blkid.txt
**for x in `[B]grep ???** ~/my_blkid.txt` ; do
*#Finds the label of the partitions*[/B]
echo pswd | sudo -S mkdir /media/$x
echo pswd | sudo -S mount **???**

```

Contents of my_blkid,txt
```

/dev/sda1: LABEL="**WIN_7**" UUID="7A61F35A4FA4167C" TYPE="ntfs" /dev/sda5: LABEL="**XUBUNTU**"
UUID="545171da-a0d2-40a0-8f9b-d19c0ca99874" TYPE="ext4" /dev/sda6: 
UUID="5aef87a5-77da-4b6f-888e-91579e22288b" TYPE="swap" /dev/sda7: LABEL="**DATA_VOLUME**"
UUID="e22d7fec-93e9-4e57-8238-eb26e0418ab7" TYPE="ext4" /dev/sdb1: LABEL="**OSENEGG32GB**"
UUID="E15E-82A9" TYPE="vfat"

```


And now I'm stuck...
Can anyone help me?

---

### Post by Vaphell on 2012-11-23
assuming you use bash

```
pswd="MY-PASSWORD"
labels=( $( echo "$pswd" | sudo -S blkid | sed -rn '/LABEL/s/.*LABEL="([^"]+)".*/\1/p' ) )
for l in "${labels[@]}"
do
  echo "$l"
done
```

use $() istead of deprecated ``
also try to avoid all-caps variable names, you can override some env variable by accident (all caps by convention) and you won't know why funky things happen.

---

### Post by rhss6-2011 on 2012-11-24
Alright, thanks.

Now that the Terminal can find the labels all right, how do I implement that with mounting the partitions to the corresponding labels?

Maybe creating the **BLKID file**, and using **find** to search for the correct **SDA???** for the right label to **mount**?

---

### Post by Vaphell on 2012-11-25
try this
```

for l in "${labels[@]}"
do
  echo pswd | sudo -S mkdir /media/"$l"
  echo pswd | sudo -S mount -L "$l" /media/"$l"
done
```

---

### Post by rhss6-2011 on 2012-11-26
Alright, thanks :guitar:

---

