---
title: "When booting, then what??"
date: 2006-07-15
forum: General Help
---

### Post by Foodie on 2006-07-15
I am a pretty newb to Linux, at the moment! But when i got an answer to this then i think i can do all the other by myself! ;)

I have downloaded and burned down the Ubuntu Live thingy, and it works like a charm... So much, that i now decided to install Linux on my computer...

The thing i wanted to do, is to make a new partition with PartitionMagic. I have a HDD with about 6 GB. free space, and then i will make a new partition with 5 out of the 6 GB. Is it then possible just to install Ubuntu, on this new partition without any problems?? Will i get the option to choose which OS i want to boot to, when i am starting my computer??

Have you any tricks, that will do the job for me?

I found some guides on video.google, but seemed a little bit strange to me... 

But i am really excited about exploring this new Linux world! :-D

---

### Post by gerbman on 2006-07-15
> **Foodie said:**
> The thing i wanted to do, is to make a new partition with PartitionMagic. I have a HDD with about 6 GB. free space, and then i will make a new partition with 5 out of the 6 GB. Is it then possible just to install Ubuntu, on this new partition without any problems??Yes, that should work fine. I'm assuming you already have Windows taking up the rest of the drive (correct me if I'm wrong). Once you create the 5GB partition, you will have to tell Ubuntu to install to that partition. The installer should automatically set up the boot loader to allow you to select which OS you want to boot.> **Foodie said:**
> Have you any tricks, that will do the job for me?If you've already got PartitionMagic, then you should be set. Please read the following pages before asking questions about partitioning or dual-boot installations:

[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

Happy reading, and welcome!

---

### Post by Foodie on 2006-07-15
Well, actually i have my Windows install on my C:, and split that HDD in 2 partitions, so its C: and E:. Then i have the 40GB. HDD with none partitions on it, that i want to split in 2 and then install Ubuntu on one of them! ;)

I dont think that makes any difference, or does it??

Just realized i proberbly have put this thread the wrong place... ](*,) 

Hope its ok! :D

---

### Post by cyclister on 2006-07-19
A question why dont download the ISO of drappler drake instead if you going to run it more often?

And when you partoning leave like 15 gb in ext3 at least 8 gb if you dont wnat the whole system on one partoning you can have it like 3 - 4 gb.
But a / root, swap and /home at least are to recomend, then I think linux loader is to prefer in this setup.Grub what I know of only boot up linux, but i can be wrong here.
/ like minimum 4 gb, swap like 1 ½ times of your ram setup in the computer and /home (its here you download and like the most of the enviroment is) minimum like 6.
One thing though the smaler system you have the faster its gonna get.

Beacuse when you setup a real distro you partoning in the installation part when I was complete nub I had like linux partoning and a program called commander something a bootuploader, where I could partoning from.
Its not the way it's suposed to do, not partoning first any how not for system setup.

If you want to be able to boot two system in one hdd, partoning only so you can manage your system setup.

During partoning in system setup take time do wrong test a lot, this will take a while, but when that is done your a little prouder of yourself.

Or use a complete diffrent hdd with only ubuntu in it.

And when everything with setup is done you have the system to work with and belive me you have many fancy package you want to have, for example like a nice firewall :D

---

