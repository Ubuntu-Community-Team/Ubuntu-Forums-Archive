---
title: "URGENT - annother one sorry!"
date: 2007-02-13
forum: General Help
---

### Post by KAL9000 on 2007-02-13
I seem to have accidently deleted a partition with windows...

I dont know if it was a bug or what. I went to delete R: logical and it also took F: with it aswell.

what I need to know VERY derperatly is what programs can i use to recover that partition
(nothing so far has been written to the drive) and ATM its still un alocated. it is the last 60GB of my drive I KNOW (not the exact point) where it is but how can i get it back.

abit of info:

My drive was a 200GiB maxtor broken into :

10GiB for windows
<extended partition starts here>
60GiB for programs 
40GiB old docs and media drive (the acctual partition I needed to delete)
30GiB unallocated here
60GiB for a reposotory of the other drive and a few backups (which also got deleted)
<end of drive>

now it is:
10GiB for windows
<extended partition starts here>
40GiB for programs 
150GiB unallocated space
<End of drive>

any help would be vastley apreciated theres 40-50GB of backup and media on there!

---

### Post by KAL9000 on 2007-02-13
Bump...surely someone can help...

Its not a drive error. its just the partition was deleted on the drive by mistake. surely theres something. after looksing i can only find things that charge or that are talored to work with dead drives.

This is a very urgent matter if ANYONE can help. something to edit the partition tablels to get it back.

I know the partition was right on the back 60GB of the drive, is there anyway of making a new partition "over" the area and the files can reappear?

---

### Post by Soulxlight on 2007-02-13
Google this, and you will get tons on this subject :D

recovering an accidentally deleted partition

---

