---
title: "How to get Kindle downloads from 'Downloads' to my Kindle?"
date: 2020-06-22
forum: General Help
---

### Post by Extreedoc on 2020-06-22
Just got 20.04 and it sure is different to 'Trusty'. I've downloaded some Kindle books to my computer and there they are in the downloads file but I can't drag them to my Kindle like I did with Trusty. When I drag the book file to the Kindle icon in the Dash it tells me: Error, destination is Read-Only, (or words to that effect). It used to be so easy, what do I need to do?

---

### Post by CelticWarrior on 2020-06-22
Ubuntu 14.04 used Unity as DE, Ubuntu 20.04 uses Gnome. Although looking similar, and for the most part having the same functionality (after all Unity was a plugin to Gnome), some things work differently.

Avoid such drag'n'drop. Open your file manager and copy/paste (like always).

---

### Post by Extreedoc on 2020-06-22
Thanks CelticWarrior, problem: Copied one of the files and when I tried to Paste it into the documents folder in my Kindle I got the message: "Could not paste files, permissions do not allow pasting files in this directory"

---

### Post by cmcanulty on 2020-06-22
You need to change the mounted kindle ownership to yourself and give it read & write permissions. I need to leave for work now but can explain how to do that later if someone doesn't tell you first.

---

### Post by Extreedoc on 2020-06-22
Thanks cmcanulty, yes, I might not have done it right but I already had this idea and check permissions on my Kindle. It looks like it is set for me to both create and delete files. There are two other headings: Group and Others, these are set to 'Access' and cannot be changed to 'Create and Delete'. Pointers gratefully received...

---

### Post by cmcanulty on 2020-06-22
A common Linux issue is doing that to attached USB devices when not safely removed. Try attaching to another computer, any operating system and safely removing it then reattach it to your machine and see it it works OK

---

### Post by Extreedoc on 2020-06-22
> **cmcanulty said:**
> A common Linux issue is doing that to attached USB devices when not safely removed. Try attaching to another computer, any operating system and safely removing it then reattach it to your machine and see it it works OK
I can't do that at the moment, my wife's computer is in the shop, lousy Windows 10 issues - wish we'd never had the thing but I can tell you that I have never improperly unmounted the Kindle, in fact, today is the first time I've connected it since the 20.04 install. If I can think of another machine to connect it to, I will. Thanks for your support.

---

### Post by ActionParsnip on 2020-06-22
Any computer will do. Do you have a buddy with a Windows system you can borrow for 10 seconds

---

### Post by Extreedoc on 2020-06-22
> **ActionParsnip said:**
> Any computer will do. Do you have a buddy with a Windows system you can borrow for 10 seconds
I'll see what I can do, maybe the wife's computer will be fixed by now, it's been in the shop for more than a week.

---

### Post by Extreedoc on 2020-06-23
Ok, wife's machine back from the shop, connected my Kindle to it and unmounted properly and tried on my 20.04 again. Still no joy, it *still* says no permissions to paste files. What now?

---

### Post by yancek on 2020-06-23
Post the output of the following command on the mount point (directory) in which your Kindle files are as well as on a/some files in the directory to find the owner:group and permissions.

```
ls -l /mountpoint
```

---

### Post by Extreedoc on 2020-06-23
> **yancek said:**
> Post the output of the following command on the mount point (directory) in which your Kindle files are as well as on a/some files in the directory to find the owner:group and permissions.

```
ls -l /mountpoint
```

Sorry but you'll have to walk me through that... I'm presuming the code goes in the terminal, also presuming that the Kindle needs to be connected to the computer. If I'm right, the output will appear in the terminal and I can 'Print screen'?

---

### Post by CelticWarrior on 2020-06-23
> I'm presuming the code goes in the terminal, also presuming that the  Kindle needs to be connected to the computer. 
Yes and yes.

> If I'm right, the output  will appear in the terminal and I can 'Print screen'?
No.
Please select the output just like you would do with any text. Then either right-click > copy -or- CTRL+SHIFT+C to copy. Then here click the Go Advanced button, click "#" and paste inside - CTRL+V or right-click > paste - so it keeps the format and makes it easy to read.

---

### Post by Extreedoc on 2020-06-23
> **CelticWarrior said:**
> Yes and yes.


