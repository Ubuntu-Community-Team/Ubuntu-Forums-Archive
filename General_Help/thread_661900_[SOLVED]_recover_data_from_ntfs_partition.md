---
title: "[SOLVED] recover data from ntfs partition"
date: 2008-01-08
forum: General Help
---

### Post by p1977p on 2008-01-08
my friend has a laptop with  a single 40 GB windows Xp partition formatted as ntfs. the windows installation got screwed up due to some virus and it wont start  (in any mode -- dos/safe, etc). He has important data in his my documents folder (upto 6 GB). i have a ubuntu live CD but the problem is that i can't backup to another folder on the hard drive since it is mounted as a readonly  filesystem. can someone tell me how to change that and make the disc writable?

---

### Post by tszanon on 2008-01-08
Never done that, but I think you could install ntfs-3g so you can mount it Writable.
But, if possible, I'd suggest you to use an usb external drive/flash disk. It would be much easier.

---

### Post by p1977p on 2008-01-08
> **tszanon said:**
> Never done that, but I think you could install ntfs-3g so you can mount it Writable.
But, if possible, I'd suggest you to use an usb external drive/flash disk. It would be much easier.



thanks. but the amount of data is very large.  you know how to change the drive's attributes?

can i install ntfs-3g using a live cd?

---

### Post by tszanon on 2008-01-08
> **p1977p said:**
> thanks. but the amount of data is very large.  you know how to change the drive's attributes?

can i install ntfs-3g using a live cd?
I believe so, because ntfs-3g is a package just like any other.
When you mount a ntfs partition, it's implicitly mounted as a NTFS partition (of course, as expected :)).
After installing ntfs-3g, you will NOT mount it as a NTFS partition, but as a **ntfs-3g** partition. Then, Ubuntu will be able to write to it.

I think gutsy already comes with ntfs-3g installed by default. If you have a gutsy livecd, maybe it'll be easier.

Again, I never done it, but I believe the command-line for mounting would be:
sudo mount -t ntfs-3g <hd partition> <mount point>

What came to mind was: after you backup the data to that same partition, how are you planning to recover it? Since you can't boot the system and you can't format the partition, you don't have many options...System Repair?

---

### Post by p1977p on 2008-01-08
well i'll just overwrite the corrupt xp installation. i don't have to worry about the 'my documents' folder getting overwritten then.

edit: ntfs-3g doesn't show up in synaptic!!

---

### Post by tszanon on 2008-01-08
> **p1977p said:**
> well i'll just overwrite the corrupt xp installation. i don't have to worry about the 'my documents' folder getting overwritten then.

edit: ntfs-3g doesn't show up in synaptic!!
Hmm...fine. I hope the installation won't automagically format the partition.

Type this in terminal:
```
sudo gedit /etc/apt/sources.list
```
You'll see lines like this (I'm at work now, I don't remember exactly how they're written):
```
deb http://archive.ubuntu.com/ubuntu feisty nnnnnn restricted
```
I don't remember what's that nnnnnn. The point here is: in the end of the line, add this:
```
universe multiverse
```
Save the file, then, back in terminal:
```
sudo apt-get update
sudo apt-get install ntfs-3g
```
It may solve the problem. If you have any doubts, paste here the file /etc/apt/sources.list or any error message that you get.

---

### Post by p1977p on 2008-01-08
can't install because the compiler cant create executables!!

BUMP!

now what?

---

### Post by tszanon on 2008-01-08
> **p1977p said:**
> can't install because the compiler cant create executables!!

BUMP!

now what?
What? When does this message appears?
Did you update sources.list successfully?
Did you install ntfs-3g successfully?
And above anything else: what livecd version are you using? dapper? feisty? gutsy? 32-bit or 64-bit?

---

### Post by kdwillia on 2008-01-08
do you have the computer set up on a home network or is it a stand alone?    If on a network, you can use the Ubuntu LiveCD to connect to another share on the network and copy the data across.

There are also USB Hard Drives that hold a lot of data.   My techs carry 120GB 2.5" USB HDD's so that they can copy off any data that needs to be retained.  These types of drives go for around $100 now.

---

