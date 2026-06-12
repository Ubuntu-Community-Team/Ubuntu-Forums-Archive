---
title: "Loading screen (boot splash) does not stay on throughout boot"
date: 2008-04-30
forum: General Help
---

### Post by ezramorris on 2008-04-30
Hi, I upgraded to Hardy from Gutsy, and most things work fine, but when I boot, the following happens:

To begin with, the boot splash displays, and the status bar bounces back and forth similar to the live CD.

Then, after a while, the boot splash disappears, and text scrolls up on the screen, as if "splash" and "quiet" were removed from grub.

I do, however, have "splash" and "quiet" on the kernel line, so any ideas of how to make the boot splash display throughout boot?

Thanks.

---

### Post by hermes0710 on 2008-04-30
> **ezramorris said:**
> Hi, I upgraded to Hardy from Gutsy, and most things work fine, but when I boot, the following happens:

To begin with, the boot splash displays, and the status bar bounces back and forth similar to the live CD.

Then, after a while, the boot splash disappears, and text scrolls up on the screen, as if "splash" and "quiet" were removed from grub.

I do, however, have "splash" and "quiet" on the kernel line, so any ideas of how to make the boot splash display throughout boot?

Thanks.

Go to System > Administration > Startup Manager

and see if usplash entry is enabled. (If Startup Manager is not present in the menu: ```
sudo apt-get install startup-manager
```)

---

### Post by ezramorris on 2008-04-30
> **hermes0710 said:**
> Go to System > Administration > Startup Manager

and see if usplash entry is enabled. (If Startup Manager is not present in the menu: ```
sudo apt-get install startup-manager
```)

Hi, thanks for the reply.

There is no "usplash" entry, but the following are selected:

-"Boot options"
  ---"Show boot splash" is checked

-"Appearance"
  ---"usplash-theme-ubuntu" is selected for "Usplash theme"

Also, the splash screen **does** appear when the system is shutting down.

---

### Post by hermes0710 on 2008-04-30
> **ezramorris said:**
> Hi, thanks for the reply.

There is no "usplash" entry, but the following are selected:

-"Boot options"
  ---"Show boot splash" is checked

-"Appearance"
  ---"usplash-theme-ubuntu" is selected for "Usplash theme"

Also, the splash screen **does** appear when the system is shutting down.

Try disabling usplash from the startup-manager, close startup-manager so it writes configuration and the start startup-manager again and enable usplash.

---

### Post by ezramorris on 2008-04-30
> **hermes0710 said:**
> Try disabling usplash from the startup-manager, close startup-manager so it writes configuration and the start startup-manager again and enable usplash.

Thanks, but the problem still exists.

---

### Post by hermes0710 on 2008-04-30
Ok, i got back home so now i'll try to help you more. On the first screen of the startup-manager there is a section "Display" and in this section you can change resolution and color depth. What are the values you see? Try selecting a small one (800x600 res and 8 bit color depth)

---

### Post by SpacePenguine on 2008-04-30
I'm having the exact same problem. The splash screen is there during shutdown and partially through bootup. It seems to be related to GRUB being on the same partition as Ubuntu (I dual-boot OS X Leopard and Ubuntu), as when GRUB is on a separate FAT partiton, everything works great.

Thanks in advance for help.

MacBook 2nd generation, 2GHz.
Leopard and Ubuntu dual boot.

---

### Post by ezramorris on 2008-05-01
> **hermes0710 said:**
> Ok, i got back home so now i'll try to help you more. On the first screen of the startup-manager there is a section "Display" and in this section you can change resolution and color depth. What are the values you see? Try selecting a small one (800x600 res and 8 bit color depth)

I already had the resolution set to 640x480, since 800x600 created a huge logo which fell off the right hand side of the screen, and the remaining was printed on the left.

I changed the colour bit to 8 bit, and this solved another problem I had, but this problem still exists.

---

### Post by Steve1961 on 2008-05-01
This is probably due to a wrong UUID for your swap partition.  This fix on post #16 should fix it.

[http://ubuntuforums.org/showthread.php?t=746132&highlight=usplash&page=2](http://ubuntuforums.org/showthread.php?t=746132&highlight=usplash&page=2)

---

### Post by ezramorris on 2008-05-01
> **Steve1961 said:**
> This is probably due to a wrong UUID for your swap partition.  This fix on post #16 should fix it.

[http://ubuntuforums.org/showthread.php?t=746132&highlight=usplash&page=2](http://ubuntuforums.org/showthread.php?t=746132&highlight=usplash&page=2)

Hi, the UUIDs were indeed wrong, so I changed them, but this does not solve it.. hmmm...

```
ezra@ezra-laptop:~$ sudo blkid |grep swap
/dev/sda5: TYPE="swap" UUID="cf734ce3-3123-48e6-9735-c4be1c0b1aae" 

ezra@ezra-laptop:~$ cat /etc/fstab |grep swap
cf734ce3-3123-48e6-9735-c4be1c0b1aae none            swap    sw              0       0

ezra@ezra-laptop:~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=cf734ce3-3123-48e6-9735-c4be1c0b1aae
```

---

### Post by ezramorris on 2008-05-01
> **ezramorris said:**
> Hi, the UUIDs were indeed wrong, so I changed them, but this does not solve it.. hmmm...


OK, I solved it. In order to get it to work, I had to run:

```
sudo update-initramfs -u -k all
```

Now it works brill. Thanks!

---

### Post by Steve1961 on 2008-05-01
Glad it worked for you:)

---

### Post by Stunts on 2008-05-06
Sadly, I have the very same problem, but none of these procedures seem to be able to fix it.
Any more ideas? 

Thanks

Edit: It's solved. Installing startup-manager brought usplash back to life, despite the fact that I didn't tinker with anything.

---

### Post by ezramorris on 2008-05-08
> **Steve1961 said:**
> This is probably due to a wrong UUID for your swap partition.  This fix on post #16 should fix it.

[http://ubuntuforums.org/showthread.php?t=746132&highlight=usplash&page=2](http://ubuntuforums.org/showthread.php?t=746132&highlight=usplash&page=2)

I would have posted in that thread, but it's closed;

This fix worked, but as soon as I changed my swap partition (made it bigger), the values were incorrect again. Shouldn't this be automatically updated when swap partitions are changed?

---

### Post by ezramorris on 2008-05-09
> **ezramorris said:**
> I would have posted in that thread, but it's closed;

This fix worked, but as soon as I changed my swap partition (made it bigger), the values were incorrect again. Shouldn't this be automatically updated when swap partitions are changed?

Something odd's going on here. The swap keeps turning off, and the only way I can turn it on is through gparted. swapon -a doesn't work.
[COLOR="Red"]
Edit: [/COLOR]solved: turned out i missed out the UUID in /etc/initramfs-tools/conf.d/resume .
Eg. I should have put ```
RESUME=[COLOR="Red"]**UUID=**[/COLOR]b9488bfa-30f4-4d99-b754-eb5699c533a8
``` not ```
RESUME=b9488bfa-30f4-4d99-b754-eb5699c533a8
```

---

### Post by ezramorris on 2008-07-16
Well, I got that sorted, but I never sorted the problem of when it shuts down. When I click shut down, I see the tail of the start up messages, then it scrolls some text, and finally shows usplash at the end, but in a weird inverted colour.

Any ideas?

---

