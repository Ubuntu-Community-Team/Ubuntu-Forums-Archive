---
title: "Partitioning advice needed"
date: 2008-03-28
forum: General Help
---

### Post by petaloid on 2008-03-28
Hey,
I'm new to Ubuntu (and Linux) and im trying to make the switch from windows. 
I got all the way up to the partitioning steps of the installation process and thats when I got confused.

Uptil then I thought I had three separate hard disks (C: which has windows installed on it , D: which has some music files, and E: which i had specifically emptied out for Ubuntu).
Before I did anything i defragmented C:, D: and E:

I saw that it detected my hard disks like so ....
[IMG]http://img.photobucket.com/albums/v202/teslaclaw/Screenshot2.png[/IMG]

I went through to my computer in WINDOWS and checked out the devices manager and saw this....
[IMG]http://img.photobucket.com/albums/v202/teslaclaw/screen.jpg[/IMG]

I think that means that the second 80 gig harddisk (ATA WDC) was prepartitioned to give me D: and E:

So that means my main questions are:

-Can I use the Ubuntu LiveCD (instead of the GParted) to accept the prepartition and get it onto E: ? -if so, can someone detail me the steps i need to take? 

-is partition #5 of sdb the same as E: ? If so should I just take the first option in the Ubuntu installation step 4? Should it be 100% of the sdb5? Does a swap get made? or do I even NEED a swap?

-this is a screenshot of what i get if i select Manual instead of Guided-whatever: [IMG]http://img.photobucket.com/albums/v202/teslaclaw/Screenshot-1.png[/IMG]

Hope ive provided enough info for you guys to help.

(P.S. for some reason ifI take a screenshot and save it in C:, then when I back track the steps to go to the Manual-way-of-partitioning then C: (where I saved the screenshot) shows Unknown Used Space)

---

### Post by imperius69 on 2008-03-28
as i am also new to ubunto im very interested in this topic couse i have similar "problem" and i would like to know how to do it!

---

### Post by CyberCowboy on 2008-03-28
You can't put the ubuntu onto drive E: because it is formated for windows, what you can do though is using the wizard resize the partions on the 80 GB drive that houses D: and E: so that you can add a 3rd (or more) partition for Ubuntu

(Hint: create a seperate partition for /home so that if you have to re-install Ubuntu like I did when playing around you save your personal files)

---

### Post by CyberCowboy on 2008-03-28
P.S. It is suggesting to resize yoru 80 GB drive in the first screenshot you posted as the top option, you can just use that if you so desire.

---

### Post by petaloid on 2008-03-28
> **CyberCowboy said:**
> P.S. It is suggesting to resize yoru 80 GB drive in the first screenshot you posted as the top option, you can just use that if you so desire.

But 54% of the 80gb hardrive isnt 18gb. I think it's referring to E:
Also how do I create a seperate partition for /home?

---

### Post by CyberCowboy on 2008-03-28
My understanding (I haven't used the resize option) is it will give you 54% of the freed space after resize, and not destroy any partitions.  And going through the Guide it will give you an option to put /home on a seperate partition.  Or you could use GParted to resize the 80 GB partitions and then manually create partitions.

---

### Post by petaloid on 2008-03-28
Gparted wont work for some reason - I keep getting stuck at the BASH place thingy because it cant open up a visual environment. Apparently for GParted to start working I have to start some Forcevideo script to configure it so i can see the visual interface.

---

### Post by piousp on 2008-03-28
If you really wanna install ubuntu under "E:"s space, what you can do is, just erased your E: partition, which is /dev/sdb5 under linux
Once you erased that, you can create new partitions for it. For example, you can create a 10GB ext3 partition for your / and the rest goes to another partition for your /home. Also, you will need some space for a swap partition. I would say 1GB its fairly enough.
Obiously, you'll need to select "Manual" under "Prepare Disk Space" to do this.

---

### Post by x1a4 on 2008-03-28
Hi,

Prepare your partition manually (using the installer) like so: 

Create a swap partition on the free space on sda
Install Ubuntu on sdb5. Use the ext3 file system; mount it on /  instead of /media/sdb5

---

### Post by petaloid on 2008-03-28
> **piousp said:**
> If you really wanna install ubuntu under "E:"s space, what you can do is, just erased your E: partition, which is /dev/sdb5 under linux


So if I erase E:, then I get my 80 gigs back as one - but what happens to D: (some stuff is already in there) ?

---

### Post by piousp on 2008-03-28
Nope, your D: partition will stay as it is. You wont get your 80 GB back either. Why? Well, to make it simple: you are using E: for another thing, and windows wont recognize it (normally, but you can install a program to read ext3 partitions in windows).

So, in windows, you'll see:

C: 37,2 GB
D: 39: GB

--- and thats it!
You WON'T loose anything under C: or D:

Now, in ubuntu, you'll see (for example):

sda: 37,2 GB
sdb 39 GB
AND
/home 35 GB

Hope this helps!

---

### Post by petaloid on 2008-03-28
> **x1a4 said:**
> 
Create a swap partition on the free space on sda
Install Ubuntu on sdb5. Use the ext3 file system; mount it on /  instead of /media/sdb5

I do all of this in the third screenshot step? Also I still want to be able to use windows... do i need to use all of the remaining space in sda for swap?

piousp , x1a4:kay ill give them a shot actually and see for far i get before getting confused again :P

---

### Post by piousp on 2008-03-28
Check out this thread, as it address the same issues:

[Install ubuntu and dual-boot vista]("http://ubuntuforums.org/showthread.php?t=736374")

[Partition disk]("http://ubuntuforums.org/showthread.php?t=345769")

Hope this helps!

---

### Post by CyberCowboy on 2008-03-28
> I do all of this in the third screenshot step? Also I still want to be able to use windows... do i need to use all of the remaining space in sda for swap?

piousp , x1a4:kay ill give them a shot actually and see for far i get before getting confused again :P

Yep all of it would be done under the manual... keep in mind the way that Piousp suggests though will give it all as one partition if you want to break home free you'll create 2 partitions where E: used to be, one about 10 GB for /  and the remaining space for /home

---

### Post by petaloid on 2008-03-29
Well it was easier than it sounded - and i decided to go about it as you guys said and it came out fine - hello and thanks from the ubuntu side of things :D

---

### Post by CyberCowboy on 2008-03-29
WElcome to the club, glad we could help out.

---

### Post by piousp on 2008-03-29
Welcome aboard!

---

