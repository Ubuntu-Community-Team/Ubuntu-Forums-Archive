---
title: "need help:Installing Ubuntu from iso instead of downloading"
date: 2007-10-27
forum: General Help
---

### Post by dstar on 2007-10-27
Hello!!
I am new to this forum and need some help i downloaded ubuntu7.4 and 7.10 on my 56k modem and it took me two days to download.
Now i want wubi to install the ubutu 7.4 from the iso which i downlaoded in E:/Ubuntu/ubuntu.isoinstead of downloading it from the internet due to slow speed any help??

---

### Post by antimatter15 on 2007-10-27
copy the iso to the same directory as the installer

---

### Post by RandomSkratch on 2007-10-27
For 7.04 to work you need the Alternate ISO file.  For 7.10 you just need the normal ISO, either i386 or the 64bit one.

---

### Post by dstar on 2007-10-28
How can i do that.........i downloaded wubi from sourceforge and save it on my desktop and downloaded Ubuntu 7.4 and saved in E: drive so you mean that i shall copy wubi to the E:????

---

### Post by RandomSkratch on 2007-10-28
Yeah exactly.  First, like I mentioned before, you're going to need the Alternate ISO for Ubuntu 7.04.  Then make a directory on E:\ called Wubi or whatever you want.  Make sure both the Wubi installer and the ISO are in the same directory then run the installer.

As a note, you may want to make a copy of the ISO and leave it somewhere else as once the installer unpacks it, it's gone (unless you let Wubi download the ISO for you).

---

### Post by dstar on 2007-10-28
I still can not figure it out.
I created a new folder in G drive named installer
I copied both Wubi installer and iso to the folder installer
I open wubi.exe It asked me some questions and answere them
Then a progress bar nearly  reached at the end
On the bottom of the progress bar another progress bar appeared with text "Connecting to ftp://something"
Then It said downloading Ubuntu with "5 kib @" of something

---

### Post by ago on 2007-10-28
You need the ALTERNATE ISO with Wubi 7.04
And the DESKTOP ISO with Wubi 7.10

---

### Post by rkillcrazy on 2007-10-28
> **dstar said:**
> I still can not figure it out.
I created a new folder in G drive named installer
I copied both Wubi installer and iso to the folder installer
I open wubi.exe It asked me some questions and answere them
Then a progress bar nearly  reached at the end
On the bottom of the progress bar another progress bar appeared with text "Connecting to ftp://something"
Then It said downloading Ubuntu with "5 kib @" of something

If you were to install wubi to the default location, it would install to... ```
%systemdrive%\wubi
```

**%SystemDrive%** is normall **C:\**...

When it downloads the ALTERNATE iso file, it places that file in... 
```
%systemdrive%\wubi\install
```

Place your **ubuntu-7.04-alternate-i386.iso** in there and the setup shoould check to make sure the file is good and procedd if it is.  If it still tries to download the ISO, then you either have the wrong file or the file you have is corrupt.  Evidently you can place **ubuntu-7.10-desktop-i386.iso** in there as well but I've not tried it.

10-28-07
0919 EDT

---

### Post by dstar on 2007-10-28
I think i have donwloaded the wrong version...........is there any way to check either i have alternate or Live iso

---

### Post by dstar on 2007-10-28
> If you were to install wubi to the default location, it would install to...
Code:

%systemdrive%\wubi

%SystemDrive% is normall C:\...

When it downloads the ALTERNATE iso file, it places that file in...
Code:

%systemdrive%\wubi\install

Place your ubuntu-7.04-alternate-i386.iso in there and the setup shoould check to make sure the file is good and procedd if it is. If it still tries to download the ISO, then you either have the wrong file or the file you have is corrupt. Evidently you can place ubuntu-7.10-desktop-i386.iso in there as well but I've not tried it.

I did it as told me.....now everything works fine...........after the calculation of checksum it again downloads instalaation files

---

### Post by ago on 2007-10-28
> **dstar said:**
> I think i have donwloaded the wrong version...........is there any way to check either i have alternate or Live iso

The file name will say "alternate" if it's an alternate and "desktop" if it's a desktop.

If it downloads after checksum it means that the download was corrupted, you can test  the checksum yourself against what is provided on the website.

---

