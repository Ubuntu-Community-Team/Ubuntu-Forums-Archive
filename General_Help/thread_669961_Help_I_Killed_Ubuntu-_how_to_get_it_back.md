---
title: "Help I Killed Ubuntu- how to get it back?"
date: 2008-01-16
forum: General Help
---

### Post by Dunover on 2008-01-16
Hi All!

First I have been tested and setting up ubuntu and had it perfect today...then decided to try to get nvidia card working ( BAD IDEA) long story short that driver killed my ubuntu from booting.ANYTHING.....after working all afternoon was able to now get the live CD to boot, but I did loose GRUB

This is what I have Win2k on the whole master.( some room available if need be ) and Ubuntu 7.10 installed on slave, all to itself.  I can now boot to a live cd and get to an install screen. I attempted to gain my orginal  install and copy and paste my "home" folder, but kept getting a you are not authorized message

what I would like to do is some how gain access to the old install I had this morning? can this been reset up again? Meaning the grub part? now that is gone?

I did try to do like a repair install from the live CD, and copy my settings over to a new install, but stopped. it now only wants to be installed on the master not the slave. am worried about loosing my fun stuff had installed

Am very, very green and new to ubuntu but can follow detail instructions

Can I save my "sweet" from this morning ubuntu install?  If not, how is best way to do a new install and get as many of my settings moved over

Thanks for a great product and your help in advance!

Corisa

---

### Post by cdaringe on 2008-01-17
Take a breather, well get'er back.
First, installing your nvidia card shouldnt toast your grub...it would toast what is known as X.  X is essentially the window system.  its what enables picture to show up on your screen (well...the pretty pictures for that manner. everything that doesn't look like an command line or MSDOS prompt).

So. we have two goals.
Restore your GRUB,
and restore your X.

1)  Restore your grub
visit: [http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)
Read the post by wernst
its pretty short and sweet.  follow his instructions and it should get your GRUB boot loader back up.  RATHER than typing 'su,' then typing 'grub' when he tells you to, TYPE 'sudo grub' then your password.
bingo. when you boot back up, you should see your grub

2) Now, boot into recovery or command prompt... i forget what it says exactly in the menu.  the one thats NOT the standard ubuntu, memtest, or windows.
run this command after you have logged in at the prompt

dpkg-reconfigure -phigh xserver-xorg

what this little feature does is reconfigures your graphics for you.  when it pops up select the nv driver, then just make your way though the rest of the program.  most of it is pretty self explanatory. if you dont know the answer to something, just go with the default!
when it asks if you want it to save. hit yes.

now

sudo shutdown -r now (restarts the computer)

then youre good!
what kind of nvidia graphics card do you have?
this may help us install the driver. it ought be fairly painless these days.

---

### Post by kryth on 2008-01-17
I hope your system restored. But a friendly piece of advice is to learn how to back up your system. I'm new to linux/ubuntu, also. And I've had to restore my system atleast 7 times. It's nice not starting from the begining everytime you tank the system. I used imagepart. 

[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)


But it's not very user friendly. Atleast to me. But once I got it to work, I loved it.  It's sorta like Norton ghost. 

Here's a HOWTO

[http://ubuntuforums.org/showthread.php?t=287522](http://ubuntuforums.org/showthread.php?t=287522)

hope that will help....in the long run :)

---

### Post by Dunover on 2008-01-17
Thanks did all that nut Now ubuntu will not load graphics mode, I only get the comand prompt log in
I am sure it is really broken :( and I had it perfect...

How can I reinstall ubuntu and recover some of my settings?  Do ubunut have like a recovery or repair function?

Cori

Will post about the card later

---

### Post by cdaringe on 2008-01-17
When you say you can only boot into command prompt, do you mean the option for graphical ubuntu did not show up in GRUB?  or do you get some sort of error? ..."wrong setting...missing file...etc."  if thats the case and you can quickly post some of that, it might be way faster than doing a system reinstall.

im not entirely aware of any complete graphical recovery program...but someone else may know a bit more.

if you really want to reinstall and still snag your files, there a few things you can do.
1) boot from windows. install the program found here:
[http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm](http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm)
you can access your linux files from here, and save them to your windows hard drive
2)boot from your ubuntu live cd.  here you could mount your hard drive, snatch some files from it...and do whatever you need to do.  mounting it is pretty easy, but i have to jet out of here RIGHT now...sorry i cant finish.. might be able to later today

---

