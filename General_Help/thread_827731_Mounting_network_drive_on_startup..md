---
title: "Mounting network drive on startup."
date: 2008-06-13
forum: General Help
---

### Post by Rafal07BC on 2008-06-13
Hello.

I have router with connected usb drive and I am wondering how I could mount it on system start.

This is the problem, because of limited resources I am running samba 2.x on the router.
New versions of samba ( above 3.0.26 ) allows only read access to router disk ( not fully compatible with samba 2.x ).
Because of this I have compiled samba 3.0.22 on my Xubuntu and use it to mount router drive.
By default make installed this samba version in /usr/local/samba/ directory. I like this because it lets me to run new version of samba together with the old one that I keep for compatibility reasons.

But now the question is how can I mount router drive from fstab using samba 3.0.22 ( /usr/local/samba/bin/smbmount ) instead of newest version that is installed in environment PATH variable?

And if this is not possible then what other solution is there?

---

### Post by fsmithred on 2008-06-13
If you can mount it from command line using the correct version, then you should be able to put that command in /etc/rc.local and get the result you want.

---

### Post by Zorael on 2008-06-13
You could also rename [FONT="Courier New"]/usr/bin/smbmount[/FONT] to make it default to your [FONT="Courier New"]/usr/**local**/bin[/FONT] one, then add it to your fstab. Note though that your smbmount is probably just a symbolic link to [FONT="Courier New"]/sbin/mount.smbfs[/FONT] or [FONT="Courier New"]/sbin/mount.cifs[/FONT], so there is a chance that fstab calls that one directly instead of the smbmount symlink. Hence, you may need to rename/relink those.

Mount it normally from the command-line with the options you want, then open up [FONT="Courier New"]**/etc/mtab**[/FONT] and find its entry there. There you can see all your mounts expressed how fstab interprets them. Copy your samba-mounted line and paste it in your [FONT="Courier New"]**/etc/fstab**[/FONT]. Now *unmount* the samba directory, and then do '**sudo mount -a**' to see if it automounts properly. If it does, presto, try rebooting.

You will probably need to add the option **_netdev** to its entry in fstab to make it try to mount it *after* network connections have been established. Else it will stop there and try until it times out (or until you Ctrl+C). From [the man page of mount](http://linux.die.net/man/8/mount):
```
**_netdev**
    The filesystem resides on a device that requires network access (used to prevent the system from attempting to mount these filesystems until the network has been enabled on the system).
```

If you're having trouble with the mount disappearing (perhaps after suspend), you could create a script that manually checks to see if it is mounted, and if not, mounts it automatically. With this, you could skip the whole fstab solution. See [http://ubuntuforums.org/showthread.php?t=788146](http://ubuntuforums.org/showthread.php?t=788146).

---

### Post by Rafal07BC on 2008-06-23
Thanks for your answers.

I have tried fsmithred method but I still cant mount it on startup.

I hope you can point out error I make.

I have created mountRouter script in /etc/init.d/
```

 #!/bin/bash
  2 ### BEGIN INIT INFO
  3 # Required-Start: $network
  4 # Default=Start: 2
  5 ### ENID INIT INFO
  6 case "$1" in
  7         'start')
  8         /usr/local/samba/bin/smbmount //router/dysk1 /mnt/router -o rw,guest
  9         ;;
 10         'stop' )
 11         umount /mnt/router
 12         ;;
 13 esac
 14 
 15 exit 1


```

I can now mount and unmount router by command /etc/init.d/mountRouter start or stop

I have used update-rc.d to create simbolic links in rcX.d directories.

```

-rwxrwxrwx 1 root rafal 241 2008-06-23 07:39 ./init.d/mountRouter
lrwxrwxrwx 1 root root   21 2008-06-22 19:36 ./rc0.d/K20mountRouter -> ../init.d/mountRouter
lrwxrwxrwx 1 root root   21 2008-06-22 19:36 ./rc1.d/K20mountRouter -> ../init.d/mountRouter
lrwxrwxrwx 1 root root   21 2008-06-22 19:36 ./rc2.d/S20mountRouter -> ../init.d/mountRouter
lrwxrwxrwx 1 root root   21 2008-06-22 19:36 ./rc3.d/S20mountRouter -> ../init.d/mountRouter
lrwxrwxrwx 1 root root   21 2008-06-22 19:36 ./rc4.d/S20mountRouter -> ../init.d/mountRouter
lrwxrwxrwx 1 root root   21 2008-06-22 19:36 ./rc5.d/S20mountRouter -> ../init.d/mountRouter
lrwxrwxrwx 1 root root   21 2008-06-22 19:36 ./rc6.d/K20mountRouter -> ../init.d/mountRouter

```

What am I missing?

What log file should I check for any errors ?

---

### Post by PaulHuffman on 2008-06-24
I used Zorael's method with success, but I couldn't remember how to unmount the samba mount for testing. I just restarted. I didn't add the _netdev option.  At restart, the samba mount was empty at first, then 2 seconds later a little file system icon for it appeared on the desktop, then the samba mount was populated. So I think this means that the system I'm mounting is close enough that the samba mount gets made before it times out without the _netdev option.

However, sometimes this mount doesn't appear for as long as ten minutes when the windows system is loaded down. How do I improve that?  Can I get samba to knock on the door a little harder?

2008-07-07 update. I just noticed that all I have to do to get the file system icon to pop up is to start a terminal window.  So is fstab not accessed until a terminal window is launched?

---

