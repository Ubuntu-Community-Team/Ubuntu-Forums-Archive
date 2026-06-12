---
title: "Hard power off on shut down"
date: 2007-04-21
forum: General Help
---

### Post by soro2005 on 2007-04-21
I didn't find this on the board, but I also don't quite know how to describe/search for the issue.

Situation is as follows: I have a Toshiba laptop Feisty (upgraded from Edgy). Everything's fine, except one thing, which makes  me worry a little:

When I shut down Feisty, it goes down graciously, and then shuts off power in what to me sounds like too abrupt a way. Last thing before the laptop is off is a sound like something that spins spinning down really hard. I actually think it's the hard drive. It's the same sound I get when the laptop is unresponsive and I just kill it by shutting off the power with the power button. It seems to me that the power goes down before the laptop has completed its full shut down cycle.

All other Ubuntu versions I had installed on the laptop didn't cause this issue, and Windows XP also powers down without a sigh. Also, if I restart Feisty, instead of shutting it down, I don't get the issue.

I'd really like to solve this issue as I fear it might wear down my hardware quite quickly. But I don't have a clue where to look. :confused: :confused:

---

### Post by Alterax on 2007-04-21
Could it be the fan shutting down abruptly?  That would cause the loud spin-down sound but in reality it's very little to worry about.

--Alterax

---

### Post by nebhead on 2007-04-21
I have exactly the same problem but i did a fresh install of feisty. i have a acer travelmate 2420.
it sounds like the hard drive is stopping abruptly like it would if i was to kill my computer by holding in the power button.  anyone help?

---

### Post by mhansen on 2007-04-21
Here's a bug report on the issue, along with some possible workarounds.  You're not alone...

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810)


Regards,
Mike

---

### Post by soro2005 on 2007-04-21
Cool, thanks! Found it myself, and am just about to reboot to see whether the fix does it for me:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/comments/66](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/comments/66)

(extends a fix from a few posts up: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/comments/60](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/comments/60))

Also discussed here: [http://ubuntuforums.org/showthread.php?t=404977](http://ubuntuforums.org/showthread.php?t=404977)

---

### Post by luisglz on 2007-06-18
Hi. I have the exact same problem on my Toshiba Laptop. I'm new to Ubuntu and Linux in general, and this has been the SINGLE reason keeping me from running Ubuntu on my laptop. I've tried different distros (openSUSE and Fedora) but they all give me the same problem. 
I've been looking everywhere for information and found this website: [http://linux-ata.org/shutdown.html]("http://linux-ata.org/shutdown.html") which seems to tell its a bug on the kernel and says it's been fixed on version 2.6.22; but like I said, I'm new to all this and have no idea what to do to fix it.

I really hope the Ubuntu people get to fix this soon. I'd love to run Ubuntu on my laptop but I don't want to screw up my hard drive.;)

---

### Post by soro2005 on 2007-06-18
> **luisglz said:**
> Hi. I have the exact same problem on my Toshiba Laptop. I'm new to Ubuntu and Linux in general, and this has been the SINGLE reason keeping me from running Ubuntu on my laptop. I've tried different distros (openSUSE and Fedora) but they all give me the same problem. 
I've been looking everywhere for information and found this website: [http://linux-ata.org/shutdown.html]("http://linux-ata.org/shutdown.html") which seems to tell its a bug on the kernel and says it's been fixed on version 2.6.22; but like I said, I'm new to all this and have no idea what to do to fix it.

I really hope the Ubuntu people get to fix this soon. I'd love to run Ubuntu on my laptop but I don't want to screw up my hard drive.;)

It seems to be fixed for future kernel versions, but is unlikely to be fixed in Feisty as it requires some more extended tinkering. In the meantiime, the solution I've referenced above should do. Produce the two line script as described here: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/comments/60](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/comments/60) and place it as described here: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/comments/66](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/comments/66)

The entire bug report is here: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810)

By the way: It's just an emergency parking of the read and write heads. It sounds wild, but it's a procedure that's supported by the hard drive. Not saying it can't cause issues on the long haul.

---

### Post by tolstoybikeboy on 2007-06-18
hi, i was wondering if someone might write out this script or patch...whatever is needed to resolve this issue. i am a newbie to ubuntu and reading the links posted here that show workarounds; they might as well be greek to me. i am concerned about my hard drive. i am running fiesty fawn 7.04 64bit. when i shut down i get the same noise described;  the OS shutsdown nicely and shows the shutdown progress bar...but then immediately the machine cuts off..and the hard drive stop is quite loud...

