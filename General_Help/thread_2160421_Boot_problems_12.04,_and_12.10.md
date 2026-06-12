---
title: "Boot problems 12.04, and 12.10"
date: 2013-07-07
forum: General Help
---

### Post by feardotcom on 2013-07-07
I dont know what in the world is going on with my PC. First i have 13.04 installed on my dell laptop and it works great. I have had nothing but problems from my desktop. The funny thing is, back when 12.04 first was released i had no problems at all. But due to my Wifi Adapter not working on linux i was forced to go back to windows untill i could afford another one. Now i have another wifi card and i have nothing but problems with ubuntu. I first tried to install 13.04, live USB worked great, and i installed. Once i rebooted the computer would never boot into ubuntu, it would freeze at a black screen, sometimes make it to the purple screen but never load. The same thing happens in 12.10. And, actually the same thing happens in 12.04 from a fresh download from ubuntu. I had to go back to my original live usb i found back that was from the original launch of 12.04. I'm guessing it was video drivers, but i'm not sure.

Now, after i installed 12.04 i did the updates. Then the boot problems started where it freezes at a black screen with a flashing Dash. Sometimes, after about 5-10 mins the pc will go to a  screen with "Waiting for root deviced failed..." i will reboot. After that, most of the time, it boots fine. I usually have to reset the pc about 4-5 times before it boots.I was thinking of upgrading to 13.04, but im not sure if it will fix the issue. 

The issue is random and my pc will boot fine for days and then all of sudden do this and then start booting fine. So weird.

---

### Post by feardotcom on 2013-07-08
No answers? or even tips?

---

### Post by jdhoskins on 2013-07-08
I'm having a similar problem and haven't gotten any hits on my thread either.  Mine makes it to the splash screen, which flashes a couple of times, then goes black.

---

### Post by feardotcom on 2013-07-08
You dont perhaps have a Razor mouse do you?

---

### Post by BreezyBrooke on 2013-07-08
Is this a USB Wifi Stick by anychance? I found them to be somewhat troublesome in linux, like halting boot, shutting off durring use and more among other things. Internal cards work great by the way.

---

### Post by feardotcom on 2013-07-08
yes, my wifi adapter is usb. It's all i could afford atm.

---

### Post by efflandt on 2013-07-08
As long as WiFi works at all in Linux, that should not be an issue. Some USB WiFi devices admittedly only have Windows drivers, but if it worked at all without having to install special drivers, I doubt if that is the problem.

