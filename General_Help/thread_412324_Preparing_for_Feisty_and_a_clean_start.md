---
title: "Preparing for Feisty and a clean start"
date: 2007-04-17
forum: General Help
---

### Post by dryder on 2007-04-17
Hi,
Please bear with me ... apologies for the long post. :oops:

OK, my initial 'experiment' with Ubuntu (linux) has convinced me to switch over completely. As I have severe problems since the last update (see "I think a config file is corrupt - help please?") which nobody has been able to help me resolve (that's not a complaint nor a snipe - the Ubuntu community helps a LOT) I think it best to 'start again' when I install feisty.

So, I am asking advice on a good partitioning strategy please.

I use a (virtually) paperless office approach for a business which creates a lot of  documents and large databases  so rely on large Document and Database folders and regular backups to dvd in case of disk failure. I also do dvd work for which I use dedicated drives.

My beginner's setup was (is):
/root       PRIMARY      7.45GB
/home    PRIMARY     14GB
/data      PRIMARY      57.25GB
/store    EXTENDED   250GB for dvd work
/swap   EXTENDED    4GB

I thought /data  would hold my Documents and Databases but they are in /home/Documents and /home/Databases as $HOME always seems to be the default starting point when saving files. So I am thinking of combining the GBs for /data into /home. Though I would prefer a separate partition on a separate disk for this data primarily because a separate disk for the Documents and Databases would be 'tidy'.

I also need a unique partition while I migrate all my data from MS into Ubuntu as it will need to be converted and checked for integrity for use in Ubuntu. Then ... out goes MS ....

I will have 2GB of RAM. So, the new partition thoughts I have, hoping I am using the KISS approach, are:

/root        PRIMARY        20GB
/home     PRIMARY      100GB
/store      EXTENDED   250GB for dvd work
/swap     EXTENDED       4GB
/migrate  EXTENDED     50GB - the space to be later combined with /store

Please, can any more experienced users give me their opinions on this approach? Making the move will involve a lot of work and I want the best partition assignments I can.

Does anything other than /root need to be a primary partition?

One last question: can I move the data in my /home directory to another disk which is linux partitioned while I format the original disk for Ubuntu and then simply copy the data back into the new /home folder?

Many thanks,
David

---

### Post by WiseElben on 2007-04-18
I would think twice before putting only 20gigs to root. Yes, it's root and would only hold the program files, but keep in mind that the root partition would be the hardest to modify after you installed Ubuntu. I'm glad you decided to merge /data and /home, because that's what /home is for, to store personal data. /swap is fine, but some would say twice the amount of RAM is unnecessary, but I do it anyways; I don't take any unneeded risks.

> can I move the data in my /home directory to another disk which is linux partitioned while I format the original disk for Ubuntu and then simply copy the data back into the new /home folder?

Of course, it just might take a while.

---

### Post by ardchoille42 on 2007-04-18
More than 2Gb swap is a waste regardless of how much ram you have, on my opinion. I have 2Gb of ram and I rarely use my swap.

---

### Post by dryder on 2007-04-18
Thanks WiseElben and ardchoille42,
> 
Of course, it just might take a while.

Is there another way?

> More than 2Gb swap is a waste regardless of how much ram you have, on my opinion. I have 2Gb of ram and I rarely use my swap.

I had noticed my present swap file is rarely used - if ever ...
 
David

---

### Post by Neobuntu on 2007-04-18
I think we can greatly simplify, depending on what you need.

What files systems are you planning on using, on these partitions?

Are those partitions or are some separate drives?

Do you have USB 2.0 or could you add it for fast access to external, universal (Fat32) drives. Both big externals and USB sticks. Did you know that 4GB solid state USB flash drives are under $40 now and are MUCH faster than DVDs and much less picky. You can't scratch them and they are supposed to read/write more without failure, than hard drives.

HOLD ON: I wouldn't put my business on Fiesty yet. In fact for business, I'd stay with Dapper LTS.

---

### Post by dryder on 2007-04-18
Hi Neobuntu,

I won't be rushing into feisty, but (as per my first post) I have seemingly unsolvable and critical system problem since the last update (may be coincidence), refer post _[http://ubuntuforums.org/showthread.php?t=410482](http://ubuntuforums.org/showthread.php?t=410482)_ so a reinstall of at least edgy, which I've used successfully for some months, seems to be required. If I need to reinstall then I would like to restructure the partitions.

> What files systems are you planning on using, on these partitions?

ext3. If there is a better one for dvd files then I'll use that on the /store partition which is a separate drive.
> 
Do you have USB 2.0 or could you add it for fast access to external, universal (Fat32) drives.
No - I have SATA drives (450GB each) and don't want USB - there are too many problems when using a lot of USB devices especially if many want access to the MB ports.

> USB flash drives are under $40 now
not here (Australia) - wish they were! But my system is geared to nightly dvd backups anyway and I would need a lot of testing with memory sticks being left in overnight. Manual backups, if required during working hours, go to hard disk in the background. I guess memory sticks could be a medium in the future.

David

---

### Post by username132 on 2007-04-18
If you already have Windows license(s), I would maintain a small Windows installation, just in case. You can set the default OS to boot as Ubuntu and all your data can be in the ext3 format. I use the fs driver ([www.fs-driver.org](www.fs-driver.org)) to allow Windows to read and write to the ext3 partitions that I choose (the data ones, not the OS ones).

---

### Post by dryder on 2007-04-18
Hi username132,
> I would maintain a small Windows installation, just in case.
I think I will have to during the transition and until I can find a d****d good scanner that works in Ubuntu (my current one doesn't).
Unfortunately MesS has to be the first drive which is the most inconvenient factor as when it goes altogether I will have to do this all over again putting Ubuntu on the first drive!

Thanks for the tip and link - it will greatly help in the transition. The worst thing about this is XP and earlier don't recognize the open document format. 

David

---

### Post by username132 on 2007-04-18
> **dryder said:**
> Hi username132,

Thanks for the tip and link - it will greatly help in the transition. The worst thing about this is XP and earlier don't recognize the open document format. 

David

Glad I could help! Not sure what you mean re: XP recognition of the open document format... I use OpenOffice for Windows to for all such needs ([http://download.openoffice.org/2.2.0/contribute.html?product=OpenOffice.org&os=winwjre&lang=en-US&version=2.2.0](http://download.openoffice.org/2.2.0/contribute.html?product=OpenOffice.org&os=winwjre&lang=en-US&version=2.2.0)) but I'm not sure if that's what you're getting at...

---

### Post by Neobuntu on 2007-04-18
Partitioning is foundational so it's wise to give it some thought. Yet, what's wrong with the default set up for you? 

I'm still not sure which partitions you envision are totally; separate drives. AKA What drives have you?

You may well have reasons that have not been expressed (or I missed) but can you tell me why you don't let *ubuntu auto configure your fastest drive (with "/" and a swap) and then use the other drives for storage in flexible ways apart from auto installation? You would still backup "/home" out of "/", right?

Sure, there may be an advantage to having swap on another drive but will you ever kick in swap, anyway?

If I used DVD much, I wouldn't bother with erasing questionable RW's. I'd just write once and maybe add to a partial DVD-R some more, or just put in another blank. But that's another subject.

It's nice to hear that you do auto backups to another hard drive and then also to DVD, That works.

I'm thinking it is not so critical to be on another partition, as it is another drive.

The whole separate multiple partitioning comes down to one of the partitions getting filled faster than if it had room to grow dynamically. 

Are you concerned about an attack making data unrecoverable (unless saved in its separate partition)? Wouldn't backups solve this unlikely event?

I think if you just make sure the folder and project you're working with resides on the appropriate drive, further partition segmentation on each drive might not be worth it. 

Again, you may have different needs.

Perhaps I can best help by steering you more toward Dapper. Edgy obviously works for you but there MIGHT be things you want to do that Dapper handles better. Overall, I'm saying we should all avoid NEW RELEASE FEVER. That's best for a separate; test install. Do you also want to allow a partition or drive for that? Segmented partition (or better drives) are best for testing other OS installs. 

Do not (dist)upgrade (unless it's on a cloned install and for testing.)

---

### Post by dryder on 2007-04-18
username132:> 
Not sure what you mean re: XP recognition of the open document format
Badly expressed, you are correct - I am referring to MesS Word 2003 and less...

Neobuntu:> Partitioning is foundational so it's wise to give it some thought.  Yes, hence this post.

> what's wrong with the default set up for you? It is not suited to my requirements - I have to change partition sizes. When I first started using Ubuntu I found this out and started again after reading a lot of posts, howtos, the wiki and asking questions on partitions. Now I am ready to commit one business machine I want to get the best but simplest structure I can for my needs and felt asking those who know more than I do (about Linux) for advice seemed a good idea. 
> 
I'm still not sure which partitions you envision are totally; separate drives. AKA What drives have you?  As Linux treats the file structure as folders, not drives, I considered this irrelevant. Which drives I can put partitions on can be done at install time.
> What drives have you? Business: three 450GB SATA striped. All are the same speed. Five more SATA drives are available to MesS and,other OS testing. This does not contradict my statement above about folders and drives - the former is simply a stament of how unix/linux differs from MesS and other OSs. This is a large system (let alone the network) but Edgy has coped extremely well. Experimenting with so many software packages may well have caused my current problem. A good fax at least equivalent to MesS Fax is the only thing I wish I had but in the meantime I'll live with efax. (See different post re HylaFax problems).
> tell me why you don't let *ubuntu auto configure your fastest drive (with "/" and a swap)I need control over which partition goes on which drive and the size of some of them due to the mission critical nature of some of the databases. Maintaining database integrity is easier that way, especially doing DVD work. This is not to be confused with my current "OS/HylaFax" problem. I have had more uptime and less maintenance with Edgy than I ever had with MesS.
> The whole separate multiple partitioning comes down to one of the partitions getting filled faster than if it had room to grow dynamically. Precisely.
> Are you concerned about an attack making data unrecoverableIf you mean malicious - no.
> Edgy obviously works for you but there MIGHT be things you want to do that Dapper handles better. Please tell me what you think Dapper does better - I'm very interested to know. There is no "fever" - only that Feisty is not a substitute (yet) but it is something to run separately and test under the same conditions - and of course learn about. There are more drives I can put in to test Feisty (or Dapper) without interfering with Edgy.

David.

---

