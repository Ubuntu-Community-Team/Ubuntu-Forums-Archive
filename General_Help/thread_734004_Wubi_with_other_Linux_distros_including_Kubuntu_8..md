---
title: "Wubi with other Linux distros including Kubuntu 8.04"
date: 2008-03-24
forum: General Help
---

### Post by martosurf on 2008-03-24
hi!  :popcorn:

I just want to know if Wubi will work with:

1. Kubuntu 8.04 Beta remix (KDE4)
2. OpenSUSE 10.3 KDE
3. DreamLinux 3
4. as well other linux distros - It would be a killer if you just can test any distro this way


thanks and congratz on such a GREAT application =)

---

### Post by .nedberg on 2008-03-24
> **martosurf said:**
> hi!  :popcorn:

I just want to know if Wubi will work with:

1. Kubuntu 8.04 Beta remix (KDE4)

Yes!

The others I don't know about...

---

### Post by martosurf on 2008-03-24
hi .ned tnx 4 your kind reply

Indeed, I just downloaded and burned K 8.04.

After choosing to install it *via* Wubi I found myself totally lost (lol).
May be I'm a stupid ******* but found serious problems with this kind of 'virtualization':

1. I installed K 8.04 beta thru Wubi then reboot (as asked by Wubi installer)
2. When PC boot I choose to boot Kubuntu then press Esc key to show menu and the choose verbose mode
3. After Kubuntu initiated I choose my city/country then happens the first error, something related to filesystem that after ages waiting for anything that can happen I choose Ignore and go to the next screen.
4. On the user account configuration screen a window pop-ups telling it is searching for the filesystem. I close that windows because nothing happens, create my user account and go for the next screen (with the same credentials Wibu asks when first installing Kubuntu from within Windows.
5. Finally Kubuntu 4 kicks in and I found THE SAME screen you can find in the LiveCD, in fact is the same thing.
6. "well, let's then start installing this **** for good" I thinked about finally install Kub in the virtual partition Wubi made minutes ago. All I find is the common install procedure, choose language, location and partition where you want to install Kubuntu.

...

WTF??? It isn't supposed after installing it from Wubi it will be ready to use at next boot???

Okay, may be I'm a pathetic ******* with no knowledge of computing at all, but all this procedure is but ****.
I do really hate Window$ because it's traditionally shitty AND I know Micro$oft spy on us with their OS, but yesterday I installed Vista sp1 just to give it a try and found it plain AWESOME.
Also I don't know why Linux GUI developers make GUI so giant!! I need to have a 30" monitor to have several windows displayed on screen! With XP or Vista my 17" 1280x1024 works really fine =)

Once again, I really don't like Window$, I'm telling Linux is way beyond Window$ GUI and very FAR FAR FAR FAR away from making install process a breeze as it was with Vista.

cheers

---

### Post by .nedberg on 2008-03-24
I have in fact never used Wubi, I just know it is there.

Here is what I think happened:

Wubi installed Kubuntu in a virtual disk inside Windows and told you to reboot. Since you probably had the CD in the drive at this time, your computer booted into the LiveCD. When presented with this desktop you went ahead and installed again, making a "proper" install this time (but something went wrong...).

If, when you boot your computer, you are presented with something called [GRUB]("http://i80.photobucket.com/albums/j180/brthomas503/grub.jpg"), then Kubuntu installed properly the second time. If you are presented with the [NT loader]("http://content.answers.com/main/content/wp/en/thumb/c/c4/350px-NTLDR_selection_menu.png") (not completely sure about this on Vista) your second install failed and you can select your Wubi install.

Remember that 8.04 is still Beta software and the Wubi install is quite new. Things can go wrong with beta software!

---

### Post by martosurf on 2008-03-24
Way too much kindness on your part, I give you :KS:KS:KS:KS:KS :lolflag:

After installing Wibu Kubuntu I take out the installer CD and boot through the menu option and then happen what I described before - anyway, you have a good point on your guess.

After all of this I just decided to plain install Kubuntu in it's own partition.
Installation was smooth, GRUB worked like charm (I had problems with 7.10 Ubuntu/Kubuntu) BUT altough apt-get can download the list of packages to update it actually stop cold when it have to start updating the system =(

But this is another story I think I will continue in kubuntuforums.net !!

Thanks a lot 4 your time and help :D

---

### Post by bsalt on 2008-04-04
hey martosurf, i'm just letting ya know that i did notice that if you try to install ubuntu amd64 inside windows 32-bit, it gives that partition error. 


**For everyone experience problems with incompatible CD-ROM's:**

Don't use your CD-ROM! I downloaded the ISO file, download **Virtual Clone Drive** (in Vista) and mounted the ISO as a CD-ROM. I then installed it inside Windows with no problems (once I realized I needed to try Ubuntu x86 inside Windows x86.

---

### Post by ago on 2008-04-04
No need to mount an ISO, just launch wubi with the ISO in the same drive

---

### Post by ago on 2008-04-04
No need to mount an ISO, just launch wubi with the ISO in the same drive
You can use the wubi.exe in the CD or the one on ubuntu-installer.org

---

