---
title: "Compressed Folder?"
date: 2021-05-26
forum: General Help
---

### Post by rsteinmetz70112 on 2021-05-26
Is there a way to create a compressed folder which can be accessed using standard command line tools?
I want to do some moving old data around but don't have enough free space to do what I want but if I could compress the data it should work.
I do know about tar -z, zip and gzip but they do not do exactly what I'm looking for. I would consider a compressed filesystem but I'd need to add additional storage and if I do that I can simply get enough storage to replace some of teh stirage I already have.
I'm thinking of something similar to a Windows Compressed Folder which can be accessed using Explorer but it can be accessed using Command Line tools.

---

### Post by ActionParsnip on 2021-05-26
Could use BTRFS compression
[https://www.codeground.net/howto/install-ubuntu-or-linux-mint-with-btrfs-disk-compression-enabled/](https://www.codeground.net/howto/install-ubuntu-or-linux-mint-with-btrfs-disk-compression-enabled/)
Is space really stretched for you?

---

### Post by rsteinmetz70112 on 2021-05-26
Thanks  - I was aware of that, but reformatting an existing partitions involves more than I want to do or can do since I have no place to move the stuff already on the partition.

I'm "remodeling" a remote computer so I have to do all of the file moving over ssh and some other methods have failed. I have enough storage for my ultimate goal, but I don't have enough for the intermediate moves.

Since it's remote I can't simply add another hard drive, even a USB drive, which is what I'd usually do - add a scratch drive and move stuff there then move it to the new location.  

I have tried creating compressed tar archives, but the connection breaks before the copies are completed and I have to start over. 

If I could rsync into a compressed folder rsync could keep track of what had been already copied. I don't see a way to do that but I don't know all of the tricks and thought someone here might know something I don't know.

---

### Post by HermanAB on 2021-05-26
Hmm, some points to ponder:
a. NFS mount a remote share.
b. A tmpfs RAM disk.
c. Create a small swap file and put btrfs on the previous swap partition.

---

### Post by Holger_Gehrke on 2021-05-26
> **rsteinmetz70112 said:**
> 
I have tried creating compressed tar archives, but the connection breaks before the copies are completed and I have to start over. 


'screen' might be helpful in this situation. In 'screen' you can have sessions which will continue to run even if the connection between server and terminal  goes down.

Holger

---

### Post by rsteinmetz70112 on 2021-05-26
Thanks for the suggestions.

> **HermanAB said:**
> Hmm, some points to ponder:
a. NFS mount a remote share.
That might work if I can find an filesystem with enough space. I have 322 GB files to deal with.
> b. A tmpfs RAM disk.
I have 16GB of RAM , but the system needs at least 4 GB and 12 GB of RAM wouldn't be enough.
> c. Create a small swap file and put btrfs on the previous swap partition.
I have 20 GB of SWAP in a swap partition,  even if I took the whole partition a compressed 20 GB btrfs doesn't seem likely to hold enough compressed date.
My /home partition has about 500GB free, so a compressed tar archive should fit.

---

### Post by Impavidus on 2021-05-27
How much do you expect to gain from compression? Without media files (images, sound, video), you rarely need more than a few hundred MB. To fill a few hundred GB, you need media files, and those are usually compressed already. Compressing them again rarely saves more than a few percent.

---

### Post by rsteinmetz70112 on 2021-05-27
> **Impavidus said:**
> How much do you expect to gain from compression? Without media files (images, sound, video), you rarely need more than a few hundred MB. To fill a few hundred GB, you need media files, and those are usually compressed already. Compressing them again rarely saves more than a few percent.

Actually this is an archive of project files stretching back a couple of decades and includes a variety of file types. Some are media files pictures, cad files etc., some are documents of various types that will compress quite well some are even already compressed archives which will actually take more space if compressed again. If I can get 20-30% that should be enough.

---