### Post by dstar on 2007-10-28
Oh...............i was installing desktop version of 7.4 so that's why it was not working my mistake
I shall try it with Wubi7.10 with desktop of ubutu7.10
let me download wubi7.10............i have 7.10 iso

---

### Post by dstar on 2007-10-28
yeah!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
i got it working it is creating  " Virtual disk" stuff
wubi7.10 with ubuntu desktop7.10

How much time it will take

---

### Post by dstar on 2007-10-28
I got it working
What's next??
Installer asks reboot.........computer reboots so how do i load ubuntu

---

### Post by ago on 2007-10-28
reboot and select Ubuntu. There is another installation stage yet.

---

### Post by dstar on 2007-10-28
i rebooted..........but their is no other option...............
It seems that i need to edit boot.ini can u help me in editing it

---

### Post by ago on 2007-10-28
boot.ini should have an extra line with

c:\wubildr.mbt="Ubuntu"


And of course there should be a file called wubildr.mbr somewhere in C:\

---

### Post by dstar on 2007-10-28
Thank you.............i already did it
After the reboot I get Ubuntu-Linux
1)When i click the first option alot of things happen and i get an cursor
2)Same as first
3)No acpi works but when the splash screen appears it says fat32 in not unix partion something and i have to shut down my computer

---

### Post by ago on 2007-10-28
post here /var/log/syslog

---

### Post by dstar on 2007-10-28
> The file system is FAT32 can not  be mounted on / because it is not fully functional Unix file system.Please chose a different file system such as ext2
Anyway Make a quick reply it is 1:00 Am or i will be late for the classes in morning

---

### Post by ago on 2007-10-28
I'd need /var/log/syslog

---

### Post by dstar on 2007-10-28
It is common sense how wud i access /var/log/syslog when error appears at splash screen
> The file system is FAT32 can not be mounted on / because it is not fully functional Unix file system.Please chose a different file system such as ext2

---

### Post by ago on 2007-10-28
> **dstar said:**
> It is common sense how wud i access /var/log/syslog when error appears at splash screen

ctrl+alt+f2

then nano /var/log/syslog to see
you can use cp to copy (windows drive should be available as /isodevice or /host)

---

### Post by dstar on 2007-10-28
i typed 
> cp syslog isodevice
It said
> cp:Can not create a regular file on isodevice  ACESS DENIED
I have a USB flash drive.So if u tell me how do i copy log file on my usb

---

### Post by ago on 2007-10-28
sudo cp /var/log/syslog /isodevice || cp /var/log/syslog /host

That will get the file to you windows drive

---

### Post by dstar on 2007-10-28
The result is too long to be paste here, I have uploaded it to my site. you can get by clicking the link below
[http://hackit.110mb.com/syslog.txt](http://hackit.110mb.com/syslog.txt)

---

### Post by ago on 2007-10-28
thanks

---

### Post by dstar on 2007-10-28
welcome.
how long it will take to fix my ubuntu..........i can not wait to use it.
I will check the forums tomorow it's 2 am now............and i am very sleepy.
Thanx for reading and answering by dumb questions.
See u tomorrow
cheers

---

### Post by ago on 2007-10-29
It does not look as a completely trivial issue. I'll need a bit of time for that.

For the technically inclined: resize.sh:get_resize_range seems to crash.

---

### Post by dstar on 2007-10-29
Ok.............i will wait

---

### Post by rkillcrazy on 2007-10-30
> **dstar said:**
> I did it as told me.....now everything works fine...........after the calculation of checksum it again downloads instalaation files

When it begins downloading the ISO, look in that same directory.  If it is dumping to that directory, shortly after the downloading begins, you should see something like **ubuntu-7.04-alternate-i386.iso.partial**.  See what the the partial ISO is and then you'll know what it's downloading.  Knowing that, you can try to download it from another (faster) location like a school or a friend's house if you don't wish to pull it down over your dial-up.  It could be downloading something other than **ubuntu-7.04-alternate-i386.iso** altogether.  I know when I tried to play with the 7.10 version (which broke but should be better when the bugs get worked out) it saw that I had a 64bit rig and pulled down the 64bit version.  I stopped the download, knowing I already had the ISO elsewhere and copied it over to the directory it needed to be in.  I reran the setup and it checked the file and continued.

10-30-07
0829 EDT

---

