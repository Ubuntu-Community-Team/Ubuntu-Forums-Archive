---
title: "Unmountable Internal Hard drive"
date: 2017-06-16
forum: General Help
---

### Post by piby on 2017-06-16
Hi everyone!

I am a newbie here. So please bear with me.

I have Ubuntu 16.04.2 LTS (Gnome) installed on my system. No other os is installed besides it. I left my laptop on last night. Unfortunately, the battery drained out and it automatically closed. Today morning, I powered it on and tried to start it and saw the message "No bootable device found. Please insert a bootable device and press any key". I inserted live cd and tried it to check.[ATTACH=CONFIG]275655[/ATTACH]

File manager shows "Ubuntu 16.04.2 LTS amd64" but unable to mount it.

I tried GParted and it detects the drive and shows error.

Disk Utility and Testdisk does not even detect the volume.

[https://ibb.co/iaXj3Q](https://ibb.co/iaXj3Q)
[https://ibb.co/eZfhq5](https://ibb.co/eZfhq5)
[https://ibb.co/nkzLck](https://ibb.co/nkzLck)


I don't want to format it as I have important documents in it. Please help me how to recover my data from there. I am freaking out.
Many thanks

---

### Post by ajgreeny on 2017-06-16
From your pictures it is not possible to see what you think should be on that disk and therefore it is difficult to know what to suggest you do to recover your data.

There are no ext4 partitions and nothing at this stage that appears to be Ubuntu partition, damaged or not.  Is the shown disk size at 128GB correct and what you would expect? What partitions do you believe are on that disk, as nothing at present makes any sense?

---

### Post by piby on 2017-06-16
I had earlier installed ubuntu by completely wiping out my system. My internal hard disk is 1 TB. I have not made any partition after that or even touched it. Since the sum here is not 1 TB, I would guess gparted is not fully detecting it?

---

### Post by piby on 2017-06-16
Also, on startup, if I press F2 and  go to Bios Setup > Information, it shows Hard Disk > [Not Detected].
I do not know much about it but I am trying to provide every info that might help. 
Please help me! I need my data!

---

### Post by ajgreeny on 2017-06-16
OK, let's see if we can find out what is already on your system.

See **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script on a live USB system.	 
**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system and may give us some more useful info.

---

