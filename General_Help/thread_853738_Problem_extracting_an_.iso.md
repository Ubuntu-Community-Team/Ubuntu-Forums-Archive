---
title: "Problem extracting an .iso"
date: 2008-07-08
forum: General Help
---

### Post by s3a on 2008-07-08
I tried mounting and it didn't work so I tried to extract instead and when I attempt to extract, I get the following error: **CD-ROM is NOT in ISO 9660 format**

I used uif2iso in Windows XP to convert .uifs into .isos and this is the problem I am getting now. I used MagicISO in Wine and it extracted without a problem but I was hoping to do this in a _native linux way_ and my game has 4 CDs (4 .iso files) which I need to mount a different times for the installation process.

Any help would be appreciated. Thanks!

---

### Post by Car60n on 2008-07-08
If you want to mount an iso do this
```
sudo mkdir /media/isomount && sudo mount -o loop filename.iso /media/isomount
```

hope it helps

---

### Post by s3a on 2008-07-08
Do I have to cd to directory before adding the filename and entering that command?

---

### Post by Car60n on 2008-07-08
yes you have to go to the directory where the file is located..

---

### Post by Taxman415a on 2008-07-08
> **s3a said:**
> Do I have to cd to directory before adding the filename and entering that command?

Yes, or use the complete path to the file such as /home/s3a/filename.iso

one or the other is the standard way to find a file on the command line.

---

### Post by s3a on 2008-07-08
I have a file on my desktop called 21.iso and I did the following and it didn't work:
[B]
deniz@deniz-desktop:~$ cd ~/Desktop/
deniz@deniz-desktop:~/Desktop$ sudo mkdir /media/isomount && sudo mount -o loop 21.iso /media/isomount
[sudo] password for deniz: 
mkdir: cannot create directory `/media/isomount': File exists
deniz@deniz-desktop:~/Desktop$[/B]

---

### Post by Car60n on 2008-07-08
> mkdir: cannot create directory `/media/isomount': File exists
looking at this i can say the directory is already there,
so all you need to do is mount--
```
sudo mount -o loop /home/deniz/Desktop/21.iso /media/isomount
```

---

### Post by ramjet_1953 on 2008-07-08
A really nice GUI package for mounting iso's is [COLOR="Blue"]gmountiso[/COLOR].

It is available in the repositories and can be downloaded using Synaptic or by typing this in a terminal:

[COLOR="Red"]sudo apt-get install gmountiso[/COLOR]

Regards,
Roger :cool:

---

### Post by s3a on 2008-07-08
deniz@deniz-desktop:~$ cd ~/Desktop/
deniz@deniz-desktop:~/Desktop$ sudo mount -o loop /home/deniz/Desktop/21.iso /media/isomount
mount: you must specify the filesystem type
deniz@deniz-desktop:~/Desktop$ 

and gmountiso isn't working which is basically why I tried to right click and select extract. Is this because uif2iso (for windows) converted it badly?? Like I said MagicISO in Wine is the only application so far that reads my images. It says .iso but could they still be .uifs "deep inside?"

MagicISO doesn't do the job for me though because the game I am trying to install needs 4 discs to be loaded one after the other to install the game and only the first one has a launcher.

Please help!

---

### Post by Car60n on 2008-07-08
If you have the original .uif file you could try to convert it to iso again using magiciso..

---

### Post by s3a on 2008-07-09
I deleted all my .uif files!

---

### Post by s3a on 2008-07-09
I loaded the .iso files using MagicISO and attempted to save them as .iso files (hopefully it would save them right was what I was thinking) and then, it still doesn't work, however, if I extract the contents using MagicISO and then load the .exe, it works! _However_, the game needs 4 cd iso files to be loaded one after another and I need to find a way so that I can make the installation process see the last 3 iso files in the method I am using. Can anyone help?

---

