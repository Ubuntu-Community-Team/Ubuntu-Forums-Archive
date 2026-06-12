---
title: "Share mail data with Thunderbird"
date: 2005-04-22
forum: General Help
---

### Post by krpasundarananda on 2005-04-22
Hello,
I am using Thunderbird in Windows for my e-mail. I have now installed Kubutu 5.04 and added Thunderbird there as well. As I am slowly shifting my things to linux I like to be able to use my e-mail from either platform.

How can I set up Thunderbird in Kubuntu that it uses the data files from my D: drive in Windows. I can already access the D:drive, it's just how to somehow link it. I guess that TB has to some how think it's in my home folder while in reality it's on the WIndows partition.

Any help or suggestions greatly appriciated.

Dada K.

---

### Post by magicfab on 2005-04-22
Start Thunderbird with the profile manager option, create a new profile and choose your TB directory of your WIndows partition as the data directory of the new profile.

On Linux, start Thunderbird with the the -profilemanager switch, e.g. ./thunderbird -profilemanager (this assumes that you're in the Thunderbird directory). (from [http://www.mozilla.org/support/thunderbird/profile#new](http://www.mozilla.org/support/thunderbird/profile#new) ).

Remember to backup your TB data directory in Windows before attemmpting this.

Here's a couple of how-tos:

[http://www.pcquest.com/content/linux/2004/104050805.asp](http://www.pcquest.com/content/linux/2004/104050805.asp)
[http://64.233.167.104/search?q=cache:8HHE6a36qkwJ:texturizer.net/thunderbird/share_mail.html+&hl=en&client=firefox-a](http://64.233.167.104/search?q=cache:8HHE6a36qkwJ:texturizer.net/thunderbird/share_mail.html+&hl=en&client=firefox-a)

---

### Post by diebels on 2005-04-22
Would this work too? :
```
ln -sf PATH_TO_WINDOWS_THUNDERBIRD_FOLDER ~/.mozilla-thunderbird/
```

---

### Post by Fab on 2005-04-22
[QUOTE=diebels]Would this work too? :
```
ln -sf PATH_TO_WINDOWS_THUNDERBIRD_FOLDER ~/.mozilla-thunderbird/
```[/QUOTE]
 should

---

### Post by krpasundarananda on 2005-04-22
Thanks for the info, trying it out right now. 

One obstacle is that I can read but not write in my window partition.
I opened konqueror as root and tried to change the permissions in the property sheet of the /mnt/WinD and set the recursive tab. No result it is not changing any permissions.
Is there a different way of doing this or should I change something in fstab? As it was not set up by defoult I may have done something wrong there. I have:

/dev/hda1	/mnt/WinC	ntfs, user,defaults	0	0
/dev/hda2	/mnt/WinD	vfat  user,defaults	0	0


Dada

---

### Post by krpasundarananda on 2005-04-23
[QUOTE=magicfab]Start Thunderbird with the profile manager option, create a new profile and choose your TB directory of your WIndows partition as the data directory of the new profile.

On Linux, start Thunderbird with the the -profilemanager switch, e.g. ./thunderbird -profilemanager (this assumes that you're in the Thunderbird directory). (from [http://www.mozilla.org/support/thunderbird/profile#new](http://www.mozilla.org/support/thunderbird/profile#new) ).

Remember to backup your TB data directory in Windows before attemmpting this.

Here's a couple of how-tos:

[http://www.pcquest.com/content/linux/2004/104050805.asp](http://www.pcquest.com/content/linux/2004/104050805.asp)
[http://64.233.167.104/search?q=cache:8HHE6a36qkwJ:texturizer.net/thunderbird/share_mail.html+&hl=en&client=firefox-a](http://64.233.167.104/search?q=cache:8HHE6a36qkwJ:texturizer.net/thunderbird/share_mail.html+&hl=en&client=firefox-a)[/QUOTE]
 I still couldn't make the Win partition writable but as my memory stick works fine under both system I stored the new profile there. I wrote some things while in windows and after following the instructions for setting it up in Linux I could read those things so they were indeed accessing the same files. 

Now when I went back to WIndows and tried to open TB it told the profile is locked. I can still access it from within Linux.
What could this be? The links describe a slightly different proccess as it seems for an older version of TB, the directories were a bit different on my system.

Dada

---

### Post by brickbat on 2005-04-23
try going to the directory where you have mounted the windows partitions and check the permissions with

ls -l

i thought logging in as root was forbidden by default.  it is better to go into a terminal and do it manually.

ciao
bb

---

### Post by derrick1985 on 2005-04-24
[QUOTE=krpasundarananda]I still couldn't make the Win partition writable but as my memory stick works fine under both system I stored the new profile there. I wrote some things while in windows and after following the instructions for setting it up in Linux I could read those things so they were indeed accessing the same files. 

Now when I went back to WIndows and tried to open TB it told the profile is locked. I can still access it from within Linux.
What could this be? The links describe a slightly different proccess as it seems for an older version of TB, the directories were a bit different on my system.

Dada[/QUOTE]
 well, if the system is NTFS, you can't. Ubuntu doesn't support write access NTFS, only read. You would have to format a small portion of your drive fat32 for both of the to work properly together.

---

### Post by brickbat on 2005-04-24
Derrick, I was thinking the same thing but if you look at the fstab extract you can see that the d drive is "vfat" so thats not the problem.

ciao
bb

---

### Post by crazybill on 2005-04-24
You might have to use the chown and chmod commands to modify your Windows location.  Check with ls -l of that directory first and modify as needed with those two commands.

---

### Post by krpasundarananda on 2005-04-25
[QUOTE=crazybill]You might have to use the chown and chmod commands to modify your Windows location.  Check with ls -l of that directory first and modify as needed with those two commands.[/QUOTE]
 Thanks again for your input.
My D: partition is definitely Fat32. I tried both from Gnome Desktop and KDE to open a file manager in Root mode. This also is no problem but somehow I still can't change the permissions for the D: drive. 
Right now I was downloading e-mail (still in Windows) so I'll have the try the command prompt commands ls -l and maybe the chown and chmod to see if that works. Could it be the way I added the drive in fstab? What should be the line in fstab to mount a window fat partition read and write?

Dada

---

### Post by krpasundarananda on 2005-05-05
Thanks again,

with all your input and some help from the Wiki pages I got it up and running now.

Dada

---

