---
title: "network file server questions"
date: 2007-12-07
forum: General Help
---

### Post by bluepowder7 on 2007-12-07
i'm running out of space!  i'm downloading and mp3'ing way too much stuff (around half the work is turning my CD's into MP3 / Ogg files to listen to while on the computer and to keep me from having to shuffle around actual CDs).

where was i?  oh yes, i'm out of space.  my laptop hard drive is just about full.  my desktop has its own drive for the OSes and stuff.  i've got 3 other hard drives kicking around AND i need to buy at least 1 more hard drive to store all this garbage on.  how do i do that?  i think what i'm trying to build is a network file server, but there's a bunch of features and details that i'm not sure about.

there will be at least 2 computers using the network storage - i don't need to set up quotas or anything like that, just want to be able to access any file from either computer - read and write and delete and create.  basically, i want all my files to reside on the network storage machine (word documents, pics, movies, tunes, firefox bookmarks [that may be pushing it, but you get the idea]).  i will probably also move the saved files from the laptop to the network file server, and only "copy" a file to the laptop if i need to take it someplace with me (like a few tunes and random docs when i travel).  how easy is this to set up?  what OS does the NFS machine need to be running?

i currently have 3 "spare" hard drives, a 40G, 120G, and 250G.  they're all IDE, though.  they have some stuff already stored on there, so they'll be used almost as-is, with whatever files i've already put on them over the years.  one of them (the 40G) is gonna need some cleanup since it was previously used as a WinXP OS drive, but i can probably move the files over and the format the crap out of it.  whatever NEW drives that i buy are gonna be SATA, though, so is there any problem at all in mixing IDE and SATA?

i want all the drives in that network box to be one giant drive.  i really don't want to deal with having to mount 4 (or more) individual drives.  how easy is this to accomplish within the file server machine?  i'm thinking that any PC that's networked will see the collection of random sized drives as one big chunk of storage, i'm guessing 910GB if i use my 40G, 120G, 250G, and buy a 500G SATA.  easy to do?  i haven't planned on any kind of redundancy, but if there IS some level that i can achieve then it would be nice.  if it means that my 910G potential size is only gonna be 120G, though, then that's a no-go and i'll deal without redundancy to keep the size up.

i assume i'll need to install some software on each PC (and each OS in multiboot scenarios) to be able to get at the files.  do i use SAMBA on each machine for this?

oh, and since some drives are older and have been used a bit, they might croak in a year or two.  and i might also realize that i need yet more space.  how easy is it to add / remove drives to the "tree"?  i figure the 40G is gonna bite the dust first, so MAYBE i'll use it only for the OS and not for storage (lotsa unused space, but whatever, it's on 40G).  but, if i buy another 500G or a 750G in 6 months, i want to be able to add it to the file server fairly painlessly.  is that possible?  and, if a drive IS about to go sour, how easy would it be to move the files off of it and remove it from the "array"?


lotsa questions, i know....

---

### Post by underdog512 on 2007-12-07
I would suggest that you use Ubuntu server.  I suggest using 6.06 because its and LTS.  Its always nice to have a stable platform for your servers.

---

### Post by bluepowder7 on 2007-12-07
um...  ok.  but what about all of my questions and concerns?  the ubuntu page doesn't tell me squat about what the server release does, so i don't honestly know if it'll do what i need or what my limitations are gonna be.

i thought a bit more, looked at what i currently have, and i think i'd like to make this NFS box also behave like a printer server since my hp laserjet is parallel only.  i figure what i'll do is use the mobo+cpu+ram from my current desktop, mount it into a larger case so that i get more hard drive bays, and set it up using [[INSERT NAME OF OS THAT I SHOULD USE]] and configure it as a file and print server.  then, buy a current generation mobo+cpu+ram and stuff it into the desktop and revive it.  might as well put the more basic hardware into a server box.

so...  um...  back to my original questions.



what OS and software packages do i need to install so that:

* i can mix IDE and SATA drives into one giant strage block (ok, i can deal with two blocks - an IDE block and a SATA block, but each is gonna be made up of 2 or more drives of various sizes)

* i can add more drives to the block to expand my storage, and it'll just do a nice simple NEW STORAGE = OLD STORAGE + CAPACITY OF NEWLY INSTALLED DRIVE, and i don't need to change anything on any of the networked PC's (i can deal with a small bit of configuring on the server box)

* i can remove dying drives and move their contents onto one of the healthy drives, and none of this is noticed by the other computers using this server box (so, transparent file locations hard drive arrangement)

* i can run this headless, so no monitor, keyboard, or mouse - just boot it up once and leave it on 24/7 for months and months on end, maybe even have the OS installed onto a small USB stick

* i can hook up that parallel printer so that i can print to it from any other PC that's on the network

---

### Post by bluepowder7 on 2007-12-08
bump?

---

### Post by bluepowder7 on 2007-12-08
still nothing?  c'mon, it's not like i'm asking how they got the soft chewy caramilk inside the caramilk bar...

---

### Post by bluepowder7 on 2007-12-09
well this sucks...  guess nobody knows how to use multiple disks for mass storage.  hmm...

---

### Post by graphius on 2007-12-10
I have been using SME server, especially since it sets up a raid automatically. If one drive dies, I don't lose any files.

---

### Post by bluepowder7 on 2007-12-11
> **graphius said:**
> I have been using SME server, especially since it sets up a raid automatically. If one drive dies, I don't lose any files.

all RAID schemes i've seen so far work on same size disks, which doesn't work for me all that well since each of my drives is going to be a different size.  i've got a 120G and a 250G, and going to try to pick up some 320G or 500G drives to start.  if i deploy all of those, any RAID scheme is gonna call my 320G drive a 120G since that's the smallest drive in the pool.  i can always partition them to have a lot of 120G slices to make maximum use of the space available, but that kinda shoots redundancy in the foot if i have 4 partitions on one physical drive -->  when one gets hosed, the other three are gonna get hosed too.  not exactly redundant.

is there ANY sort of scheme (in software) that would spread files over whatever drives are available, regardless of drive size?  maybe something like a RAID 5 that says "hey, that drive is full, so i'll put the remaining bits on some other drive".  obviously, it would have to be smart enough not to split any incoming file into the same number of chunks as there are drives.  i figure something like "split into three chunks and scatter over the 7 available drives" would work.  maybe - drive 1, 4, and 7 for the first file, and drives 2, 5, and 6 for the next file, and then drives 1, 3, and 5 for the third file, and so on.

also, i'm not sure how a RAID 5 would react when a new drive is added.  lets say i start with 3 drives and set them up as a RAID 5 array.  in 3 months, i'll run out of space so i'll want to add one or two more drives to the pool.  is the software running going to be smart to say "hey look - more space to spread myself onto!" and make use of the space automatically?  and, would the files that were spread over the first 3 drives continue to exist just as they were?

---

### Post by graphius on 2007-12-12
you can set up the SME server with one drive (or pick up a cheap second drive to raid) and then add the additional drives as single drives. For some reason I seem to collect drives so I swap out my drives with larger ones regularly.
The SME forums are almost as helpful and friendly as the Ubuntu forums...
Alan

---

### Post by fjgaude on 2007-12-13
raid5 puts enough of the same data on all disks through the use of parity, so that the array can still run if one drive fails. I know of no software that can do what you wish in raid or otherwise.

The 120G drive is likely getting old and not as fast as any 320 or 500 you might buy today. Speed is the issue along with reliability. Three 320s is a lot of storage for other than commerical databases.

---

