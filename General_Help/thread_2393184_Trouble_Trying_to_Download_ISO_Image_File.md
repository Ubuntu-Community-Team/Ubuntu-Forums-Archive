---
title: "Trouble Trying to Download ISO Image File"
date: 2018-05-30
forum: General Help
---

### Post by lawrence-joy on 2018-05-30
I am trying to download the ISO image file of Ubuntu 18.04 LTS to a USB stick. I am following the online instructions and am at step 3 "Launch Startup Disk Creator". We're going to use an application called 'Startup Disk Creator' to write the ISO image to your USB stick. This is installed by default on Ubuntu, and can be launched as follows: 1. Insert your USB stick (select 'Do nothing' if prompted by Ubuntu) [I already have an 8 GB empty USB stick mounted]. 2. On Ubuntu 18.04 and later, use the bottom left icon to open 'Show Applications'. [Bottom left icon is NOT "Show Applications", it is the USB stick that I have plugged in.]

I do have a problem with my 18.04 LTS install. The "kubuntu" screen comes up for about 2 s and then goes to the Ubuntu GUI screen. The Ubuntu GUI screen comes on for about 5 s and then a small screen opens and asks for password. I enter my password and the small screen goes away so the Ubuntu GUI screen is completely visible. After about 5 s this scenario repeats. I can get to the console by entering "Ctrl+Alt+F2". What are the terminal commands to enter to accomplish what I am trying to do?

---

### Post by The Cog on 2018-05-30
Firstly, don't mount the stick. I think the kernel will prevent rewriting the stick contents fully (especially the partition table) if it is mounted.

This should download the image file:
```
wget http://releases.ubuntu.com/18.04/ubuntu-18.04-desktop-amd64.iso
```

Use this command to work out which device is the stick - I guess /dev/sdb or higher (NOT sda) On my desktop it's always /dev/sdg. 
```
sudo parted -l
```
If you're not sure, post the output here and don't go on to the next step.

Write the downloaded file to the stick using the following commands. Replace sdx with the device id you worked out above:
```
sudo dd if=ubuntu-18.04-desktop-amd64.iso of=/dev/sdx bs=1M
sync
```
Don't unplug the stick until sync returns to the command prompt. You are wating for the OS to finish writing to the stick.

---

### Post by lawrence-joy on 2018-05-31
Here is what I got when I entered the Code: 'wget [http://releases.ubuntu.com/18.04/ubuntu-18.04-desktop-amd64.iso](http://releases.ubuntu.com/18.04/ubuntu-18.04-desktop-amd64.iso)' with no USB stick mounted.
--2018-05-31 22:05:29--  [http://releases.ubuntu.com/18.04/ubuntu-18.04-desktop-amd64.iso](http://releases.ubuntu.com/18.04/ubuntu-18.04-desktop-amd64.iso)
Resolving releases.ubuntu.com (release.ubuntu.com)... 91.189.88.166, 2001:6b0:e:2018::1337
Connecting to release.ubuntu.com (releases.ubuntu.com) |91.189.88.166| :80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1921843200 (1.86G) [application/x-iso9660-image]
ubuntu-18.04-desktop-amd64.iso: Permission denied

Cannot write to aCyubuntu-18.04-desktop-amd64.isoaCO (Permission denied).

Anything further??

---

### Post by PaulW2U on 2018-05-31
Reading both of your posts it seems that you are trying to download the ISO file directly to the USB stick. Is that correct? If not, to where are you downloading as you have "Permission denied" errors?

You need to download to your hard drive, I suggest ~/Downloads, and then use USB Creator or the commands given above to write the image to the USB stick.

---

### Post by sudodus on 2018-06-01
+1 to the advice by @PaulW2U.

[hr][/hr]
Which version of Ubuntu or Kubuntu are you running, when you try to download the iso file (16.04 LTS, a newer or older version)?

I am asking because a new and robust version of the Startup Disk Creator was introduced with 16.04 LTS. If you run an older version, for example 14.04 LTS, you had better use another tool, for example **Disks** alias gnome-disks (which is bundled with Ubuntu) or [**mkusb**](https://help.ubuntu.com/community/mkusb) (which must be installed).

---

### Post by The Cog on 2018-06-01
It looks as thought you are running the download command from within a folder where you don't have write permission. I wonder if this is because there is a problem with your home directory (which would explain your problems with the GUI). 
Anyway, you should be able to gain a root command prompt by running the command:
```
sudo -i
```
and then you should be able to download the ISO. 

Or maybe you have problem mounting the filesystem in read/write mode. If the filesystem is mounted read-only then you still won't be able to download the file. If that's the case then try to boot from a live CD ( assuming you have one) and perform the download and stick install from there.

---

### Post by lawrence-joy on 2018-06-01
To PaulW2U,
I was just following the instructions of The Cog. No USB Stick mounted so I assume the download of the ISO image file would go somewhere on my solid state drive (SSD), but I don't know where it would go.
To sododus,
Previously I was running Ubuntu 17.10. When I would get notification of an update I would run the update. A little while ago when I ran one of the updates there was a problem in that the message said something about there was a problem and was not completed. Updates after that said the same thing. When Ubuntu 18.04 LTS came along I ran the update, assuming that would take care of the problems I was having, and this is the version that is loaded. Previously, I think it was during one of those automatic updates, Kubuntu was added--not that I wanted it, but there it was so I worked with it--where I would pick on the terminal mode selection and away I would go.
To The Cog,
I don't think I am running the download command from within a folder as I am running the Code at the command prompt. I don't have a live CD of 18.04 but a friend has one that he said he would send to me in the mail. I have tried to run 'firefox' and that doesn't work as it did previously in 17.10. I will try the Code: 'sudo -i' and see what happens and report back later. When I do the download command 'wget...' where is the ISO image file downloaded to?

Thanks to all and I hope you will stick with me to get this resolved. My system consists of two SSDs on which I have Windows 10 OS loaded on one and Ubuntu loaded on the other one. They are completely separate and the Windows 10 OS is how I am able to communicate now that the Ubuntu OS is messed up.

---

### Post by oldos2er on 2018-06-01
> I don't think I am running the download command from within a folder as I am running the Code at the command prompt Folder (or directory) just means a particular place in the file system. Can you run *pwd* from where you ran the wget command, and post the result here?

---

### Post by lawrence-joy on 2018-06-01
[SOLVED] I was able to run 'sudo -i' and got to my root directory. I ran 'wget [http://releases.ubuntu.com/18.04/ubuntu-18.04-desktop-amd64.iso](http://releases.ubuntu.com/18.04/ubuntu-18.04-desktop-amd64.iso)' and it worked. I then mounted my 8 GiB USB stick and the OS recognized it with
"[ 8943.549616] sd 6:0:0:0: [sdc] No Caching mode page found"
"[ 8943.549639] sd 6:0:0:0: [sdc] Assuming drive cache: write through"
I ran 'sudo parted -l' which filled the screen with what looked like the status of all eight cores of my AMD microprocessor. If there was information about the USB stick previous to this I couldn't see it. I used the "sdc" as the USB stick address and ran
'sudo dd if=ubuntu=18.04-desktop-amd64.iso of=/dev/sdc bs=1M'
'sync'
And it ran and completed returning to "sync" at the command prompt.

The reason I wanted to get the ISO image file is to do a clean install because of the corrupted 18.04 LTS I have now. I will save what little directories and files I want to another USB stick, wipe the SSD clean, and then install 18.04 LTS from the USB stick I now have.
Thank you very much to everyone who responded.

---

