---
title: "WD MyBook Error on Ubuntu 16.4"
date: 2017-02-18
forum: General Help
---

### Post by linux.girl on 2017-02-18
Hi everyone,

Here I am once again in need of this amazing and helpful community!

I have a brand new WD My Book external HD with 4TB. It was working great on my Ubuntu 16.4 64 bit. Then, for a few minutes, I disconnected it from my Ubuntu and connected it to a Windows 7 computer also 64 bit. 

When I tried to re-connect it to my ubuntu PC, which is my main PC, I get the following error:

"This location could not be displayed. Sorry, could not display all the contents of “My Book”: Error when getting information for file '/media/user/My Book/User Manuals': Input/output error"

What do I do? Any ideas?

Super thanks in advance!!!

---

### Post by linux.girl on 2017-02-18
Now the problem got even worse - I unmounted the WD and now it does not even appear on ubuntu, no error message, notghing. I looked for it on /dev and it is not there either. I disconnected the power, I unplugged the USB, put it all back in, and I still can't see the disk :-(

---

### Post by RobGoss on 2017-02-18
Hello and welcome, Do you have **Tweak tool **installed? if you do open it and you will see **Desktop**, click on that you'll have the option to mount volumes. Check the mounted volumes options and see if your device is mounted

---

### Post by howefield on 2017-02-19
Have you tried plugging the disk back into Windows and properly unmounting it, or whatever the correct terminology is for Windows ejecting USB peripherals ?

---

### Post by RobGoss on 2017-02-19
I know the WD external drives don't play well with both Windows and Ubuntu or Linux for that matter, it's ether Windows or Ubuntu, but not both 
I believe it has something to do with the type of formatting for Ubuntu

WD requires a password to be unlocked in order to use the drive with Windows I'm not sure if this is what's needed to use the drive on both systems. I'm also having issues with my WD external drive it was working ok then just stop allowing me to access the files on Ubuntu

---

### Post by linux.girl on 2017-02-19
Hi guys, how many nice answers and suggestions, so here it goes:

1 - I have something called unity tweak tool installed, is that what you mean? I opened it and didnt really understand how it can help me. EDIT - I went to Desktop on Tweak and it is not mounted.
2 - I tried to plug the disk back into windows, didn't help, but I will try again, you never know.
3 - I dont need to use the WD on both windows and ubuntu - just on ubuntu. I mistankely connected it to windows for a few minutes and when I plugged it back to ubuntu it gave me that error that I posted. And now after I nicely umounted the volume from my ubuntu, I cant seem to find it anymore to re-mount it and try to fix it or even re-formmat if needed (hope not cause I have a lot of info there). It is connected to the pc, but when I look on ls /dev/sd* it just doesnt appear there, so now I dont even know how to find it.

Any ideas?

Thanks!!!!!!!!!!!!

EDIT: I just tried to connect it to windows and it doesn't recognize it either :-( What do I do? It is brand new 4TB! How do I find it on Ubuntu to try and mount it?

Update: I connected the disk to win 10 LT instead of win 7 and it connected fine and all the data is there intact. I now reconnected it back to Ubuntu in the hopes it would solve it, but again I get the error:

""This location could not be displayed. Sorry, could not display all the  contents of “My Book”: Error when getting information for file  '/media/user/My Book/User Manuals': Input/output error"

It opens the disk but doesn't show the data in it. But when I try to see the properties of the disk, it shows me the exact amount of free and used space - I just can't access the data.

It is not asking me for any username or password, it just says "This location could not be displayed. Sorry, could not display all the  contents of “My Book”: Error when getting information for file  '/media/user/My Book/User Manuals': Input/output error"

Experts and friends, what do I do? I cant use this disk on windows and I dont have any other place with enough storage to copy all this data, then format the disk and copy it back to ubuntu. Any ideas please?

And more, from the command line I get this:

```
user@linux:~/Desktop$ cd /media/user/
user@linux:/media/user$ ls -l
total 0
drwxrwxrwx 1 user user 0 Feb 19 00:54 My Book
user@linux:/media/user$ cd My\ Book/
user@linux:/media/user/My Book$ ls -l
ls: cannot access 'Locale': Input/output error
ls: cannot access 'WD Apps for Mac': Input/output error
total 64
drwxrwxrwx 1 user user 45056 Dec  1 22:36 Completed Downloads
-rwxrwxrwx 1 user user 20480 Nov 21 18:34 Extras
drwxrwxrwx 1 user user     0 Nov 22 20:50 From PC Windows 7
d????????? ? ?     ?         ?            ? Locale
drwxrwxrwx 1 user user     0 Nov 27 20:53 $RECYCLE.BIN
drwxrwxrwx 1 user user     0 Feb 19 21:18 System Volume Information
drwxrwxrwx 1 user user     0 Feb 19 00:54 Test
d????????? ? ?     ?         ?            ? WD Apps for Mac
```

Any way to fix this?? And BTW, all the folders that I cant access are marked in GREEN, like Completed Downloads. What does it mean?

---

### Post by uNoubu8a on 2017-02-19
I don't have an answer to the problem but if I were you I would again mount to Windows 10 and copy from it all important data so at least you have it safe.  Then I would re-format the drive in Windows 10 (ntfs or fat32 or what ever plays nice with 4TB) also perhaps check SMART to see if there are any errors.  Then give it a go on Ubuntu again.

---

### Post by linux.girl on 2017-02-19
I guess you are right - I just have to find a storage big enough to copy everything that is in there. If anyone else have other ideas, more than welcome!

---

