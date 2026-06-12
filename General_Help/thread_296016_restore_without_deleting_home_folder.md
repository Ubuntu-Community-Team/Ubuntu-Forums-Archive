---
title: "restore without deleting /home folder"
date: 2006-11-09
forum: General Help
---

### Post by Fittersman on 2006-11-09
i followed the how to [http://ubuntuforums.org/showthread.php?t=219336&highlight=ati+radeon](http://ubuntuforums.org/showthread.php?t=219336&highlight=ati+radeon) without realizing that laptops and desktops are so much different (i have a desktop and thought a laptop guide could work) and now im screwed here.

i was trying to get my 3D acceleration to work but now everthing is messed up. The problem seems to be tied to this forum for some reason... when i try to open a thread or post a new one the monitor either shuts off or freezes and im not sure if the computer is still working or not or it it froze too. I also have messed up font that is weird lookingish that cant be read. I am forced to use the live cd to come on this forum and get help now.

is there any way i can do any of these options??

1)restore my system to yesterday
2)undo the effects of that howto
3)reinstall ubuntu wihtout deleting the /home folder
4)anything that will save my /home folder and make ubuntu work again

and also if you could tell me how to get my ati radeon 7500 card to work properly that would be of use to me.

---

### Post by insub2 on 2006-11-09
Firsly, how messed up is everything?  whats not working?


1)to do this, you'll have had to backup you system yerturday.  if you did that, there should be something on the forums tell you how.

2)...i have no idea... there might be.

3)did you put /home on different partition?  if so, you're all set to reinstall..........but it doesn't sound like you did that.  (you should do that.) If the answer is no, my answer here depends on what is actually the matter.  I can tell you how to do this if you give me some more information:
[LIST]
[*]can you get to your /home directory now?/does ubuntu function (however poorly)?
[*]can you see them with a liveCD (you can use the ubuntu insall disk and mount your harddrive or knoppix or something.)
[*]Do you have free space on your harddrive (the size of your /home+about3G)?
[INDENT][*]If no, do you have access to another with that much space you can use?[/INDENT]
[/LIST]

---

### Post by jpkotta on 2006-11-09
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I like to use ATI's installer, but I've had success with the one in the repos as well.

You can't restore unless you backed up.  It may be tricky to undo the howto; I see a dist-upgrade in there and those are kind of hard to reverse (but it can be done).  Your best bet is to reinstall, I think.

A fool-proof way to reinstall without killing /home is to backup /home.  Now, I'm pretty sure that you can reinstall and it will leave /home untouched, as long as you don't format the partition it's on.  Boot from the live cd and delete everything on the partition except /home, and that will guarantee that all of the misconfigurations will be gone.

I keep /home on it's own partition, so I know it's always safe.

---

### Post by jpkotta on 2006-11-09
Before reinstalling, try to reinstall xorg-driver-fglrx (or whatever driver you had before) and replace /etc/X11/xorg.conf with the backup.

---

### Post by handy on 2006-11-09
I run a separate **/home** partition on both my machines always.

The way I did this the first time was to convert one of my machines using this [how-to]("http://www.psychocats.net/ubuntu/separatehome"), it worked perfectly, if your system is still functional enough to follow the how-to, then I highly recommend it!

If you don't land on the ***Create a separate /home partition in Ubuntu*** how-to, you will have to find it on the **psychocats.net** site.  They sometimes change addresses I have found, so??

---

### Post by Fittersman on 2006-11-11
i tried using gparted but it always screws up for me so i basically am now forced to reinstall and start over :'(

o well (i have high speed now :))

---

