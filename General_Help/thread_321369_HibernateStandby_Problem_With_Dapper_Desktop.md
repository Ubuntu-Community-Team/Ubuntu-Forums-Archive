---
title: "Hibernate/Standby Problem With Dapper Desktop"
date: 2006-12-18
forum: General Help
---

### Post by linux4me on 2006-12-18
I am an Ubuntu noob, but I have gotten Dapper 6.06 LTS installed and have all my hardware working; however, I haven't been able to get the machine to wake from hibernation or suspend. It went on Standby in Windows XP (after XP had been out for about four years and they released a patch for such issues), and the BIOS is ACPI capable.

First, here's the hardware involved:
Albatron KX400-8XV Pro (v.1) with the R1.01 BIOS (latest non-beta)
PNY Nvidia MX 420 AGP video (using the latest nvidia-glx drivers)
Intel 536EP internal modem
Western Digital WD800J EIDE hard drive
HP Photosmart C3180
HP Scanjet 2200C
Microsoft Internet Explorer Mouse running via PS/2

Next, here's what happens:
I only have a hibernate button in gnome, but when I click it the machine shuts down appropriately without any errors. When I try to wake it up, it gets to the "OK, booting the kernel" line and then hangs. There is no video output after about 15 seconds. I have to push the reset button to restart it.

At the login screen, I have both a hibernate and suspend button. The hibernate button has the same results as the command in gnome. The suspend button puts the machine in standby, on resume it appears to start back up but there is no video output, ever. A hard restart is again necessary.

Here's what I've tried:
[LIST=1]
[*]I booted from the Live CD, but it has no hibernate or suspend options, so that was a bust.
[*]I set the only ACPI option in the BIOS from "S3"--where it was--to "S1&S3". It made no difference.
[*]I disabled ACPI and enabled APM by modifying my /boot/grub/menu.lst, updating grub, modifying /etc/modules, and adding a file in /etc/modprobe.d as described here on the forums. and couldn't resume from hibernate that way, either. 
[*]I have verified that acpi and acpid are installed. When I run the command "cat /sys/power/state" I get "mem disk".
[*]I have read every article in the forums with "suspend" and "hibernate" in them, but only found one that was similar to my situation, and there have been no definitive responses to it. ](*,) 
[/LIST]

I would welcome any suggestions as to where to go from here. I thought about upgrading to Edgy, but being such a noob, I'm thinking I would be better off staying with Dapper for now if possible. As I said, I have everything else working, so maybe the best I can hope for is to just get used to saving all my work and shutting down when I'm going to be away from the PC for a while, but I'm not quite ready to give in.:-?

---

### Post by Rippey on 2006-12-18
do you have a swap partition?
to use hibernate you will need a swap file that is atleast the same size as your ram.

---

### Post by Dubbayoo on 2006-12-18
Does the swap file have to equal the amt of ram in the system or the amt in use?

---

### Post by Rippey on 2006-12-18
amt in the system

---

### Post by linux4me on 2006-12-19
When I go into Disks Manager and click the Partitions Tab, it lists a Swap Partition that is 2.8 GB in size, and I have 1 GB of RAM. All the buttons for it--Format, Create, Delete--are inactive, but it looks like I have one and it is the right size if I am interpreting it correctly...

---

### Post by nmincone on 2006-12-19
Your issue is not new, STF for additional information regarding suspend/hibernate issues in Linux.

---

### Post by linux4me on 2006-12-19
Nmincone, I appreciate you taking the time to read my post, but as I said in the original post, I have searched the forums for others with this particular issue, and though I found many threads about suspend/hibernation issues, I wasn't able to find any that experienced the hang right after the "booting the kernel" line.

---

### Post by linux4me on 2006-12-21
I finally got suspend and hibernate working. Nmincone was right; the answer was in the forums/wiki, but I was not trying the answers that were for laptops thinking I would get into trouble, and the answer came from a solution for a laptop.

The other thing that was confusing me was that with hibernate, my system appeared to hang right after the "OK...loading the kernel" line, and I was expecting all the other lines to print out after that and a normal boot having never seen hibernate work before. I know now that it's working that there are no subsequent lines on this machine, Right after the "OK...loading the kernel" line, the GUI (gnome, in my case) pops right up when things are working correctly.

Keep in mind that this is a fix for a system with an nVidia video card running the nVidia drivers in Dapper 6.06 LTS. I don't know what the effects would be trying it on another system.

Here's the solution that worked with my hardware in newb-format:

Open a terminal window (Applications, Accessories, Terminal) and open /etc/X11/xorg.conf for editing by typing the following and hitting Enter:
```
sudo nano /etc/X11/xorg.conf
```

Go to the "Device" Section. Mine looked like this before the change:
```
Section "Device"
        Identifier      "NVIDIA Corporation NV17 [GeForce4 MX 420]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection

```

Add the line 'Option          "NvAGP"       "1"' so it looks something like this:
```
Section "Device"
        Identifier      "NVIDIA Corporation NV17 [GeForce4 MX 420]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "NvAGP"       "1"
EndSection

```

Press Ctrl+O to save the file, then press Enter to use the existing file name. Press Ctrl+X to exit nano.

Now edit the /etc/default/acpi-support file using nano:
```
sudo nano /etc/default/acpi-support
```

Go to the section that looks like this:
```
# Uncomment the next line to enable ACPI suspend to RAM
#ACPI_SLEEP=true

```
If there is a '#' in front of "ACPI_SLEEP=true, delete it to uncomment that line.

Now move down to the section that looks something like this:
```
# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true
```
If your POST_VIDEO setting is set to "true", change it to false so it looks like this:
```
# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false
```

Press Ctrl+O to save the file, then press Enter. Press Ctrl+X to exit nano. Type 'exit' in terminal to close it.

Finally, I had a Hibernate button in my shutdown screen, but no Suspend button. If you want to add one, it's easy to do.

Press Alt+F2. Type "gconf-editor" (without the quotes) and hit Enter. Navigate to /apps/gnome-power-manager. Make sure that can_hibernate and can_suspend are checked. Click File, Quit. 

Now you should have both the Hibernate and Suspend buttons on the shutdown screen, and if you're lucky, they'll work!

---

### Post by nmincone on 2006-12-21
I'm glad you found your solution! Excellent, and great post.
Everyone with suspend/hibernation problems, this might help....

[Search this thread for clues...]("http://ubuntuforums.org/showthread.php?t=284994")
[How to suspend and hibernate a laptop under Linux]("http://www.linux.com/article.pl?sid=06/05/24/1716222")
This is a real problem that needs real solutions. Supporting hardware for suspend/hibernation is tricky business and could use some polishing in Linux. There's no magic bullet (at the moment).

---

