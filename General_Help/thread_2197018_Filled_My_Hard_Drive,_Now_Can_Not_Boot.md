---
title: "Filled My Hard Drive, Now Can Not Boot"
date: 2014-01-01
forum: General Help
---

### Post by Adler on 2014-01-01
Hi All,

I am running 12.04 LTS, and I managed to fill my 128Gb SSD. Now, I can't boot my system. Is there a way to delete files from Downloads? Right now I am sending this from the Boot Disk.

Help! Thanks in advance for any assistance.

Adler
Wildwood, New Jersey

---

### Post by Adler on 2014-01-02
Hi All,

I am still working on booting my machine to run 12.04 LTS, and not using my install disk. My 128Gb SSD is full, and any command lines in Terminal do not seem to work deleting files. I also have a 2Tb HDD attached to my machine, but if I copy / move these files to it the files still remain on my machine.

Any help would be appreciated. 

Adler
Wildwood, New Jersey

---

### Post by Impavidus on 2014-01-02
Boot from a live disk. Mount the 128GB SSD and the 2TB HDD. Move the files to the HDD using the GUI file manager or the terminal, whichever you feel most comfortable with. Copying or moving may not automatically remove the files from the SSD. Make sure the files have gone from the SSD (delete them if necessary) and **empty the trash**. Reboot.

Note: the rm command in the terminal removes files at once. Pressing delete in the GUI file manager moves them to trash, ctrl-delete should remove them at once.

---

### Post by Adler on 2014-01-02
Impavidus,

Thank you for the reply. I'll try your sugestions.

Adler
Wildwood, New Jersey

---

### Post by Adler on 2014-01-02
Hi All,

From the Live CD I go to my 128Gb SSD, then to Downloads. I have tried deleting files with both DELETE, and CTRL DELETE without success. 

I then tried the following in Terminal:

://media/4a55be6b-4161-4c15-984e-72a513ef116e/home/adler/Downloads# rm **file name** -f
://media/4a55be6b-4161-4c15-984e-72a513ef116e/home/adler/Downloads# rm **file name*** -f
://media/4a55be6b-4161-4c15-984e-72a513ef116e/home/adler/Downloads# rm -f -r **file name**
//media/4a55be6b-4161-4c15-984e-72a513ef116e/home/adler/Downloads# cd
:~# rm -f -r **file name**
:~# 

None of the above have worked. Any ideas? Thanks in advance for support.

Adler
Wildwood, New Jersey

---

### Post by grahammechanical on 2014-01-02
There is another thing that you can try. At the Grub menu select Recovery Mode and at the Recovery menu select Clean. It is labelled as "Try to make free space." That script seems to run two commands:

```
apt-get clean
apt-get autoremove
```

The clean command will remove .deb files for applications no longer installed on your system and all packages from the package cache.

The autoremove command removes packages that were installed by other packages and are no longer needed.

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

It might get booting and there you can do some more cleaning up.

Regards.

---

### Post by Adler on 2014-01-02
grahammechanical,

Thanks for your reply!

I always use **clean **and **autoremove **after I sudo apt-get update, sudo apt-get dist-upgrade, which is on a daily basis. So, there was nothing to remove.

I did try the the **Recovery Mode **on the Grub Menu, but the system only launced to some boot paramaters, but nothing where I could even open a Terminal. Nor, the opportunity to delete files.

I installed **Nautilus, then did gksudo nautilus** in Terminal. I could delete several files, but my system SDD still omly shows 16Mb free. This still does not allow me to Boot. Hmm...

I have tried several Trash commands to empty it, because none of the Trash Icons show anything. To see if a re-boot would work I have tried that also.

I am still stuck. Any further ideas?

adler
Wildwood, New Jersey

---

### Post by Impavidus on 2014-01-02
**rm -f filename** (usually the -f isn't needed) should either delete the file or give an error message. Do you get an error message?

Keep in mind some characters in file names, like spaces, need to be escaped or quoted.

Are you sure there is only one partition on the SSD? I guess so, but I have to ask. If you made a separate /home partition, cleaning stuff from that probably won't help.

Have a look at this thread: [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670). It has some advice in case of full drives.

---

### Post by Adler on 2014-01-02
> **rm -f filename** (usually the -f isn't needed) should either delete the file or give an error message. Do you get an error message?

Impavidus,

I originally tried several **rm commands **with no effect. I mounted my SDD, then got to **Downloads **via terminal. Then tried to remove the file using **rm comands**. I did eliminate the files that I wanted to, with **gksudo nautilus**. However, they didn't end up in Trash. I went looking for Trash in the fle structure, but couldn't find any trace of those deleted files. 

> Are you sure there is only one partition on the SSD? I guess so, but I  have to ask. If you made a separate /home partition, cleaning stuff from  that probably won't help.

There is only one partition. I did the install straight from the Live CD. 

> Have a look at this thread: [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670). 

I will take a look at the link above.

Thank you for your assistance.

This is all so embarrasing. I've been running Linux for over 10 years!

Adler
Wildwood, New Jersey

---

### Post by Adler on 2014-01-02
Hi All,

Well, I solved the problem.

From the Live CD I installed **nautilus**. I also installed the recommended package **gnome-suschi**. 

In Terminal I entered **gksudo nautilus**,went through my /Home Directory, then made sure that Hidden Files was checked so the I could view files not seen normally. Then going through the file structure I found, and opened, a file called **Trash-0**. Although none of my trash cans showed any trash there were three (3) large files there.

Here I highlighted each then I clicked **shift delete**. In the past I had made the mistake of clicking **ctrl delete**. I was asked if I wanted to delete each file after clicking **shift delete**.

Again, problem solved!

Thanks to all for your valuable input!

Adler
Wildwood, New Jersey

---

