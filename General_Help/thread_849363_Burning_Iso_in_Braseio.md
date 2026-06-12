---
title: "Burning Iso in Braseio"
date: 2008-07-04
forum: General Help
---

### Post by rokytnji on 2008-07-04
Just wanted to know when burning a Linux live cd in Braserio which I've done before, do I need to use the md5sum to check integrity of download or does Braserio do it for me automatically and the md5sums are for Windows users only? If I do need to run a check, how do I go about it. I tried typing md5sum with the file name in terminal and I got no such command exists or file and the file is sitting on desktop. Also, a little off topic here, I tried to post this in the Newbie section and was given the screen that I wasn't allowed to post there. Don't know why when I can post it here.Just in case somebody from admin reads this since I haven't figured out yet how to contact them about this.):P

---

### Post by rbmorse on 2008-07-04
Bresero will geneate an md5 sum but I don't know if it checks it the specified value automagically.  Make sure the package "coreutils" is installed; in a terminal window: 

sudo apt-get install coreutils 

Coreutils is the metapackage that installs md5sums + some other useful stuff in one go. 

When I see the error you mentioned from the forum it usually means I've forgotten to log in.

---

### Post by rokytnji on 2008-07-04
:lolflag:I just went to General straight from Newbie without having to log in. I went to User Cp to see if I had any new messages before all that and Web Forum shows me as logged in and registered. Oh well, guess I'm special. Thanks for the info rbmorse. Appreciate the metapackage info.:)

---

### Post by rokytnji on 2008-07-04
Went to synaptic and found coreutil already installed so I guess I'm OK. I just wasn't sure about how Ubuntu checks Live Iso's to make sure your download is OK.:popcorn:

---

### Post by plucky on 2008-07-04
> **rokytnji said:**
> Just wanted to know when burning a Linux live cd in Braserio which I've done before, do I need to use the md5sum to check integrity of download or does Braserio do it for me automatically and the md5sums are for Windows users only?

Yes you need to do the md5sum separately.

> I tried typing md5sum with the file name in terminal and I got no such command exists or file and the file is sitting on desktop

You need to switch to your Desktop before running md5sum ```
cd ~/Desktop
md5sum <Name of file>
```

The terminal is case sensitive.

Then compare the md5sum generated with md5sum.txt file ,also from the mirror you downloaded the iso from.

Good Luck

---

### Post by rokytnji on 2008-07-04
Don't know what I'm doing wrong. Tried cd ~/Desktop
md5sum <Name of file> in various combinations and get invalid command for cd -/Desktop and running both commands with file name gives me No file etc. 

This is my terminal (harry@harry-desktop:~$)

This is command ( md5sum netbsd-live-2007.iso)






:confused:

---

### Post by plucky on 2008-07-04
> Don't know what I'm doing wrong. Tried cd ~/Desktop
md5sum <Name of file> in various combinations and get invalid command for cd -/Desktop and running both commands with file name gives me No file etc.

This is my terminal (harry@harry-desktop:~$)

This is command ( md5sum netbsd-live-2007.iso)


cd ~/Desktop should change the prompt to **harry@harry-desktop:~/Desktop$**



Try ```
cd /home/harry/Desktop
ls -l
``` that is lowercase L not a 1 to see if you can see the file

OR 

```
md5sum /home/harry/Desktop/netbsd-live-2007.iso
```


Good Luck

---

### Post by rokytnji on 2008-07-04
Worked liked Vaseline on a babys rash Thank you plucky. gonna store your instructions in a text file in case I forget later.:guitar:

---

