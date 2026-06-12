---
title: "root encryption and usb key file"
date: 2008-05-06
forum: General Help
---

### Post by nightfrost on 2008-05-06
Dear community,

I have successfully installed ubuntu hardy on an encrypted system using the alternate CD. The password I have chosen is long and tedious to enter everytime I boot. Therefore I would like to have a key file to on a usb stick, have it automounted at boot time when it's there and unlock the partitions without any user interaction. 

Is there any way to do this in Hardy? 

I have found, for example, this [https://help.ubuntu.com/community/GutsyLUKSTwoFormFactor](https://help.ubuntu.com/community/GutsyLUKSTwoFormFactor) and other howtos, but none that explicitly states it is safe for Hardy. Any suggestions?

EDIT: I have tried numerous times to get this working and the main problem seems to be that I my keyscript file never gets copied to the initramfs. How do I make sure it gets added?

---

### Post by nightfrost on 2008-05-06
Sorry to reply to my own post. I now believe this to be a bug and if no one discourages me I will file it at launchpad.

my /etc/crypttab contains
sda3_crypt /dev/disk/by-uuid/xxx root.key luks,keyscript=/boot/mountkey.sh

I have also tried to put the keyscript in /usr/local/sbin, /sbin, and /bin, none of which help. The reason I finally put in /boot of all places, is because I hoped adding CRYPTDISKS_MOUNT="/boot" to /etc/cryptdisks would solve my issue, but it didn't.


After waiting long enough while ubuntu tries to boot, I finally see this message:

```
/scripts/local-top/cryptroot: /scripts/local-top/cryptroot: 276: /keyscripts/mountkey.sh: not found
Command failed: No key available with this passphrase

```

Apparently initramfs doesn't include my keyscript. And the /keyscripts dir is something I know nothing about.

---

### Post by bodhi.zazen on 2008-05-06
I found this link : [http://www.debianhelp.org/node/6797](http://www.debianhelp.org/node/6797)

---

### Post by nightfrost on 2008-05-06
> **bodhi.zazen said:**
> I found this link : [http://www.debianhelp.org/node/6797](http://www.debianhelp.org/node/6797)

Thanks for the reply. That thread is actually one of the ones I've been following. In fact, these lines from that thread made me wonder whether this isn't in fact a hardy specific bug:

> Note that using /sbin is not required, you can save the keyscript
anywhere you like and adapt your crypttap accordingly.

- rebuild the initrd using update-initramfs -u. It will include your
keyscript automatically, no need to copy anything on your own.

---

### Post by nightfrost on 2008-05-07
Aha! I found this while running initramfs-update -u:

```
cryptsetup: WARNING: target sda3_crypt uses a key file, skipped

```

Why skip? I don't want it to skip...

---

### Post by Dolphin26 on 2008-05-26
I'm getting the same error, but I'm pretty sure it IS copying the keyscript because if I use zcat & cpio to unpack the initrd I see my keyscript, but it still complains about it not existing when I boot.  Anyway, I'm subscribing to this thread in case someone posts a workaround or other useful information.  

nightfrost: When you say you're going to report it at launchpad, what do you mean?  Is this a ubuntu bug tracking system that I might be able to subscribe to so I know when it's fixed?

Thanks!

---

### Post by nightfrost on 2008-05-27
> **Dolphin26 said:**
> I'm getting the same error, but I'm pretty sure it IS copying the keyscript because if I use zcat & cpio to unpack the initrd I see my keyscript, but it still complains about it not existing when I boot.  Anyway, I'm subscribing to this thread in case someone posts a workaround or other useful information.  

nightfrost: When you say you're going to report it at launchpad, what do you mean?  Is this a ubuntu bug tracking system that I might be able to subscribe to so I know when it's fixed?

Thanks!

[launchpad]("https://bugs.launchpad.net/") is Ubuntu's bug tracking system. You should consider signing up there and report any bugs you find, and, as you suggest yourself, subscribe to bugs you're interested in following. I haven't had time to report this particular bug yet, but if you would happen to find the time to do so, I would be most greatful :-)

---

### Post by Dolphin26 on 2008-06-09
Nightfrost, I no longer think this is a bug except perhaps in that the error messages are misleading.  While debugging this issue more throughly, I discovered that my keyscript specified an interpreter that didn't exist in the initramfs.  It's a simple shell script, and I started it the way I start all shell scripts:

#!/bin/bash

However, bash isn't included in initramfs.  So I changed this to:

#!/bin/sh

and it worked!  Maybe your problem is similar?

---

### Post by nightfrost on 2008-06-10
> **Dolphin26 said:**
> Nightfrost, I no longer think this is a bug except perhaps in that the error messages are misleading.  While debugging this issue more throughly, I discovered that my keyscript specified an interpreter that didn't exist in the initramfs.  It's a simple shell script, and I started it the way I start all shell scripts:

#!/bin/bash

However, bash isn't included in initramfs.  So I changed this to:

#!/bin/sh

and it worked!  Maybe your problem is similar?

That's great! Thanks a lot, what a stupid mistake to make. This has been plaguing me for so long. Do you get this working also with usplash? Because that doesn't seem to work for me?

---

### Post by nightfrost on 2008-06-11
I've been looking around in /usr/share/initramfs-tools/scripts, particularly the script cryptroot in top-local/. Shouldn't adding the commented out block basically support usb keyfiles with usplash?

```
	# Try to get a satisfactory password three times
	count=0
	while [ $count -lt 3 ]; do
		count=$(( $count + 1 ))

		if [ -n "$cryptkeyscript" ]; then
			if [ ! -x "$cryptkeyscript" ]; then
				echo "cryptsetup: error - $cryptkeyscript missing"
				return 1
			fi
			crypttarget="$crypttarget" cryptsource="$cryptsource" \
			$cryptkeyscript $cryptkey < /dev/console 2> /dev/console | \
			$cryptcreate --key-file=- > /dev/console 2>&1
########### This block should add usb key support		
#		elif [ -e /dev/disk/by-uuid/$usbkey ]; then
#			mkdir -p /tmp/$usbkey
#			mount /dev/disk/by-uuid/$usbkey /tmp/$usbkey -o ro -t ext2
#			$cryptcreate --keyfile=/tmp/$usbkey/luks.key
#			umount /tmp/$usbkey
########### End of block			
		elif [ -p /dev/.initramfs/usplash_outfifo ] && [ -x /sbin/usplash_write ]; then
			usplash_write "INPUTQUIET Enter password to unlock the disk ($crypttarget): "
			PASS="$(cat /dev/.initramfs/usplash_outfifo)"
			echo -n "$PASS" | $cryptcreate > /dev/null 2>&1
		else
			$cryptcreate < /dev/console > /dev/console 2>&1
		fi

		if [ $? -ne 0 ]; then
			echo "cryptsetup: cryptsetup failed, bad password or options?"
			sleep 3
			continue
		elif [ ! -e "$NEWROOT" ]; then
			echo "cryptsetup: unknown error setting up device mapping"
			return 1
		elif [ -p /dev/.initramfs/usplash_outfifo ] && [ -x /sbin/usplash_write ]; then
			# clean the text, to give feedback that it worked
			usplash_write "TEXT-URGENT "
		fi

		FSTYPE=''
		eval $(fstype < "$NEWROOT")

		# See if we need to setup lvm on the crypto device
		if [ "$FSTYPE" = "lvm" ] || [ "$FSTYPE" = "lvm2" ]; then
			if [ -z "$cryptlvm" ]; then
				echo "cryptsetup: lvm fs found but no lvm configured"
				return 1
			elif ! activate_vg "/dev/mapper/$cryptlvm"; then
				echo "cryptsetup: failed to setup lvm device"
				return 1
			fi

			NEWROOT="/dev/mapper/$cryptlvm"
			eval $(fstype < "$NEWROOT")
		fi

		if [ -z "$FSTYPE" ] || [ "$FSTYPE" = "unknown" ]; then
			echo "cryptsetup: unknown fstype, bad password or options?"
			$cryptremove
			sleep 3
			continue
		fi

		break
	done

```

Where usbkey is defined either in the same script or a config file. Of course, there should be some sort of an error checking, so that if no keyfile is found the script continues like normal, whereas if cryptsetup returns success, the next elif block should be skipped. But the basic idea should work, no?

---

