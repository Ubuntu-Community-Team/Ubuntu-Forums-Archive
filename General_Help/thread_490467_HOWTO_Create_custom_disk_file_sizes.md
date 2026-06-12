---
title: "HOWTO: Create custom disk file sizes"
date: 2007-07-02
forum: General Help
---

### Post by shinji257 on 2007-07-02
The installer creates blank files that are set at a certain amount.  Here were a couple of such layouts that I found.

_10GB_
System: 8GB
Home: 1GB
Swap 1GB

_15GB_
System: 11GB
Home: 2GB
Swap: 2GB

That's fine but I don't need a 2GB swap however I did need more space in the Home and System files.  I did a little experiment and created my own blank files.  Windows XP includes a program to create such files quickly.

[quote=command prompt][FONT="Lucida Console"]
C:\>fsutil file createnew
Usage : fsutil file createnew <filename> <length>
   Eg : fsutil file createnew C:\testfile.txt 1000[/FONT]
[/quote]

So... you can do something like the following

[quote=command prompt]
[FONT="Lucida Console"]
C:\wubi\disks>fsutil file createnew system.virtual.disk 12000000000
File C:\wubi\disks\system.virtual.disk is created

C:\wubi\disks>fsutil file createnew swap.virtual.disk 1000000000
File C:\wubi\disks\swap.virtual.disk is created

C:\wubi\disks>fsutil file createnew home.virtual.disk 3000000000
File C:\wubi\disks\home.virtual.disk is created

C:\wubi\disks>dir
 Volume in drive C has no label.
 Volume Serial Number is 5C83-BA7E

 Directory of C:\wubi\disks

07/02/2007  02:08 PM    <DIR>          .
07/02/2007  02:08 PM    <DIR>          ..
07/02/2007  02:08 PM     3,000,000,000 home.virtual.disk
07/02/2007  02:07 PM     1,000,000,000 swap.virtual.disk
07/02/2007  02:07 PM    12,000,000,000 system.virtual.disk
               3 File(s) 16,000,000,000 bytes
               2 Dir(s)  72,535,707,648 bytes free[/FONT]
[/quote]

And as you can see it is actually 16GB total.  Do this right after the wubi part and before restarting where the actual installation begins.  The files will get formatted properly and everything will work as expected.  The installer will not really be able to tell except that they have a formatted capacity of 3GB for home, 1GB for swap, and 12GB for system.  

Note that there is no easy way to do this after the installation.  You have to do this between the wubi graphical installer and the first reboot where the system does the actual ubuntu installation to the virtual drives.

---

### Post by pazsion on 2011-05-13
I've found that some software, will crash the entire os if you don't have a swap file of sufficent size. I've repeated this with previous and current versions of ubuntu, and various games, and data benchmarking tests and stress tests. And multiple pc's and hardware configurations. 

atleast 2 gb. or 1/10th of total system bandwidth.

Particularly with systems that share memory with the cpu and gfx cards. physical memory is almost always fully in use. Or reserved for various processes. 

regardless of what anyone tells any of you. swap is used and is needed. And unless you have an old ide 5400rpm drive from 1990. it will be on par with the speed of your ram. In many cases it's faster and can handle larger ammounts of data, in multitasking fashion. Where with ram alone, you would be waiting for space to become available, before the cpu can even process the info you just requested,  making your system slow, or freeze. And in some cases crash. You can further improve multitasking and response times by adding a flash drive or ssd, with usb 2.0+ or sata or an ultra dma 300+ drive. of 7.2k rpm or more. 7.2krpm seems to be plenty. Even with dcc and various media computations, decodeing and encodeing of codecs and handleing of huge files.. the time it takes to complete such tasks are significantly reduced when swap is used. 

an example of half of total system bandwidth..

test your ram using something like pcwizard, it will give you a benchmark to base this off of. 

let's say your pc can handle at most 40gigs per second. or 40 million instruction strings of 1mb in size. at most, current cpus process 4-8 or 12 diffrent streams of these instructions per second per thread.. If you want to be more precise you can divide the total bandwidth by the detected cpu capabilities. specificially it will state that your cpu lvl 1 and lvl 2 cache have 2-4-6-8-12 way assosiation.  multiply that by however many threads your cpu supports. for example 40gigs / 4 x 2 = 20 gigs maximum bandwidth per second, per thread, per core. for this example 2 gigs would be minimum swap size. this would be 500mb's per core for a quad core. 

for optimal performance, and heavy use.. you'd want a 40 gig swap.. for more practical use, and to save space, 4-8gb swap will be plenty.  For net books and laptops. 2-4gigs. should be considered max. As more heat will be produced across all components that handle memory. Includeing the device you choose to put the swap files on. Using a device other then the os drive, will reduce this heat stress significantly.
:D

---