I had some intermittent issues before that turned out to be video card related. The first time I noticed it was when Win7 occasionally paused for awhile and said "Video driver stopped responding, recovered". Updating nvidia drivers or using default Windows driver did not help. I think that I had just installed 64-bit Ubuntu 11.10 at that time (the problem didn't seem to happen in 10.04 on another partition). That worked fine most of the time, but occasionally stopped accepting keyboard or mouse click input (mouse cursor would usually still move). It did not seem to happen while playing cpu/gpu intensive minecraft, most often in the desktop, sometimes after days and sometimes immediately after booting. Eventually I started having problems during boot and logs said something about nvidia hardware not responding. The card was a cheap Chinese (Galaxy) GT 430 and the glitches started happening about the time its 1 year warranty expired.

That may not be your problem. But it would not hurt to reseat your video card and reconnect cables just to make sure everything is making good contact.

I replaced my video with EVGA GTX 550 Ti (3 yr warranty) and no video/keyboard/mouse problems since (currently running 64-bit 12.04.2 reinstalled after replacing failing 3 yr old drive).

---

### Post by feardotcom on 2013-07-13
I upgraded to 13.04. I realized that my floppy driver was set to be on when i dont have a floppy drive. So i turned it off and now it boots every time it just takes 10+ minutes. I can turn the PC on and go make some tea and come back and it's justs getting to the login screen. Any ideas on the slow boot?

---

### Post by feardotcom on 2013-07-14
i take that back. I'm having more problems now than before. Is there any logs i can check and see whats going on?

---

### Post by feardotcom on 2013-08-02
Ok, so i checked the log and i noticed usb kept coming up. So i started playing around with the boot process and if i unplug EVERYTHING usb then it boots perfect. If i dont unplug everything then it hangs. If i unplug my wifi adapter and leave my mouse connected it hangs and then eventually boots. So it seems as if the usb devices are fighting for attention, so to speak.

---

### Post by feardotcom on 2013-08-03
Any Ideas? This is really getting annoying. It seems like when everything usb is unplugged it boots jut fine.

---

### Post by sioxs on 2013-08-06
> **feardotcom said:**
> Any Ideas? This is really getting annoying. It seems like when everything usb is unplugged it boots jut fine.

I've had issues to solve with booting this weekend as well (through no fault but my own ;) 
 "System boot fails to find root device."

/bin/sh: can't access tty: job control turned off
(initramfs) _ 

I know the thread started with different circumstances (usb and other devices causing hangs) so I thought you might try this method to solve your boot problems .. (well most anyway so long as it's not faulty hardware issues and will rule out Linux as the culprit with any luck)

The process of booting is hardware specific and needs the correct instructions to work properly.
Most boot problems are ether misconfiguration issues or missing modules and the proper drivers for your hardware.
An easy fix is to rebuild the image called when the system boots.

This can be difficult with a broken system since you need at least a terminal and a working shell to preform such a task.
Thankfully there are ways around this - that is what I have done and would like to share.
[URL="http://www.supergrubdisk.org/rescatux/"]
Rescatux[/URL] is a great Live recovery tool. Use it to restore grub or load your OS into a embedded state to preform maintainance.
Install it to a USB or CD and boot into it from there.
From rescatux you can launch a terminal and chroot into your OS and recompile init (do this only if you can't load your OS directly)
If you have the patience to wait for your system to boot up you can update the kernel once your logged into your user space.
The very first thing you want to do is back up your system settings in case you screw up. 
Switch to a root shell
$ sudo -i
cd to your destination directory
# tar cvzpf  /media/[backup-drive]/local-backups/home.tar.gz /home
later you can restore your home directories with
# cd /to/archive/directory
# tar xvpf somewhere/home.tar.gz //automatically installs from the root path
If you want to keep the system state of the entire partition use a tool like "partimage" (the partition must be unmounted to preform this type of backup.)
Again the use of Live Systems like [Knoppix]("http://www.knopper.net/") works great for this purpose and comes with partimage.
Now you can make system changes without fear (or at least get your system back to the way it was before you started messing with it.)

If you are able to login to your problematic system try to restore init from there first and see what happens when you boot again with recovery mode and check "dmesg" for strange behaviour and don't forget the kernel log.

To rebuild the boot sequence follow these steps:
Open a new vt 
# ls -l -s bash   // note the '#' you must be root to do this
Shutdown the window manager
# service [gdm | kdm | xdm] stop  //whichever you use
On some machines switching to run level three does this automagically
# init 3
1. $ sudo update-initramfs -u   // this rebuilds the default image only, if you have others use the -k switch
2. $ sudo update-grub  
reboot

In the case where you can't login to your account you can try a live disk and chroot into the machines partition to preform the above tasks.

From a Live session:
Open a terminal

1. Create the mount points and chroot environment
$ sudo mount /dev/sda[partition-of-OS] /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sysfs /mnt/sys && sudo mount /dev/pts /mnt/dev/pts && chroot /mnt

2. Load any additional modules you might need
# sudo modprobe loop && sudo modprobe des  // loads loop devices and encrytion

3. Add initctrl functions
chroot:/# dpkg-divert --local --rename --add /sbin/initctl && ln -s /bin/true /sbin/initctl

4. swap the root device
# sudo  pivot_root . old-root

5. cd into the new root
# cd /
At this point you should see your fstab entries in /etc
# cat /etc/fstab
If everything went ok do:
# mount -a   // load remaining devices from fstab
From this point you could attempt updating the initramfs and grub as discribed above.

# reboot or # shutown -r now
Your Done!
cross your fingers and you might have it. If not check the logs and in the worst case senerio restore from the backup you made earlier.

Cheers!
sioxs
[I]"if we did all the things we are capable of doing we would literally astound ourselves"



[/I]

---

