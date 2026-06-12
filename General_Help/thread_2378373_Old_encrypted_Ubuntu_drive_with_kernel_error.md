---
title: "Old encrypted Ubuntu drive with kernel error"
date: 2017-11-22
forum: General Help
---

### Post by 010c-davis010 on 2017-11-22
Can I just plug it into my windows desktop and input the password to retrieve my data?

Thanks in advance!

---

### Post by The Cog on 2017-11-22
Sorry but I don't think so.

First, if I'm right (might not be, this is just what I think I remember reading) the password you give is simply used to decrypt a small file somewhere that holds the actual key used to encrypt the disk. So the password itself cannot decrypt the disk.

Second, even if you could decrypt it, I don't think windows can understand the ext4 file format.

Your best bet is probably to use a live CD. At least it would be able to mount the disk if you can work out how to do the decryption. I hope someone can help you with that, sorry I really don't know enough to help.

---

### Post by 010c-davis010 on 2017-11-22
Thank you for the response.  To be clear all I want to do is retrieve some pics off the drive before I wipe it. Hope that helps in some way. Unfortunately I am not experienced with Ubuntu at all other than using it mildy for a couple months to try it out. The bad part is that I stored the only copies of a lot of pictures of my son on there before the error occurred. 

So using a live CD I should be able to access the drive to transfer the files then?

---

### Post by The Cog on 2017-11-23
It doesn't take away the need to know how to decrypt it. A live CD just makes sure all the tools are available.

I don't know how to do the decryption. And I'm to be very short of spare time for a few days. If nobody else can help here, then at least this search in google looks as though it might provide some useful starting points for you. It's where I would start: "how to mount encrypted disk in ubntu". I tried several search terms and this was the best looking set of results.

---

### Post by kurt18947 on 2017-11-24
Certainly no expert here but if you used the default Ubuntu encryption to encrypt the partition I'd be surprised if there's a program for Windows that would decrypt a Linux partition. There are apps that enable Windows to read and write ext 3 and ext 4 partitions but that seems like the easiest part of your task.

---

### Post by ian-weisser on 2017-11-24
What is the kernel error?

---

