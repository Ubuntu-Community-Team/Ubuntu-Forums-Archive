---
title: "A couple of odd little glitches"
date: 2007-10-30
forum: General Help
---

### Post by Riverglen on 2007-10-30
I have Ubuntu installed on two machines, both of which are connected to the same network router.  Both installations work very well, but there are a couple of differences that I am wondering about.  First, on the older of the two machines, I don't get an automatic connection to my wired network.  I have to go to the network applet in the task bar and select "wired network" to get connected.  The interesting thing is that when updates are available, I get the notification before I get a chance to make the manual connection.

The second little problem is that whenever the older system displays a progress bar, the progress is displayed in the same white color as the background in the bar, so the only indication that the bar is advancing is that the text in the bar is progressively erased.  Not much of a problem, but a little strange.

Finally, somewhere along the way when updating both systems, the Grub boot menu wound up showing two generations of the kernel.  Two options for the Generic mode and two for the Recovery Mode.  I have this on both systems, the newer of which I just upgraded to 7.10.  Is there any reason not to edit the Grub menu file to delete the older of the two option?  In the case of the system I upgraded to 7.10, I have kernel 2.6.22-14 which won't boot properly, and 2.6.20-16 which seems to work fine.

---

### Post by jimrz on 2007-10-30
> **Riverglen said:**
> I have Ubuntu installed on two machines, both of which are connected to the same network router.  Both installations work very well, but there are a couple of differences that I am wondering about.  First, on the older of the two machines, I don't get an automatic connection to my wired network.  I have to go to the network applet in the task bar and select "wired network" to get connected.  The interesting thing is that when updates are available, I get the notification before I get a chance to make the manual connection.

The second little problem is that whenever the older system displays a progress bar, the progress is displayed in the same white color as the background in the bar, so the only indication that the bar is advancing is that the text in the bar is progressively erased.  Not much of a problem, but a little strange.

Finally, somewhere along the way when updating both systems, the Grub boot menu wound up showing two generations of the kernel.  Two options for the Generic mode and two for the Recovery Mode.  I have this on both systems, the newer of which I just upgraded to 7.10.  Is there any reason not to edit the Grub menu file to delete the older of the two option?  In the case of the system I upgraded to 7.10, I have kernel 2.6.22-14 which won't boot properly, and 2.6.20-16 which seems to work fine.

I have had the progress bar issue using the default "human" theme on 2 different older machines with very low spec video capabilities and found that switching to a lighter theme ( Clearlooks is one I like and several other of the themes in the default install work, as well) solved the problem.

The additional kernels showing in GRUB were added when you got a new kernel from update manager. If you don't like looking at them, you can 
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup 
```
jic yuo need to repair or restore it, then
```
sudo gedit /boot/grub/menu.lst
```
and either delete or, better yet in case you should ever need to boot the older kernel, comment out the lines pertaining to the older one.

---

### Post by Riverglen on 2007-10-31
Thanks for the reply.  I tried another theme, and it solved the progress bar problem for me too.  It's kind of odd that the only display problem I had with the default theme was the progress bars.

I did edit out the unwanted Grub menu entries.  My only concern was whether there is any value to being able to boot to an older version.

I'm still looking for an answer to why I have to manually enable my connection to my network, but it certainly isn't much of a hardship.  I would like to know how the notification of available updates gets through before I establish the connection.

---

