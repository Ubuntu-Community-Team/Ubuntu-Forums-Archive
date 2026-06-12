---
title: "[SOLVED] How do I mount a usb drive early in the boot process?"
date: 2008-03-23
forum: General Help
---

### Post by MountainX on 2008-03-23
Here is my problem mounting a usb flash drive which contains the keys to mount my encrypted partitions:

device: ssd
FAT: codepage cp437 not found

This happens before my encrypted file system is decrypted.

I followed this guide:
[http://wejn.org/how-to-make-password...ryptsetup.html](http://wejn.org/how-to-make-password...ryptsetup.html)
How to setup passwordless disk encryption in Debian Etch

After I have booted up, I can mount the usb drive as follows:

Code:

$ sudo mount -t vfat /dev/sdd1 /mnt

The important part of the script I'm using is here. (The whole script is found at the link above.)


```
MD=/tmp-usb-mount

echo "Trying to get the key from USB keychain ..." >&2
mkdir -p $MD
modprobe usb-storage >/dev/null 2>&1
modprobe vfat >/dev/null 2>&1
sleep 7
OPENED=0
for SFS in /sys/block/sd*; do
	DEV=`basename $SFS`
	F=$SFS/${DEV}1/dev
	if [ 0`cat $SFS/removable` -eq 1 -a -f $F ]; then
		echo "> Trying device: $DEV ..." >&2
		mount /dev/${DEV}1 $MD -t vfat -o ro 2>/dev/null
		if [ -f $MD/$KEYF ]; then
			cat $MD/$KEYF
			umount $MD 2>/dev/null
			OPENED=1
			break
		fi
		umount $MD 2>/dev/null
	fi
done
```



I suspect the problem is related to /etc/initramfs-tools/modules, but that's just a guess. Here are the contents of that file:

# List of modules that you want to include in your initramfs.
#
# Syntax:  module_name [args ...]
#
# You must run update-initramfs(8) to effect this change.
#
# Examples:
#
# raid1
# sd_mod
vfat
nfat
nnls_cp437
nnls_iso8859_1

---

### Post by MountainX on 2008-03-24
I think I have a solution now. The solution was offered here:
[http://www.linuxquestions.org/questions/linux-server-73/how-do-i-mount-a-usb-drive-at-boot-time-630115/](http://www.linuxquestions.org/questions/linux-server-73/how-do-i-mount-a-usb-drive-at-boot-time-630115/)

I will be able to test it tomorrow and I'll report back if that doesn't solve it, but I think it will.

For those wanting to know the solution but not wanting to follow the link, here is a copy:

My problem came from this line in the guide

```

# echo -e "vfat\nfat\nnls_cp437\nnls_iso8859_1" >> /etc/initramfs-tools/modules

```

I couldn't get that command to work (permissions), so I had to edit the file by hand. And I assumed the "\" were line break characters. Now that you point out the problem, I see that the obvious: "\n" is the line break! Being a Linux noob is tough sometimes ;)

---

