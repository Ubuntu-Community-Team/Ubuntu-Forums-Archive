---
title: "How to be prompted for password when booting Feisty"
date: 2007-06-30
forum: General Help
---

### Post by Rodrigue on 2007-06-30
Hi,

I just encrypted a new partition where I have the /usr directory containing also /var, /home and /tmp.  Everything works fine, I can read and write to it.  But for it to work when mounted at /usr, the mount has to be done at boottime...

I read a few tutorials about it.  I wrote a script that executes at boot, it is in /etc/rc2.d, with

cryptsetup luksOpen /dev/sda4 crypt4

but I should be asked for a passphrase at this point...  but nothing happens.  And when I get the gnome prompt, the /usr directory is the actual unencrypted one instead of my encrypted partition.

So my question is:

How do I do to be asked the passphrase when booting?  (a passphrase or anything else... I don't know much about sh scripting)

Thank you

---

### Post by Computer-Geek on 2007-07-01
Let me look for the webpage and send u the URL.

---

### Post by Rodrigue on 2007-07-04
OK, I found my answer at this site [http://www.c3l.de/linux/howto-completly-encrypted-harddisk-including-suspend-to-encrypted-disk-with-ubuntu-6.10-edgy-eft.html](http://www.c3l.de/linux/howto-completly-encrypted-harddisk-including-suspend-to-encrypted-disk-with-ubuntu-6.10-edgy-eft.html)

Either I had missed something or this was supposed to be obvious, but all I had to do to make the changes in /etc/crypttab and /etc/fstab effective was
```
update-initramfs -u -k 2.6.20-16-generic
```

and edit */boot/grub/menu.lst* to remove the *splash* and voilà!  It asks for a passphrase now!

Also, I found I had to modify the code in the file */lib/cryptsetup/cryptdisks.functions* around line 268 to take the input from /dev/console instead of &1.  It now looks like this:

```

if test "x$INTERACTIVE" != "xyes" ; then
			PARAMS="$PARAMS --key-file=$key"
			# $CRYPTCMD $PARAMS luksOpen $src $dst <&1
			$CRYPTCMD $PARAMS luksOpen $src $dst </dev/console
		else
			if [ -x /sbin/usplash_write -a -p /dev/.initramfs/usplash_outfifo ]; then
			     	/sbin/usplash_write "QUIT"
				# saftey sleep !
				sleep 2
			fi
			# $CRYPTCMD $PARAMS luksOpen $src $dst <&1
			$CRYPTCMD $PARAMS luksOpen $src $dst </dev/console
		fi

```

---

