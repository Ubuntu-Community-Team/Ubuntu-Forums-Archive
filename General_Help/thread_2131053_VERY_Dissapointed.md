---
title: "VERY Dissapointed"
date: 2013-03-31
forum: General Help
---

### Post by darkorical on 2013-03-31
I was trying to access files that were saved on my server that suffered a hardware failure. 

First try.
I took the hard drive out of the machine and put it in my win 7 machine and tried software to read the drive from win 7 with no luck.

2nd try
I tried to boot the drive inside my machine. it kept hanging.

3rd try 
booted my machine to a live USB and was able to finally see my files but now I cannot save them to the USB....

4th try
decided to install ubuntu desktop on the old hard drive 
when I did this it offered a method that would simply upgrade and not remove my files so I said YES do that while being quite grateful to finally be within reach of my goal.

so after the install I reboot and discover my files missing they were in /var/www/shared

and now the entire www folder is missing.

I Ran the upgrade that said it would keep my files and SPECIFICALLY avoided the option that said it would remove my files and it still removed my files

I have always respected ubuntu and used it exclusivly as a server for many years now (well since version 7 was released) and today I am simply Fuming mad I cant beleive it did this.

---

### Post by deadflowr on 2013-03-31
Sorry to hear.

I don't think the installer considers files other than the ones in the home directory to be yours, whether you own them or not.

You could try programs like testdisk or photorec to try and recover the lost data.

---

### Post by sudodus on 2013-03-31
I can understand your feelings.

Too bad you didn't succeed in your 3rd try. I think you were close. Maybe that option in your 4th try is designed for Ubuntu desktop and only saves the /home directory.

But what can you do now? I think that there is a fair chance that data from several of the files from  /var/www/shared are still available on the hard disk. Maybe some of them were overwritten, but the others can be saved with ***PhotoRec***. See this link

[[COLOR=#ff0000]http://www.cgsecurity.org/wiki/PhotoRec[/COLOR]]("http://www.cgsecurity.org/wiki/PhotoRec")

This program was originally made to recover photo files from corrupted flash memory cards, but now it is improved and can recognize the signatures of several file types and recover them to files. Unfortunately the file names are lost, and there is a lot of work if there are many files.

---

### Post by ajgreeny on 2013-03-31
It's a pity you did not come to this forum earlier because at stage 3 using the live CD you could easily have saved the files you wanted to your USB simply by using the command **gksudo nautilus** to open the file manager as root.

Too late now, but remember it if you get into the same situation again and you can save yourself a lot of trials and tribulation.

---

### Post by CCgirl6690 on 2013-03-31
dam , sry . you were close tho on your 3rd try . but like [**[COLOR=#000000]ajgreeny[/COLOR]**]("http://ubuntuforums.org/member.php?u=27747") said you can see your files with that gksudo nautilus command but if you tryi and copy them you will see that it wont let you . unless you give the whole folder R777 allocation

---

### Post by prodigy_ on 2013-03-31
Ubuntu isn't known for its smooth handling of upgrades. And Windows isn't any better.

It's a painful experience but you can learn from it if you'll stop blaming the OS. Regular backups are essential if you care about your data. And they're stupid easy to maintain (especially if you only need one snapshot at a time). A simple rsync script running every night from /etc/cron.daily/ and that's it - you have your basic backup solution.

---