No.
Please select the output just like you would do with any text. Then either right-click > copy -or- CTRL+SHIFT+C to copy. Then here click the Go Advanced button, click "#" and paste inside - CTRL+V or right-click > paste - so it keeps the format and makes it easy to read.

Excellent, I'll get on that tomorrow, it's getting late.
Thanks for your support.

---

### Post by Extreedoc on 2020-06-24
Ok, when I type in the command I get: user@user-MS-7721:~$ ls -l /mountpoint
ls: cannot access '/mountpoint': No such file or directory
user@user-MS-7721:~$

---

### Post by CelticWarrior on 2020-06-24
"mountpoint" is a placeholder...

> Post the output of the following command **on the mount point (directory)  in which your Kindle files are** as well as on a/some files in the  directory to find the owner:group and permissions.

---

### Post by Extreedoc on 2020-06-24
> **CelticWarrior said:**
> "mountpoint" is a placeholder...

Ok, so what now? The Kindle was working fine, accepting downloads until I upgraded to 20.04, since then it's just 'Read Only'.

---

### Post by CelticWarrior on 2020-06-24
What now? Please provide the results of the command with the actual mountpoint?

---

### Post by Extreedoc on 2020-06-24
> **CelticWarrior said:**
> What now? Please provide the results of the command with the actual mountpoint?

I entered the code as given by yancek and that is the result I got, If I should have entered something instead of 'mountpoint' I am unaware as to what?

---

### Post by CelticWarrior on 2020-06-24
Do you know the meaning of "placeholder"? It's something generic intended as a general example and to be replaced be the actual thing.

Example:

I have an external SSD mounted at /mnt/KINGSTON120.
If I didn't know its mount point I would either use a command in terminal to find out or use the GUI tool Disks, click on the drive in the left column and it would tell me where it is mounted.

Then I would do
```
ls -l /mnt/KINGSTON120
```
effectively replacing "/mountpoint" by the actual mount point "/mnt/KINGSTON120"

That will give the intended result of showing the permissions which is what we want to know to understand what's wrong with your kindle. Something like this:

```
total 33557288
-rw-rw-r-- 1 username username   476816690 Xuñ 15 13:31 '2020 All New Changan UNI-T SUV 1.5T 7DCT POV Test Drive (1080p_60fps_H264-128kbit_AAC).mp4'
```

Here "username" is a placeholder, I've changed it from the actual username that you don't need to know.
BTW, the video in the example is available in Youtube: [https://youtu.be/-35fbdMbvls](https://youtu.be/-35fbdMbvls)

---

### Post by Extreedoc on 2020-06-24
Thank you, now I see... Is this what you want to see?

```
user@user-MS-7721:~$ ls -l /media/user/Kindle
total 40
drwxr-xr-x 2 user user 24576 Jun 24  2020  documents
-rw-r--r-- 1 user user     0 Nov  6  2019  DONT_HALT_ON_REPAIR
drwxr-xr-x 4 user user  8192 Mar 10  2016  system
drwxr-xr-x 2 user user  8192 May 31 17:22 'System Volume Information'
```

---

### Post by cmcanulty on 2020-06-24
Try installing pmount  if you have gparted then open gparted and see if it is listed. If so type pmount dev/whatever
```
pmount /dev/whatever like sdb1 sdc1 etc
```

---

### Post by Extreedoc on 2020-06-24
> **cmcanulty said:**
> Try installing pmount  if you have gparted then open gparted and see if it is listed. If so type pmount dev/whatever
```
pmount /dev/whatever like sdb1 sdc1 etc
```

I don't have gparted installed but I could install it with the synaptic. 'whatever' etc is another placeholder? In my case I should type /media/user/Kindle...?
Is pmount part of gparted or as you seem to imply I must install it separately?
Sorry for the n00b questions, I'm not techy as you will have guessed, despite having been an Ubuntu user for 11 years.

---

### Post by Extreedoc on 2020-06-25
I have installed gparted and pmount and with Kindle connected and gparted open there is no mention of the Kindle. Icon for Kindle does show in the Dash.

---

### Post by VMC on 2020-12-16
Not sure which Kindle device you have, but I just plug in my Kindle into a usb port, open the documents folder and drop my axw3 book from my computer into the documents folder in the Kindle. Been doing it that way for years without issue.

---

