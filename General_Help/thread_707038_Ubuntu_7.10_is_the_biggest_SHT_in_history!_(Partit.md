---
title: "Ubuntu 7.10 is the biggest SH*T in history! (Partitions on your HDD? Forget Ubuntu!)"
date: 2008-02-25
forum: General Help
---

### Post by AL888 on 2008-02-25
Ubuntu **INSTALLATION is the biggest SH*T** I have ever seen!

On my main (build in) hard drive I have OF COURSE several partitions. 
One for windows, one for data, one fore email, one for backup etc...

Making **at least 2 partitions** (to separate OS and data) 
is the FIRST thing every sane PC user must do! 

I repeat: 
It is the FIRST thing, that every sane PC user MUST do:
Create at least 2 partition to separate OS and data. 

Now, what is Ubuntu saying to that?

I was just trying to install Ubuntu and I was shocked by this FACT: 
**[SIZE="5"][COLOR="Red"]Ubuntu 7.10 is _NOT_ for sane users. [/COLOR][/SIZE]**

Note: 
This is not an assumption. This is a FACT. 

And why is it a fact? 
Because its simply NOT possible to install Ubuntu 7.10 on my PC 
without DELETING all other partitions that I (as every sane user) 
created for data, backups etc.

That means: 
Using the installation CD I can ONLY install Ubuntu 7.10 
IF I agree to **DELETE ALL MY DATA AND TO DELETE ALL MY BACKUPS!!!**

Now, does anybody believe that a sane person 
would ever agree to that??...


So, I WANTED to install this piece of **** 
and it took me a lot of time to prepare my hard drive (i.e. make enough space). 
And now I am totally disappointed how **STUPID** this ubu thing is!!!

How stupid are the Ubuntu developers to assume 
that everybody just have one hard drive without any partitions on it???
It's not possible to be any dumber. 
I'm very disappointed right now with this piece of SH*T!

---

### Post by AL888 on 2008-02-25
Note: 
I tried several options.

First thing was, I created a (Linux) partition and a swap partition (using PartitionMagic in Windows)
And then I was trying to install Ubuntu on those partitions. 
I assigned manually the right partition for ubuntu and set the "Mount Point" to "/".
The swap partition (500 MB) was recognized automatically as such. 
I went the whole 7 step pre-installation process 
and at the end I saw that: 
[B][COLOR="Red"]WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.[/COLOR][/B]

Holly SH*T! I'm glad I can read. 
Because that message was NOT in red and not even in bold. 
No, that was just an ordinary text message among all other text!!! 

I know for sure, that MANY people don't read every thing when installing stuff. 
Many people just click the forward button. 
So, I am curious how many people have already deleted all their data (on different partitions of the same hard drive) with this sh*t?

Listen: 
I could not believe that ubuntu developers would be soooo f*cking stupid 
to not allow to install this thing on a hard drive that already has several partitions (for data etc.)
**[SIZE="5"]I could not believe that! [/SIZE]**

I checked Google and saw some forum posting telling people (who have - like me - 
done some good preparation before installing and created a Linux partition - along with a swap partition - using PartitionMagic on Windows) 
that forum posting was telling people to go back (on Windows), 
open PartitionMagic again and delete those newly created partitions for Linux. 
And then let Ubuntu's build in thing make its own partition on a hard drive part with the biggest free space. 

So, I went back, deleted the Linux and the swap partition, 
and added the free space to the main (C) partition (hoping that now this thing will work).

Well, I tried it again and shockingly there was not much difference!!!

Ubuntu recognized that there is a part on my hard drive that has windows on it. 
But the dumb stupid ubuntu thing had no idea about my PARTITIONS on that hard drive!!!
**Partitions with VERY valuable DATA AND BACKUPS! **

HELP!!!
Does it get any dumber???

And... just in case someone would suggest something stupid like: 
"Save all data and backups on CDs or DVDs..." 

**My answer is: HELL NO! That is not an option at all! **

If you have just 2-3 GB data, then it might be an option for you. 
But not if you have 200-300 GB data... 
Also, right now I don't have any hard drives with so much free space. 
(all my external HDDs are pretty full)

---

### Post by AL888 on 2008-02-25
I just want to give a hint for sane people: 

[**[SIZE="5"][COLOR="Blue"]_Ubuntu 7.10 is NOT for sane users!_[/COLOR][/SIZE]**]("http://ubuntuforums.org/showthread.php?p=4399631#post4399631")

And in case you thought, it would be a good thing to have something that 
"just works"...
I this case I must disappoint all sane users: 
**Ubuntu just does _NOT_ work! **

It doesn't work at the very first step! 
If you have partitions with data on your hard drive 
[B][SIZE="3"][COLOR="Red"]Ubuntu wants you to agree to DELETE all your data partitions 
before you can install it![/COLOR][/SIZE][/B] 

That's no joke! 
Click that link above and read my whole post about that SH*T! ](*,) :frown: :x

---

### Post by jeffus_il on 2008-02-25
I believe I am sane and I run 5 home computers with Ubuntu, and no such problems.
but I will not reply in the spirit of your post and imply that you are insane, I will just say that I think you are making a mistake and their are better ways to solve a problem with Ubuntu, and if you are not interested, Bill Gates will be happy to accept your few dollars.

---