the post from "Martin" shows some type of "patch"..yet i have no idea how to "simply write two lines ...." of script or such...

can anyone clarify the process for a new user?

my system is an Acer Aspire 5100 laptop    HDD brand is unknown under the device profile. IDE bus. 5400rpm 120gb 

kernel is 2.6.20-16-generic #2 SMP

---

### Post by soro2005 on 2007-06-18
Okay. You can do it as follows. I'll make the additional steps for more complex situations than you probably face gray, so it doesn't look that intimidating.

1.) First thing, you need to make sure you're applying the fix to the right disk. Disconnect all your external USB and other hard drives, or perhaps best whatever you have in terms of external storage devices, open a terminal, and type (or copy + paste)
```
ls /sys/class/scsi_disk
```
If the output is just 0:0:0:0, you're probably safe to skip directly to step 2. [color=gray]If you have  another of those series (I have 3:0:0:0 for instance), that's probably because you have another drive connected. To know which one's which, do
```
cat /sys/class/scsi_disk/0\:0\:0\:0/device/model
```
which should give you the name of the manufacturer and model of the drive you have there. Do the same replacing the 0:0:0:0 with the other series of numbers you've found in the step above (like "3" in my case). Did you know that, in a terminal window, you can always type in the first characters of a path, then hit the tabulator for autocompletion? That makes it so much easier, particularly when the backward slash enters the scene. Ok, that was an aside. Identify the hard drive in question. For me, it's the Toshiba. Make a mental note whether the drive you want to silence is the one with 0:0:0:0 in the path, or which one it is, and substitute the correct reference below in the next step.[/color]

2.) At your terminal type, or better copy + paste this:
```
sudo gedit /etc/init.d/hdd-shutdown-workaround
```
Provide your password. Provided that you've Ubuntu installed, as opposed to Kubuntu or Xubuntu, this should open Gedit (text editor) for the Super User. If you have Kubuntu or Xubuntu, replace "gedit" with the text editor of your choice. To paste into a terminal, push down the middle mouse button, or go through the menu of the terminal window.

To the file you've opened in Gedit (which should be empty, because you're just creating it), write (or copy and paste)
```
#!/bin/sh
echo 1 > /sys/class/scsi_disk/0\:0\:0\:0/stop_on_shutdown
```
That is the number one there behind echo, not the letter l! [color=gray]If, in 1.) above, you've found out that the hard drive in question is not 0:0:0:0, you have to substitute the correct string here. Each colon gets a backward slash in front of it. If you have another disk drive that's also being emergency parked, just copy and paste the second line again, and substitute the 0s with the series of numbers you've found out in step 1 above.[/color] Hit "Save" and close Gedit. This was step one from the first link. :-)

3.) Make the script you've created executable. At the terminal:
```
sudo chmod +x /etc/init.d/hdd-shutdown-workaround
```

4.) Now the soft-linking part from the second link: Back at the terminal, enter:
```
sudo ln -s /etc/init.d/hdd-shutdown-workaround /etc/rcS.d/S99hdd-shutdown-workaround
```
"ln -s" means "make a soft or symbolic link," then the file to be linked and the name of the link to be produced. If you want to know what's a symbolic link, use the internet search engine of your choice :-)

That should be it. If you want to make sure your symbolic link is in place, and the linked file looks ok, you can do
```
gedit /etc/rcS.d/S99hdd-shutdown-workaround
```
to open the thing again in Gedit, or use cat instead of gedit. You don't have to do that as superuser as you only want to see whether you've done it right, so you don't need write access.

Be ABSOLUTELY CAREFUL with upper and lower case, they DO VERY MUCH MATTER.

You may not see the change until after the next restart.

Hope that helps. :D

---

### Post by luisglz on 2007-06-25
Thanks a lot. It worked. :D

---

### Post by atlfalcons866 on 2007-06-25
this is happening on my edgy install. My harddrive makes a loud sound when it spins down.

---

### Post by soro2005 on 2007-06-25
I think that this should normally not be an Edgy issue. The one that's being solved by the steps described above, I mean.You may want to look through launchpad, or perhaps try it out. But I think that for me and others, the problem came up only with the Feisty kernels. You may have another issue.

---

