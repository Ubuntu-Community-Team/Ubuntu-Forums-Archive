---
title: "Thunderbird won't open certain images received in email"
date: 2017-03-04
forum: General Help
---

### Post by Ralph L on 2017-03-04
I am running Xubuntu 16.04 with Thunderbird 45.7.0 (just updated). Thunderbird displays most photo images I receive without problem. However, it won't display some images. Instead immediately after the text message in the email, it shows a row of icons (one for each image it won't display) that look like a dimmed file icon torn in two.  Obviously some sort of file it doesn't like.  Also, there is no "Attachment" shown at the bottom of page.  However, if I go to Main menu>View>Message Body As and change from "Original HTML" to "Simple HTML", the photos will display in-line just fine. However, even with Simple HTML, no "Attachment" is displayed at the bottom of the page. In an attempt to find the problem I have disabled all the Add-on, but it doesn't affect this problem.  
If I install the add-on "Show all Body Parts" and set Message Body As to "All Body Parts", the photos will show up as Attachments at the bottom of the window and I can view them.  However, even with "Display Attachments Inline" enabled, the photos won't display in line. Instead I get:```
[cid:7c1c11e9-e067-492a-bc60-32cf380c219f][cid:1b659c9a-c780-4c3b-b171-899898369801][cid:98530805-56f6-453b-925d-98fcf5477e9b][cid:ec962f82-b892-457e-afae-e8204cad390a][cid:ebd5c049-2eec-4fbe-aabf-2a4151b89041][cid:4b8ce4f2-b7bf-4ecb-ba95-32f769751e50][cid:7d2e4102-5ce5-4953-9124-8fa6ab00d862][cid:acef8026-1c02-4771-a04b-4e04484f6779][cid:a41e58d0-a990-40dc-8be3-89f7569a1090][cid:c502717a-4436-4658-8bee-312cad1339e1]
```  For some reason Thunderbird really doesn't like these photos. I have searched the web and found something about security issues and the "cid" header, but I didn't understand it, and I didn't see any suggestions for how to fix it.  I can send an email with the photos to anybody who is interested.  Any help is greatly appreciated.

---

### Post by howefield on 2017-03-05
> **Ralph L said:**
>  I can send an email with the photos to anybody who is interested.  Any help is greatly appreciated.

Do that with one example email. Pm'ed you an address.

---

### Post by howefield on 2017-03-08
Thanks for the email, as you say the images display inline if you select "Simple HTML" so I'm assuming the issue is with saving a copy of them ?

You can either right click on each "cid" link and save from there or save the complete .eml file and unpack with something like mpack.

```
sudo apt install mpack
```

Assuming a destination folder of ~/Pictures/Hike and an .eml file name/path of ~/Documents/yesterdays\ hike\ to\ Cross\ Mt\_.eml.
```
munpack -C ~/Pictures/Hike ~/Documents/yesterdays\ hike\ to\ Cross\ Mt_.eml
```

```
sudo apt install mpack
[sudo] password for hugh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  mail-transport-agent inews
The following NEW packages will be installed
  mpack
