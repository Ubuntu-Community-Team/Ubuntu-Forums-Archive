---
title: "Shutdown problem with Gutsy"
date: 2007-12-01
forum: General Help
---

### Post by alakin on 2007-12-01
I have not found a way that I can shut down cleanly. Even with:

sudo shutdown -h now

I get error messages on the vt that shows after the splash screen vanishes:

NetworkManager:<WARN> nm_hal_deinit():libhal shutdown failed - Connection closed

NetworkManager: nm_dbus_signal_device_status_change: assertain 'cb_data->data->dbus_connection' failed

I then have to power off manually. I have tried a few tips from the forum. I have added to the /etc/modules file:

apm power_off=1

and I have appended to the kernel line in /boot/grub/menu.lst:

acpi=off apm=power_off

I also tried acpi=force and rendered my box unbootable! I won't do that again.

None of this works for me and I have notice the desktop being a bit sluggish - this may not be related, but waiting 5 seconds for konsole to open is not acceptable.

I have not had this problem with other distros. I have used arch and slackware in recent years and mandrake before that. Shutdown was never a problem. My hardware is:

Athlon64 3000 - Foxconn motherboard
Nvidia GeForce FX 550
Both IDE drive and SATA drive
1.5 Gig ram

Any ideas.

Alan

---

### Post by nicodoggie on 2008-02-16
I have the same problem as well, it happens intermittently though... 

My hardware is

Athlon64 3000
Asus K8U-X Motherboard
Nvidia GeForce FX 5500
1 GB RAM

We have similar hardware... maybe it has something to do with the specs we have in common? (CPU and/or Video Card)

I hope someone could help... I have a dial-up connection which is free of charge during off-peak hours (12-6 AM) and I usually perform updates and do all my heavy downloading while I sleep so I often use the shutdown -P <minutes_to_shutdown> command so I don't waste power (I usually wake up at 10 AM). 

Thanks a lot!! :)

---

### Post by eeefresh on 2008-02-16
I have noticed on my system that it takes almost a full minute for the log off/power off screen to appear after I hit the power button in the upper right of the desktop.  It eventually comes up...just a long delay.  Also, I have noticed that if I just close that box and click the power button again, it pops right up, much faster the second time.  Any ideas?

---

### Post by nicodoggie on 2008-02-20
Hmm... never happened to me before, probably a memory thing? 'Cause after the initial loading, the program might still be loaded in memory, making the second loading much faster, not sure though.

---

