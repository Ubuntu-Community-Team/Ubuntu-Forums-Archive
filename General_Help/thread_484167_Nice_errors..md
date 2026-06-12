---
title: "Nice errors."
date: 2007-06-25
forum: General Help
---

### Post by God Of Atheism on 2007-06-25
First I ran into an error on booting along the lines of `disc failure, insert system disc and press enter', after opening and cleaning my case yesterday. After switching the wires running to my two SATA discs, it did boot, so does SATA care about which disc I have connected to which connector? (I'm not sure whether I'm using the RAID controller or not, but I think I am. I know I used to in windows since it was supposed to give a better performance than the standard SATA controller even without a RAID array)
I had the same error as above again today, after opening my case again to replace two fans of which one had broken down while the other one wasn't in too good a condition, again switching wires solved it, but then I ran into another problem:

Logging into Ubuntu would immediately log me out again with an error message warning me that my session lasted shorter than ten seconds as well as reading that something did not have enough space. I suspected a disc error, and went on to boot with the install disc, since I assumed an option to run fsck, which I did not find there, and decided to run a memory test instead since it wouldn't be a bad idea anyway. (the memory turned out fine) I then rebooted with the gparted live cd, and discovered that I indeed had only 18 MB free on my root partition. Why does GNOME need any free space on my root partition to start up? (I have 1 GB of RAM and more than enough swap, 2.3 GB, at this moment only 300 MB total is in use, with 0 B swap in use)
Anyway, I had one mostly empty partition on the same disc, directly after my root partition, so I removed that one and resized my root partition to about 50% bigger to solve that problem. I then created a new partition in the freed space.

On next reboot, I got an error about the disc device and was thrown into a terminal, where I got one error to rule them all (this was apparently because the system was trying to do something to deal with the error):

**Apt is not installed, please use apt-get install apt**

Or something along that line.

I also could use control-D to resume booting, which is what I did. So now, the partition following the root partition is not recognized. Am I right in assuming that some simple editing of /etc/fstab is enough to fix that? If so, what is the simplest way to retrieve the data that are needed there?

Oh and the data on the old partition following the root partition only consisted of a partial backup of my home partition, and the home partition is on that same disc. I did have another copy of that backup on my other disc. Since deleting and creating new partition tends to be far faster than resizing partitions, I did the former in this case.

---

