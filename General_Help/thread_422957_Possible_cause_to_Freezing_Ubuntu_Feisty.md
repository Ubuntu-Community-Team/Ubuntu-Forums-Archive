---
title: "Possible cause to Freezing Ubuntu Feisty"
date: 2007-04-25
forum: General Help
---

### Post by KrazyPenguin on 2007-04-25
Here is a possible cause to the freezing:

I never had a problem with other kernels, so I assumed it was kernel related.

check /var/log/messages

I found this in the log:

Apr 24 20:50:31 laptop kernel: [   25.499099] PCI: Bus #05 (-#08) is hidden behind transparent bridge #04 (-#05) (try 'pci=assign-busses')
Apr 24 20:50:31 laptop kernel: [   25.499102] Please report the result to linux-kernel to fix this permanently

The solution is to add pci=assign_busses to your kernel at boot.

Here is a link:
[http://lists.infradead.org/pipermail/linux-pcmcia/2006-April/003518.html](http://lists.infradead.org/pipermail/linux-pcmcia/2006-April/003518.html)
from last year

I'm not sure if this will fix it, but if the buses are assigned wrongly, this could cause a hardware failure.

Let me know if this works for anybody.

Thanks

---

### Post by KrazyPenguin on 2007-04-25
I haven't tried the fix yet cuz I turned 3d effects off, and want to see if it freezes again.

It hasn't so far, but anyway, here is the Bug submitted by somebody else, so maybe I really am on to something here:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/108860](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/108860)

:shock:

---

### Post by KrazyPenguin on 2007-04-25
This is for an asus motherboard, i use intel but....

 ‘pci=assign-busses’

The ‘pci=assign-busses’ option is somehow required. Without it you may experience system freezes or hardware malfunctions. 

with a link:
[http://gentoo-wiki.com/HARDWARE_Asus_A6T#.E2.80.98pci.3Dassign-busses.E2.80.99](http://gentoo-wiki.com/HARDWARE_Asus_A6T#.E2.80.98pci.3Dassign-busses.E2.80.99)

Let me know if this works for anybody.

Thanks.

---

### Post by KrazyPenguin on 2007-04-25
With 3d effects OFF I still freeze but not as often.

Interesting nobody else gets this error!!! :confused:

Must be just me.

Anyway, I edited my grub and added pci=assign-busses

and I will just have to wait and see what happens.

---

### Post by KrazyPenguin on 2007-04-26
It's amazing nobody else has had these errors and experienced this freezing !?!!??

I feel that this post that i started is the closest thing to "what is going on" with this freezing, compared to the other two dozen posts, yet nobody posts.

Maybe I'm out-of-line, off track, or losing my mind or something :confused: 

Anyway here is yet another link:

    	[https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=229603](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=229603)

and i do believe the new kernel will fix this problem.

It seems to have something to do with connecting to the internet and cpu frequency, resulting in random lockups.

I'm not sure how to update my kernel.

Any ideas!?!?!?

Thanks.

---

### Post by 13013kid on 2007-04-26
Not sure if this helps anyone else.....had my first freeze-up within 24 hours of initial clean install.  I attempted to reintall and on three subsequent attempts first boot froze within 15 minutes.  What I changed to stop the freezes from all I culled out of the many, many posts on this subject was:  I removed my pci wireless card (was having trouble finding a RT61 inf anyway) and I attached a ps2 adapter to my wireless usb ms mouse.  It has been fine for 10 hours now.  Like I said, not sure if this helps anyone, but it does add credence to the pci=assign-busses solution.

---

### Post by iopo on 2007-04-26
Hi KrazyPenguin!

I have the same problem and I posted it here

[http://ubuntuforums.org/showthread.php?t=412125](http://ubuntuforums.org/showthread.php?t=412125)

but nobody seemed to have a clue!

Just a question: where should I find these two lines

Apr 24 20:50:31 laptop kernel: [ 25.499099] PCI: Bus #05 (-#0 is hidden behind transparent bridge #04 (-#05) (try 'pci=assign-busses')
Apr 24 20:50:31 laptop kernel: [ 25.499102] Please report the result to linux-kernel to fix this permanently 

to see if it's the same problem?

Thanks


Edit: I found it! gedit /var/log/syslog and I have exactly the same two lines! I'll add the command to the kernel at boot and I'll let you know

Thanks a lot!

---

### Post by dagrump on 2007-04-26
What the hell, I'll buy in and try it. I'm open to about anything short of use the dreck from Redmond. I've edited grub & added pci=assign-busses, I'll see what happens.

---

### Post by dagrump on 2007-04-26
well I thought you might of slain the the dragon, but 3 quick crashes seems to say this isn't the issue w/ this brick. Please post any other ideas though. For now I'll use my under power test box to run firefox, it must be to puny to crash.

---

### Post by KrazyPenguin on 2007-04-26
> **dagrump said:**
> well I thought you might of slain the the dragon, but 3 quick crashes seems to say this isn't the issue w/ this brick. Please post any other ideas though. For now I'll use my under power test box to run firefox, it must be to puny to crash.

Do u have 3d effects on???

With 3d effects off and adding that line makes the system much more stable, at least for me.

I recompiled my kernel (the new one 2.6.21), but can't really test it cuz i can't connect to the wireless when i boot. It seems the restricted driver packages are missing for 2.6.21 probably cuz they don't exist yet??

Will Feisty be upgraded to the new kernel or do we have to wait for Gutsy??

---

### Post by dagrump on 2007-04-26
I didn't reload beryl & I've reverted to Edgy. I had a dvd playing, firefox open, & trying to install xubuntu in virtualbox, only using 20% of the cpu & 15% of the ram, it should have ate it like cake, but alas it turns into a paperweight.
I should say peak cpu usage of 20%, oh I jumped to the test box it does not seem to have any lock up issue. Of course I have a p3 running xubuntu & it would be fine fro most folks.

---

### Post by iopo on 2007-04-26
Guys, this is NOT working for me! After editing the kernel option my computer was not able to boot anymore! It was booting very slowly and finally it was hanging on "saving VESA state".
I had to restart it in safe mode and edit the grub list again.

---

### Post by benner on 2007-04-26
i found this.  somehow don't see the lin to the bug but could it be a network card issue?

[https://answers.launchpad.net/ubuntu/+question/5157](https://answers.launchpad.net/ubuntu/+question/5157)

---

### Post by Jasper84 on 2007-09-11
Gah these random crashes are pissing me off! My random crashes are mostly straight-to black screen and cpu off. Although one crash rebooted it and a few froze screen. (This is different from what i read, that people had "vertical ubuntu bars", or "white screen with horizontal black lines.".

People that i have seen having trouble with random crashes also seem to have differing hardware, but mine is in the attachment anyway. ( "lspci > Jasper84-lspci.txt" )
It also seems not to depend on specific applications.

I tried the solution provided here, it did not work here. (edit /boot/grub/menu.lst to add argument to call to kernel, right?)

If someone has seen the solution can he/she link here?(much of the discussion seems to go back to a while ago..) It seems to me that it is the kernel, how do i up/downgrade that.  "sudo apt-get upgrade" seems to keep that back?
"The following packages have been kept back:
  linux-headers-generic linux-image-generic linux-restricted-modules-generic"

BTW I just had to retype this because of one of the crashes :(

---

