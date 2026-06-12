---
title: "How to install and execute e2defrag on Linux Mint and KuBuntu?"
date: 2017-04-17
forum: General Help
---

### Post by crashnburn_in on 2017-04-17
How to install and execute e2defrag on Linux Mint and KuBuntu? 

[http://launchpad.net/e2defrag](http://launchpad.net/e2defrag)

---

### Post by yancek on 2017-04-17
Click on the green tab on the right, just below Download.  After downloading it you need to extract it as it is a tar.gz compressed file.  After doing that, take a look at the files extracted and there should be a README or install file with an explanation.  You did notice that this software hasn't been updated for nearly 5 years.

---

### Post by HermanAB on 2017-04-17
Err... why do you want to run e2defrag?  

If you installed your system some time this decade, it probably use btrfs not ext2/3/4 and even if you do use ext2/3/4, e2defrag likely won't do anything that is particularly useful.

---

### Post by deadflowr on 2017-04-17
you can use e4defrag which comes included in the e2fsprogs package

> **HermanAB said:**
> If you installed your system some time this decade, it probably use btrfs not ext2/3/4 and even if you do use ext2/3/4, e2defrag likely won't do anything that is particularly useful.

Only if you've manually set up btrfs as the file system.
It's not the default, at least on Ubuntu or Kubuntu, and definitely not on mint.
Ubuntu's default is ext4, as would be Kubuntu and most certainly mint.

---

### Post by crashnburn_in on 2017-04-18
> **yancek said:**
> Click on the green tab on the right, just below Download.  After downloading it you need to extract it as it is a tar.gz compressed file.  After doing that, take a look at the files extracted and there should be a README or install file with an explanation.  You did notice that this software hasn't been updated for nearly 5 years.
Thank you, I will try this out and get back 
> **HermanAB said:**
> Err... why do you want to run e2defrag?  

If you installed your system some time this decade, it probably use btrfs not ext2/3/4 and even if you do use ext2/3/4, e2defrag likely won't do anything that is particularly useful.
Yes. Less than a decade, but the said system whose HDD I am using Ubuntu to do some work on, only supports Ex3 - Wish it did have Ext4 support. 
And it has 8000+ Fragmented files - So Linux is not infallibe. 


Said so on the forums here: 
[https://ubuntuforums.org/showthread.php?t=1434502](https://ubuntuforums.org/showthread.php?t=1434502)> 


The only way to avoid this is defragmenting your disk.


But Linux filesystems don't need defragmenting!


Whoever told you that is deeply mistaken, this is one of the most common myths of Linux.


What is true is that Linux filesystems avoid, where possible, fragmenting their inode tables. This means that the index of how files are split up (fragmented) across the disk, and where those parts are, tends to be kept together as a whole.


That's a good thing; fragmentation of inode tables is a big problem for other filesystems (FATs in that filesystem, etc.) so by keeping them together, it wins a lot of performance.


But the data itself is still fragmented, and spread all over your disk in a random order. And unfortunately during boot, it's the data we need.


One of the future things we want to do is use the ureadahead analysis of what we need during boot to feed into a defragmenter, so everything we need is in one big block on the disk.


---

### Post by crashnburn_in on 2017-04-18
> **yancek said:**
> Click on the green tab on the right, just below Download.  After downloading it you need to extract it as it is a tar.gz compressed file.  After doing that, take a look at the files extracted and there should be a README or install file with an explanation.  You did notice that this software hasn't been updated for nearly 5 years.

Does not contain any of that.

---

