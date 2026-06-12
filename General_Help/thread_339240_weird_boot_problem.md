---
title: "weird boot problem"
date: 2007-01-15
forum: General Help
---

### Post by Dambrosio on 2007-01-15
I recently had to re-install ubuntu 6.10 because of a beryl problem but thats beside the point. My first ubuntu install I upgraded from 6.06 to 6.10 because whenever I install from the 6.10 disk my computer hangs on bootup for a good couple of minutes, then it finally works. But when I install 6.06 and upgrade to 6.10 it doesn't hang. I tried to figure out where it is getting hung up by editing the boot line by removing "quite" and nothing happened. This is a fresh install of 6.10 from the disk and I applied all the updates.  Does anyone know how i can fix this hang?

Thanks

---

### Post by mvaniersel on 2007-01-15
Have you checked the integrity of the 6.10 CD (there is an option in the CD boot menu)? There could be a scratch on it or something...

Do you mean the delay is there when you boot from CD, or is the delay there whenever you reboot, after succesful installation?

---

### Post by Dambrosio on 2007-01-15
This has happened multiple times on different CD installs. It happens after a successful install on the reboot (without the cd). When it finally loads, everything works fine. When I start linux again it does the same thing. How can I figure out what it is hanging up on?

---

### Post by mvaniersel on 2007-01-16
You can turn boot messages back on to see what is going on during boot. To do this, you need to edit /boot/grub/menu.lst. Look for lines like this one:

 /boot/vmlinuz-2.6.17-10-generic root=/dev/sda6 ro quiet splash

and remove the "quiet" parameter for the menu item that you use normally.

---

### Post by Dambrosio on 2007-01-16
After removing "quiet" from the /boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash and restarting the computer, I found out that ubuntu is hanging on "configuring network interfaces". That is the only part where the boot up is slow or hanging up. My ethernet card is working so i think it might be getting stuck on my wireless card. I have a dell inspiron E1705 with a Intel Pro/ Wireless 3945 ABG card.

---

### Post by Dambrosio on 2007-01-16
I was looking through some forum posts and found this:
```
sudo update-rc.d -f networking remove
sudo update-rc.d networking defaults 99
```
I tried this and it booted right up. I also checked my wireless and it worked. So i think this is the solution yet I have no idea what it does.

---

### Post by mvaniersel on 2007-01-17
If I'm not mistaken that makes sure that networking is initialized as the last step. 

With config-rc.d you can change what is going on during boot, and here you set networking to go at step 99.

Still not sure why that solves your problem, but congratulations on fixing it.

---

