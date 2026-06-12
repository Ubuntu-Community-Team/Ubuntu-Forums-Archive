---
title: "Ubuntu does not load. Freeze before GUI..."
date: 2007-06-16
forum: General Help
---

### Post by ofir_k on 2007-06-16
Hello,

Two days ago, I connected an HD (so now I have two...), I checked that it was booting and since then I didn't boot again into Ubuntu but to XP placed on the second HD.

Now, when I am booting Ubuntu, it loads and after the progress bar in the load screen disappears, I get nothing except a black screen.

I didn't searched the forums since I need this computer in S.O.S and I don't have time right now to search the forums...

Regards,
Ofir

---

### Post by merlinus on 2007-06-16
This may help:

[http://ubuntuforums.org/showthread.php?t=474734&highlight=two+hard+drives](http://ubuntuforums.org/showthread.php?t=474734&highlight=two+hard+drives)

-merlin

---

### Post by ofir_k on 2007-06-16
I already followed this guide when I wanted to configure grub to boot windows XP.

But now, I can boot Ubuntu but I don't see the login screen, instead I just get a black screen.

---

### Post by ofir_k on 2007-06-17
Someone knows how to solve this problem? Someone has an idea?

I will describe the problem again:

In the beginning, I had only one HD with Ubuntu 7.04 installed. Ubuntu worked fine and everything was great!

Then, my second computer which has the same HD (SATA...) with Win XP installed, died suddenly. So, because I still wanted to be able to work on XP, I plugged the HD from the second computer in my first computer which has Ubuntu 7.04.

After I edited grub to dual boot Ubuntu from the first HD and Win XP from the second one (like described [here]("http://ubuntuforums.org/showthread.php?t=474734&highlight=two+hard+drives")), and then I worked couple of days on XP, when I tried to boot Ubuntu again, it just loads as usual (with the nice orange progress bar), and then, instead of displaying the login screen, it just shows a black screen.

When I try to boot in recovery mode, I can get to the command line. but I don't know what to do to fix this problem.

Ofir

---

### Post by Nehvrook on 2007-06-17
I've seen a problem like this before, but it had nothing to do with a second hard drive. In my case I'd updated the graphics drivers and they couldn't decide if they should use the AGP or PCI port on my motherboard. They chose the wrong one and after I got past the loading bar I just got a black screen.

I fixed it by putting 

Option         "NvAGP" "1"

into the graphics card Device section of my xorg.conf

Did you happen to update any graphics drivers last time you used Ubuntu?

---

### Post by ofir_k on 2007-06-17
Thanks for your reply.

I really don't remember if I updated my drivers. Maybe just updated the linux kernel from the Update Manager.
I also disabled my Conxent HSF modem driver, if that has a connection to the problem...

I will try to follow your advice and I will post the results.

Thanks.

---

### Post by Nehvrook on 2007-06-17
If you're using an Nvidia graphics card, your xorg.conf should look something like this

```


Section "Device"
    Identifier     "nVidia Corporation N43 [GeForce 6600]"
    Driver         "nvidia"
EndSection


```

Try booting into recovery mode, and editing your xorg.conf to change "nvidia" to "nv", if this is a graphcis drivers problem that should let you get back into Ubuntu untill you can fix whatever was wrong with the other drivers.

Of course all of this will only work if your problem has something to do with graphcis drivers, but your symptoms were exactly the same as mine so it might be.

---

### Post by Crakie on 2007-06-17
In the Grub menu, manually edit the kernel parameters and remove the ' quiet'  and 'splash' options. Hopefully you'll get a clue as to what is going wrong from the resulting output while booting.

---

### Post by ofir_k on 2007-06-17
Crakie: I did what you said but there is not enough time to read the messages...

Nehvrook: I followed your instructions (I have an ATI card but still...) and it doesn't help.

Is there a way to backup files over a Samba network? (I think that it would be faster to reinstall Ubuntu then repairing it...)

---

### Post by ofir_k on 2007-06-17
Please ignore the last post...

I managed to enter the GUI by booting in recovery mode, running:
```
dpkg-reconfigure server-xorg
```
(Or something like that...)
And then I selected vesa in the first screen and in the second one I just pressed Enter.
Then I reboot and the I again can use the GUI.

But... everything is messed up since the graphic driver of ATI isn't loaded...

Someone knows about a problem with the ATI drivers? (I use the one from the "Restricted  Drivers Manager" which is now "not in use")???

---

### Post by Crakie on 2007-06-20
By selecting Vesa, you went back to the generic video driver. You have to reinstall the Ati-drivers.

---

