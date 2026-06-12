---
title: "how to speed up my ubuntu 7.10?"
date: 2008-02-04
forum: General Help
---

### Post by xiangcao on 2008-02-04
hi,
i have try many times to iinstall ubuntu 7.10, almost 3 times, finally i have succeed.
BUT, the speed is so slow, it need more then 1 minutes 30 seconds above to boot up ubuntu, after i login, i click on "firefox", it need 1 minute to wait it load the application....oh my god...

in xp, i just need wait within 5 seconds after i click the icon of firefox...
i found the solution from google is about "File System Check(Fsck)"

Terminal : sudo gedit /etc/fstab 
find the 
"# /dev/sda1 
UUID=6E50BE5450BE22AF /media/sda1 ntfs defaults,umask=007,gid=46 0 1 "
change the last digit "1"to "0"

i follow the step,this is what i get:
[IMG]http://i18.photobucket.com/albums/b113/mason_ev_1/2%20album/Screenshot-4.png[/IMG]

my ubuntu does have the same word with abovesaid, i scare if i change randomly will trouble my hard disk cant boot xp...

can somebody tell me how to fix it???

i'm using 256mb ddr ram, 
pentium 4 (2.4 Ghz)
graphic card is S3 Graphic 6.13.10.1104 (i get it from "my computer" list)
20 gb spaces available in harddisk


Thank you

---

### Post by ajgreeny on 2008-02-04
You do not have your windows installation listed in fstab so it will not be mounted automatically by the system at bootup.  What is the output of sudo fdisk -l in the terminal, which will let us know what is installed on your machine.

What is the spec of your computer, and is it connected to the www when in ubuntu?  iIn order to check what takes so long at bootup you can disable the quiet splash in the menu.lst file for a single boot by chosing the ubuntu line in menu and hitting "e".  In the text that appears there, go to the line starting "kernel" and hit "e" again.  Now scroll to the end of the text and delete the words "quiet splash", hit enter then "b" to boot.  A lot of text will now scroll as the computer boots and you will be able to see where the delay is.  Let us know and we'll see what we can do to help.

Just a thought - You are running a hard disk installation of ubuntu aren't you, not just the live CD?  Your fstab seems a little strange to me.

---

### Post by perfecttao on 2008-02-04
Looks like it's definitely a livecd running there, looking at the fstab....

Given that you are using 256Mb RAM it is highly likely that the livecd will be slow - as it doesn't write to your hard drive it uses the RAM that you have as a READ/WRITE resource.

You say you have installed - have you tried to remove the Ubuntu cd from the drive and reboot?  If it boots into Ubuntu your speed will probably increase, if not then the install hasn't worked!

Let us know the outcome....

---

### Post by xiangcao on 2008-02-07
ya. thank you for both of you reply me.
I'm sure that the ubuntun already install in my hard disk, I'm not using live cd, because i not put any cd into my driver.
i'm use Wubi 7.10 to installubuntu, it does'nt require to partition my harddisk,
but it seem like install with Wubi is the main cause of making ubuntu run in slow speed, and maybe that's the reason you guys say that fstab seems a little strange to you.

i try to install with cd, but the speed is extremely slower than the using wubi.
i click next to choose location need to wait 6 minutes....
is that the problem of i burn into CD-RW?
later i try to burn into CD-R, maybe the speed will more faster.

---

### Post by perfecttao on 2008-02-08
Not sure that's gonna be very fast, my friend.  That would explain the lag.  Basically you are trying to run an operating system as an application.  Thats bound to result in performance issues!

As mentioned on the wubi wiki :-

> Also run chkdsk /r from windows. Defragmenting also helps.

It might also help having more RAM if possible?

Try to run the system as a livecd - if it's faster you might want to try a full install of Ubuntu....it's fun, and it's possibly the best way to learn Linux!

---

### Post by xiangcao on 2008-02-09
i have tried to run the live cd, the speed is so slow.....
when i clicked the firefox....it take so long time to load.....
i try to run xbuntu, the install process also slow like ubuntu.....
i take 2 hours to arrive the partition part, and then stuck at there 30 minutes.....
i know it will take extremely long time to wait it copy the file to hard disk when it install....so i give up and restart the pc....and then use xp online come here asking help....

hwo to install ubuntu or xbuntu smoothly ?????

---

### Post by mike555 on 2008-02-09
You should install more RAM , even XP would run better , and it doesn't cost much ......

---

### Post by #Reistlehr- on 2008-02-09
you can always try using the alternative cd. It's a menu-based install - no gdm/x

---

