---
title: "How to get photos off an iPhone 3 (Ubuntu 10.04)?"
date: 2012-12-31
forum: General Help
---

### Post by juliarain on 2012-12-31
I want to get the photos off an iPhone 3. I am using Ubuntu 10.04. When I plug it in via the USB port, the phone buzzes but nothing happens on the computer. 

[This thread]("http://askubuntu.com/questions/27141/nothing-happens-when-i-connect-my-iphone-3g-to-my-laptop") suggested adding a repository that would upgrade your libimobiledevice package. I did that and it still does nothing when I plug it in. 

I tried following [these instructions]("http://www.ubuntugeek.com/ipod-touch-3g-sync-over-usb-without-jailbraking-in-ubuntu-karmic.html") on Ubuntu Geek. It couldn't find the package libiphone-utils, but I continued with the instructions and tried to mount the phone anyway. This is what happens when I try to mount it: 

```
$ ifuse /mnt/ipod
Failed to connect to lockdownd service on the device.
Try again. If it still fails try rebooting your device.

```

Any ideas for what I can do? I'm just using this phone as a camera.

---

### Post by sudodus on 2012-12-31
This is a last resort, but anyway:

Is there a removable [micro]flash card? In that case, move it into a card reader (with an adapter, if the card reader only reads standard size cards).

---

### Post by chadk5utc on 2012-12-31
unfortunately the iphone memory is built in not removable. Does your phone not show up as a removable drive?

---

### Post by juliarain on 2012-12-31
sudodus - All it has is a SIM card. 

chadk5utc - It doesn't register at all when I plug it in, at least on the computer's end. 

I know it can be detected and accessed in newer versions of Gnome/Linux. I'm using Ubuntu 10.04 with old gnome now, but I have tested newer versions of Ubuntu on this computer. I just kept having all these problems with slowness and freezes, and no one knew what the problem was, and I will have to research kernel dependencies to figure it out, which I have no idea how to begin doing, so I decided to just switch back to the old system that worked (Ubuntu 10.04).

---

### Post by Lars Noodén on 2012-12-31
This is just a guess but do you have HFS+ support installed on your computer?  If the iPhone is like the iPod I used to use, then adding HFS+ support allows you to mount it as an external drive.  See the packages hfsplus, hfsutils and hfsprogs.

---

### Post by WasMeHere on 2012-12-31
You just told us the solution ;-)

Boot from the newer Ubuntu install disk or if you have problems, download the iso files of Lubuntu 12.04 and Knoppix.

Make CD/DVD/USB drives and run a live session, to connect to your iPhone and copy the photos. There is a fair chance that either Lubuntu or Knoppix will work well enough for this task.

If necessary, try some boot option in Lubuntu alias cheat-code in Knoppix

[[COLOR="Red"]https://help.ubuntu.com/community/BootOptions[/COLOR]]("https://help.ubuntu.com/community/BootOptions")

---

### Post by juliarain on 2012-12-31
Lars Noodén - I installed hfsplus, hfsutils, hfsprogs, and hfsutils-tcltk, but that didn't help it automount. I don't know what to do if it's not even registering the device. 

This [community documentation on portable devices]("https://help.ubuntu.com/community/PortableDevices/iPhone#Ubuntu_10.04_Lucid_Lynx:_Support_out_of_the_box") says Ubuntu 10.04 is supposed to connect to an iPhone automatically. I don't understand why it's not doing it. 

Olle Wiklund - I could solve all my problems by restarting the computer and booting into Windows, but that's no fun. The idea is that I want to access the photos without rebooting or using a virtual machine. Also, I'm skeptical that a lightweight system would really help - I tried running the latest Xubuntu on this laptop and it still had the same freeze problem. Thanks for the suggestion though.

---

### Post by sudodus on 2012-12-31
> **juliarain said:**
> The idea is that I want to access the photos without rebooting or using a virtual machine.

Yes, I understand. I didn't know you are dual booting with Windows.
> 
Also, I'm skeptical that a lightweight system would really help - I tried running the latest Xubuntu on this laptop and it still had the same freeze problem. Thanks for the suggestion though.
Maybe it is worth trying some light-weight system after all, using only default graphics drivers. If you don't think Lubuntu will do it, at least try Knoppix, which is famous for excellent recognition of and cooperation with hardware, also aging hardware. Knoppix is designed to run live (or persistent live) and it boots really fast, several times faster than Windows, particularly if you have a fast USB pendrive.

*Edit*: April 2013 is end of life of Ubuntu 10.04 LTS. No more security updates except for the server edition (without graphics). So you will soon need something new for the computer anyway. You might as well [s]start[/s] continue testing now.

---

### Post by juliarain on 2012-12-31
Thanks, sudodus! I will look into Lubuntu. The thing is, my computer is only two years old ([specs]("http://www.laptop-spec.com/?p=319")). The main problem with newer versions of Linux was that it would freeze and be totally non-responsive if the screen-brightness adjustment keys were pressed too rapidly, but the newer systems also seem to take a really high toll on CPU usage. For example, the CPU usage in Linux Mint was always hovering at around 50% (resting); I took a screenshot of CPU usage in the system monitor while I was performing a file search in Nautilus, and each thread would keep maxing out. I have run MemTest and I don't think anything is wrong with the machine. Windows is running fine, especially since I upgraded the RAM. I bought this thing refurbished, so I guess it's possible that it has some sort of inherent hardware issue. Or maybe I just have unreasonable expectations for how fast Linux should be.

---

### Post by sudodus on 2013-01-01
I'm surprised that your system freezes. The specs look OK, for example Intel graphics usually work very well with Ubuntu. I don't know about the mobo. I don't know about the wifi chip, it says only 'yes' in the specs. If you search for it in the computer, maybe someone can recognize it and tell us if there are issues with that chip. Look for 'network' and or 'PCI controller/network' with ***hardinfo*** or
```
gksudo lshw | less
```

Have you tried with some boot option?

[https://help.ubuntu.com/community/BootOptions]("https://help.ubuntu.com/community/BootOptions")

---