0 to upgrade, 1 to newly install, 0 to remove and 0 not to upgrade.
Need to get 34.6 kB of archives.
After this operation, 92.2 kB of additional disk space will be used.
Get:1 http://gb.archive.ubuntu.com/ubuntu zesty/universe amd64 mpack amd64 1.6-8.1 [34.6 kB]
Fetched 34.6 kB in 0s (178 kB/s)
Selecting previously unselected package mpack.
(Reading database ... 216399 files and directories currently installed.)
Preparing to unpack .../mpack_1.6-8.1_amd64.deb ...
Unpacking mpack (1.6-8.1) ...
Setting up mpack (1.6-8.1) ...
Processing triggers for man-db (2.7.6.1-2) ...
```
```
munpack -C ~/Pictures/Hike ~/Documents/yesterdays\ hike\ to\ Cross\ Mt_.eml
tempdesc.txt: File exists
=Xutf-8XBXT3V0bG9va0Vtb2ppLfCfmIwucG5nX= (image/png)
IMG_2906XXLargeX.JPG (image/jpeg)
IMG_2907XXLargeX.JPG (image/jpeg)
IMG_2909XXLargeX.JPG (image/jpeg)
IMG_2910XXLargeX.JPG (image/jpeg)
IMG_2913XXLargeX.JPG (image/jpeg)
IMG_2914XXLargeX.JPG (image/jpeg)
IMG_2915XXLargeX.JPG (image/jpeg)
IMG_2917XXLargeX.JPG (image/jpeg)
IMG_2919XXLargeX.JPG (image/jpeg)
IMG_2920XXLargeX.JPG (image/jpeg)
```
```
ls ~/Pictures/Hike/
IMG_2906XXLargeX.JPG  IMG_2910XXLargeX.JPG  IMG_2915XXLargeX.JPG  IMG_2920XXLargeX.JPG
IMG_2907XXLargeX.JPG  IMG_2913XXLargeX.JPG  IMG_2917XXLargeX.JPG  =Xutf-8XBXT3V0bG9va0Vtb2ppLfCfmIwucG5nX=
IMG_2909XXLargeX.JPG  IMG_2914XXLargeX.JPG  IMG_2919XXLargeX.JPG
```

---

### Post by Ralph L on 2017-03-13
Howfield,
Thank you very much for your help.  You went to a lot of trouble, and I appreciate it.  One of the things I was wondering about is why Tbird won't display these photos, either in-line or as an attachment, without "Show All Body Parts" add-on installed, and why even with that add-on installed, it won't show the photos in-line.  Do you have any insight into this??

Thanks again,

---

### Post by Autodave on 2017-03-13
By chance, are your emails coming through Outlook? My wife refuses to leave her Outlook account and forwards me messages all the time that she can't display.

---

### Post by howefield on 2017-03-13
> **Ralph L said:**
> Thank you very much for your help.  You went to a lot of trouble, and I appreciate it.

You're very welcome. 

> One of the things I was wondering about is why Tbird won't display these photos, either in-line or as an attachment, without "Show All Body Parts" add-on installed, and why even with that add-on installed, it won't show the photos in-line.  Do you have any insight into this??

I *_believe_* that poor standards implementation (or at least different standards implementation) on the part of Microsoft are to blame here, the pictures will most likely display fine on another Microsoft machine using Outlook Express, Mail, Outlook or the like, I'm assuming that the mail was sent from a Windows installation. I could well be wrong, it's been a long, long time since I had to wrestle with this type of issue. I could well be wrong here and will happily defer to others with greater knowledge on the matter. 

I can confirm that no addon was needed to display the pictures in Thunderbird, they displayed fine viewing the email body as Simple Text if I recall correctly. It was a bit more difficult to save a copy, with 2 methods as described above.

---

### Post by Ralph L on 2017-03-13
NOTE"  This may all be incorrect!!!  This problem got submitted as a bug [https://bugzilla.mozilla.org/show_bug.cgi?id=1347598](https://bugzilla.mozilla.org/show_bug.cgi?id=1347598) .  Please read the bug report, rather than believe what I wrote here!!!

Thanks for the responses...  Just a little more info that I came across.  From my original post you can see that these are "cid" files that I can't display.  Apparently cid files are downloaded and read, when they are accessed in the email.  The files are NOT included in the email as are normal attachments, but just have a hyperlink to the web site that contains the file.  Apparently spammers and scammers commonly include cid files in email.  Then, to find out if they are sending to a real email address that somebody reads, they monitor the cid file to see if it is downloaded.  If the file is downloaded, they know they have reached a real person, (and send more spam to that email address).  For this reason many email programs (apparently Thunderbird is one of those) refuse to allow opening of a cid file.  However, people do send out legitimate photos as attached cid files.  That is why I have installed the Tbird add-on Show All Body Parts.  At this time I have Tbird set to always display cid files. And this makes me vulnerable to spammers.  As Howfield pointed out these files can also be read using Simple HTML.  But Simple HTML has other issues and you probably don't want to leave Tbird always set to Simple HTML.  Because I would like to be able to view these cid photos in-line, I sent a private message to the author of Show All Body Parts asking if he could install a display in-line feature to it.

---