### Post by finferflu on 2007-02-13
It sounds like a problem I have had... I actually gave up the recovery, but there is a tool for that.
Look at this thread: [http://www.linuxquestions.org/questions/showthread.php?t=456880](http://www.linuxquestions.org/questions/showthread.php?t=456880)

hope it helps...

---

### Post by meng on 2007-02-13
I don't know the answer, but don't go making a new partition "over" the old one, that sounds to me like a recipe for ensuring that the files are even less recoverable!
It might help to explain exactly what went wrong with your repartitioning within Windows. What tool did you use to delete the partition? Are you sure you didn't delete the extended partition, thus automatically deleting the logical partition inside it?
Also, I understand why you want help quickly, but be aware that acting in haste, on bad advice, is the surefire way to reach a bad outcome (that is, loss of data). What you need to do is learn exactly what to do (or else enlist the help of a professional). One false move and you're more screwed than you are now.

---

### Post by r4ik on 2007-02-13
Try,

[http://servers.linux.com/servers/06/08/21/1558230.shtml?tid=119&tid=13](http://servers.linux.com/servers/06/08/21/1558230.shtml?tid=119&tid=13)

Good luck !

---

### Post by KAL9000 on 2007-02-13
Well as an update I found a demo software thing that tells me the lostpartition is at:

(starts "C 16960 - H 1 - S 1" Size 61436 Mbyte)

where I assme the C H and S means clusters/heads/sectors

Also the files are intact within the partition still as this same program can "see" whats in the partition.
im going to look through those links. I've not been able to do much since my post as for some reason my router factory reset itself when I was portforwarding :confused: 

Thanks for any help you guys can post.

p.s. is is possible with the information this program gives me to manualy edit the partition table to "write" it back in as it were?

or program where if I feed it all that it can make it.

The worst thing is im not sure what was on there "docs backup" had anythisn massiveley important. but theres always the chance there is.

---

### Post by r4ik on 2007-02-13
Looked around and found this

[http://www.ubuntuforums.org/showthread.php?t=354069&page=2&highlight=data+recovery](http://www.ubuntuforums.org/showthread.php?t=354069&page=2&highlight=data+recovery)
Post #15 seems to be of interest.

Foremost is a tool to recover files. It works very well, even if the partition is gone. Just run it on the raw drive.

You will need to mount a drive somewhere where the recovered files can be saved.

You can run the Edgy live cd and install and run it. Just enable universe and install foremost

then, mount your hard drive to save the files to (for example /saved) and run

sudo foremost -o /saved -i /dev/sdb

[http://foremost.sourceforge.net/](http://foremost.sourceforge.net/)

Good luck !

---

### Post by KAL9000 on 2007-02-13
How can I mount non allocated space?

Ive had to shut the PC down as its abit late, but it will still be fine wont it. do any programs write to the end of the disk even if its unallocated?

I think when/If i get the contents of that drive back it will be a Totaly new system. reorganised so Nux is all mounted properly and XP is happy and they can both use the same drives (the aim of what i was doing in the 1st plase)

Im just concerned as I cant rember what exactly was in the folder. but i get the feeling it was important. Ive thaught maybe just leave it but i keep thinking of that file and theres someting in there i know i need :S

as said if none of this stuff works is manual editing of the table poissible?
I know one of my friends said you can totaly F the disk in like that. and turn whole sections unreadable :S

---

### Post by r4ik on 2007-02-13
"as said if none of this stuff works is manual editing of the table possible?"

Don't know have to look into that.
Looking the timezones we are in a bit of sleep seems a good idea to me.
Be back in a couple of hour's.
Maybe others would be so kind to look into the matter in the meanwhile.
Thanks !

---

### Post by r4ik on 2007-02-14
Can't come up with a solution sorry.
One thing you could try is Plan B

[http://www.projectplanb.org/](http://www.projectplanb.org/)

Good luck !

---

### Post by KAL9000 on 2007-02-14
Right...I've got a program called "Norton Partition magic" and it just says my 200GB drive is "bad" but doesnt say why or what I can do. This is stupid. 

I may have alook now at the Linux based one. maybe have more luck with that...

---

### Post by finferflu on 2007-02-14
As suggested, foremost seems the most appropriate one..

---

### Post by r4ik on 2007-02-14
Gpart,
A partition labelled "orphaned" is a logical partition which seems ok but is missed in the chain of logical partitions. This may occur if a logical partition is deleted from the extended partition table without overwriting the actual disk space.

[http://linux.softpedia.com/get/System/Hardware/Gpart-12102.shtml](http://linux.softpedia.com/get/System/Hardware/Gpart-12102.shtml)

Maybe worth looking at....

---

### Post by r4ik on 2007-02-14
It has been suggested twice but it is not up to me/us

---

### Post by KAL9000 on 2007-02-14
Well it didnt seem to work. seems that disk was damaged.

I would guess thats what caused this in the 1st place. Several utilities have listed my Maxtor as "bad" and Gparted says it couldnt make partitions. Ive notgot enough allocated space to run any other recovery methods. as that drive was 58GB.

I also think the problem is that it was a Logical drive in an extended partition. so using that "gpart" doesnt guess that partition as correct.

Looks like its a new install Ahoy. XP boot disk here I come, and I wont trust that to partition it again. fraid I will make the 10GB for XP and thats that! then I will use Gparted tomake the rest as I need it, by the look of it theres free space between the 1st primary partition and the extended partition where there is meant to be none. this is ether the Windows setuppartition having a bran fart at the time OR a disk error.

ether way I think a total stripout of the drive is in order. using primary partitions rather then extended ones so it makes any future need to recover ALOT easier. 

while looking through all the things I have on the matter it seems to suggest that Extended paritions are nowhere nearas robust as primarys and its 1000 times easier to recover a primary.

Thanks for all the help guys. i did try loads of different things but i ether dont have room or the utilities say the drive is "bad" due to the gaps between partitions (100's of MB in the case of the gap between the pri and the ext!

Im going to guess that there wasnt anything important on there :S

Just in case I will be installing BOTH Ubuntu and XP on the newer 40GB drive and use my 200GB as a reposotory untill i can afford to replace it.

Is it more advisable to have both OS's on one disk?

---

### Post by r4ik on 2007-02-14
Sorry to hear it could not be restored.
If you are going to use the 40g install Ubuntu after Windows.

"Is it more advisable to have both OS's on one disk?"

I find it more easy.

Good luck !

---

### Post by ghandi69_ on 2007-02-14
Depending on how important your data is.... I have a bad drive with about 100 gigs of music/movies/illegal copies of windows programs... on it, and software for windows such as stellar phoenix and D.A.R.T sumthin or another were able to recover my data, even though my partition information amongs other things were damaged...

Only problem... they cost about 50 to 70 bucks if you can't get a crack for em..

---

### Post by KAL9000 on 2007-02-14
Im too cheap to pay :P

Besides its already done. damn drive. I hope its atleast fine now theresno partitions on it anymore. I may have norton disk doctor go through it all and seeif theres any crap on it.

Ive got Windows up on a 10GB part of the 40GB drive. then install Ubuntu on annother 10GB part with home mounted on that. then ill have the 200GB parted and mounted in home.

now the parts mounted in home will also be XP drives so they will be like D: <documents> and /home/user/docs depending what OS is loaded.

---

### Post by meng on 2007-02-14
> **ghandi69_ said:**
> Only problem... they cost about 50 to 70 bucks if you can't get a crack for em..
And of course that's illegal and we don't condone that here.

---

