---
title: "windows partion disappeared.plzzzz help"
date: 2007-06-01
forum: General Help
---

### Post by Irti on 2007-06-01
hey......i just installed ubuntu linux 7.04........dual booted with xp....i hav a 160 gb hard drive which was partioned in 2 ..... one 50 gb(c:) the other 100 gb(d:).....i installed ubuntu linux 7.04.....everything's workin fine...and my xp is running fine too....the only prob is that the d drive has disappeared wen i tried on xp....i cant access any of the stuff tht was on my d drive ...its just simply not there...only my c drive is visible.....i can access my d drive on linux though.........also i imported all of my xp documents on linux....and i want to gt rid of them now.....is there any specific way or do i just go about deleting them....i also wanted to install google talk on linux...any way to do tht....tried gain bt cudnt find google anywhere in the list...i am completely new to linux ......................  pls help

---

### Post by shae on 2007-06-01
If you would like to get rid of your old D drive, I recommend using gparted in Linux.  

To do so you must open a terminal and enter:
```
sudo apt-get install gparted
```
It will prompt you for your password for root privilages.

Next to run gparted use the following code in terminal:
```
gksu gparted
```
It may again prompt you for your password.

Delete your second ntfs partition and replace it with a ext3 partition.  Sounds like a buzz kill for windows right?  Well then you can use a driver to gain access to it in windows.  It is available from here: [http://www.fs-driver.org/]("http://www.fs-driver.org")

And what about all that swap space on a partition.  Well you can have windows use it too!  Use the SwapFS driver here: [http://www.acc.umu.se/~bosse/]("http://www.acc.umu.se/~bosse/")

You cannot use the Google Talk client in Linux, but no worries.  First you might want to update GAIM from beta 6 to the final release which is named pidgin.  You can download the latest Pidgin package from here: [http://www.getdeb.net/release.php?id=955]("http://www.getdeb.net/release.php?id=955")

To install, double click the icon where you downloaded it and click on the install button.  You will be prompted for your password.

Then you can follow the instructions from here to set it up for gtalk:
[http://www.google.com/support/talk/bin/answer.py?answer=24073]("http://www.google.com/support/talk/bin/answer.py?answer=24073")

---

### Post by Irti on 2007-06-01
thanx a lot man....gonna try it out now...............

---

### Post by Irti on 2007-06-01
no waitttttttt......i dont wanna delete any of the old stuff tht was there on the d drive....will this gparted thing delete the stuff on my d drive....?????

---

### Post by shae on 2007-06-01
"and i want to gt rid of them now"  I took that to mean the D drive.  Sorry.  Some of the other things you should try.  I am not sure why Windows would stop recognizing your D drive.  What I would do would delete the D drive and remake it as ext3 and make it readable in linux and windows.  This would delete everything, but if you moved it all over into linux, you could move it back afterwards.

Anyways, what were you intending on deleting?

---

### Post by Irti on 2007-06-01
i wanted to delete the stuff tht i imported to linux from windows.....leaving tht apart...the basic problem is tht i partitioned the free space using the partion manager thing tht comes on wen u install ubuntu linux......i read sumwhere tht using the guided partion thing is the best thing to do if u wanna leave ur windows intact......and now i cant c my d drive on windows.....i even tried searching for a few files tht were there on my d drive in windows.....nuthin came up.......

---

### Post by shae on 2007-06-01
What did you import?

Yes using the guided partitioner is safer if you are new, but because you did not break your partition, you should be safe in that regard.

---

### Post by Irti on 2007-06-01
ok this is silly...i restarted my comp and everythin is fine.....hehe.....ok i am a completely newbie to linux....i wanted to move sum files from my desktop to tht usr folder...i tried using tht command thingy.....bt it says i dont hav permissions and all.....i cant cut ..paste....i dont hav permissions for tht either...i tried using the sudo command....bt it says tht the file or directory doesnt exist ...do i hav to give full file path names and everythin wen i am tryin to move files or sumthin???? if yes then wut r the path names used in linux???? cud u plzzzzzzzzz help me on this one.....and can i use the call feature in google talk while on tht pidgin thing....and do u hav ne ideas if i can use a webcam on pidgwin while using msn messenger....sry for askin soo many questions all at once....bt i am completely knew to this linux concept...:D

---