### Post by dohko_xar on 2008-02-25
It is recommended to have at least some _minimal_ knowledge about computing for the person that is going to do the install...

Ubuntu doesn't want to delete your HDD, all it wants is a couple of GiB's where it can install itself. If you are smart enough, you can shrink one of the already existing ones and let some space for Ubuntu.

---

### Post by jrusso2 on 2008-02-25
And the reason you are reposting it is?

---

### Post by NineseveN on 2008-02-25
Um, no. Sorry, you're either misunderstanding the message/partitioner or we're not getting the full story (your complete disk set-up of primary VS extended partitions/logical drives etc...).

The partitioner in the Ubuntu install does indeed format the partitions you are assigning for Ubuntu, but it does not, I repeat, it does not automatically format/delete or even resize any partition other than those you've selected for your Ubuntu unless you tell it otherwise. Tens to hundreds of thousands of people run dual-boot systems with Ubunutu. When I installed Ubuntu for the first time (7.10), it left my Windows XP primary partition and my data backup partition alone on my primary HD...it also didn't touch my 300gb of data in 7 other partitions on 2 separate disks. My latest install, on an HP laptop, it left the HP restore partition completely alone.

Perhaps someone could walk you through the process, I fear you're either doing something ill-advised or misunderstanding the partitioner/install process.

Good luck.

---

### Post by deepclutch on 2008-02-25
well,what I do is to  not to depend upon partition manager for "guided partitioning" as u does.
when the partition section reaches,I select  "manual partitioning" and runs gparted to create ext3 for / and a 300MB swap :p

yes,Ubuntu by default tries to add all the other partitions to be auto mounted.but..wait [COLOR=Red]**IF U R NOT CAREFUL AND DO A "TICK" ON INSTALLER,THAT PARTITION OF URS WILL BE DELETED FOR ETERNAL!.**[/COLOR]

Ubuntu is a gr8 distro!still I feel Ubuntu alternate CD is what is better as an installer as it uses Debian CLI installer(better and bug free).
that says-go on try!

---

### Post by AL888 on 2008-02-25
> **jeffus_il said:**
> I run 5 home computers with Ubuntu,
In this case either all those 5 computers were brand new (or had fresh formatted hard drives)
or you have never heard of a thing called "partition" before and why every sane person should use partition to separate OS and data on their computer (thus you've never used it on your "5 computers").

---

### Post by NineseveN on 2008-02-25
AL888, it sounds like you're misunderstanding the install process/partitioner. Perhaps you'll find some help in the other thread you created about this if you'd sit back, take a deep breath and listen and learn?

Either way, happy travels.

---

### Post by AL888 on 2008-02-25
> **dohko_xar said:**
> It is recommended to have at least some _minimal_ knowledge about computing for the person that is going to do the install...

Ubuntu doesn't want to delete your HDD, all it wants is a couple of GiB's where it can install itself. If you are smart enough, you can shrink one of the already existing ones and let some space for Ubuntu.
Thanks, 
I even have some intermediate (for some people even advanced) knowledge 
about computing and such. 

THIS message from the last step (while trying to install Ubuntu 7.10 from CD): 
> [B][SIZE="4"][COLOR="Red"]WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.[/COLOR][/SIZE][/B]
That message clearly tells you that "This will destroy all data on any partitions you have removed as well as on the partitions that are going to be formatted"

[B]Can you read? 
Or would you rather trust your "minimal knowledge about computing" 
and hit the install button after reading that message???[/B]
No sane person would!

---

### Post by AL888 on 2008-02-25
> **NineseveN said:**
> Um, no. Sorry, you're either misunderstanding the message/partitioner
No, I'm NOT misunderstanding anything! 

I am able to read and this message: 
> [B][COLOR="Red"]WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.[/COLOR][/B]
cannot be any clearer!

---

### Post by AnRa on 2008-02-25
I think a sane person would read [THIS](https://help.ubuntu.com/community/GraphicalInstall) and maybe realize that it has made a mistake (hint: "Manually edit partition table").

---

### Post by AL888 on 2008-02-25
> **deepclutch said:**
> well,what I do is to  not to depend upon partition manager for "guided partitioning" as u does.
when the partition section reaches,I select  "manual partitioning" and runs gparted to create ext3 for / and a 300MB swap 
You obviously haven't read, what I wrote above?...

The manual thing is what I tried FIRST!

That is where I got this very nice message: 
> [B][COLOR="Red"]WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.[/COLOR][/B] 

---

### Post by soldats on 2008-02-25
Please don't respond to trolls. Let us end this now.

---

### Post by AL888 on 2008-02-25
> **NineseveN said:**
> AL888, it sounds like you're misunderstanding the install process/partitioner. Perhaps you'll find some help in the other thread you created about this if you'd sit back, take a deep breath and listen and learn?

Either way, happy travels.
I am misunderstanding? 
No, I just can read. 

Tell me, what does this message say to you (that appears on the last page before hitting the final install button: 
> [B][COLOR="Red"]WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.[/COLOR][/B]

Now, who is misunderstanding what??

---

### Post by aysiu on 2008-02-25
This belligerent attitude and inappropriate language is not in accordance with the forum rules. I'm closing this thread and issuing a warning. Please, if you want help, AL888, ask for it nicely, and you will receive it. If not, you will receive an infraction.

---

