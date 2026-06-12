---
title: "Why does rsync slow down?"
date: 2021-06-22
forum: General Help
---

### Post by rsteinmetz70112 on 2021-06-22
I've been using rsync to copy a lot of files between filesystems and it seems if copying a large amount of data that after running for a while rsync file transfers slow way down, they keep going but slow considerably. 
This seems to happen regardless of whether the transfer is over a network, the Internet or between two file systems on the same computer.
I am using very basic commands like ```
rsync -av /file1/file3 /file2/file3
``` Sometimes I use the "z" option when copying over the network.

Looking at System Monitor I don't see excessive CPU or Memory consumption. Free shows plenty of RAM free and very little swap in use.

What am I missing?

---

### Post by freedombacon on 2021-06-22
Copying a large number of small files will take longer and the small number of large files because the filesystem tables and metadata need to be updated for each file as well. Spinning disks can make that very slow. Also, -z will typically slow you down on a LAN due to the single threaded compression.

---

### Post by rsteinmetz70112 on 2021-06-22
Thanks,  

What is happening is I am copying a mix of files and when I start the copy it moves along quickly with any size files but after a while it slows way down again with a mix of file sizes. This appears to happen regardless of whether there is a network involved or not.

---

### Post by HermanAB on 2021-06-23
Buffers.  In the beginning, it buffers to RAM, but eventually all buffers are full and what you see then is the real speed of the transfer.

---

### Post by sudodus on 2021-06-23
You can check the 'dirty' data which is not yet flushed from buffers with

```

grep -e 'Dirty:' /proc/meminfo

```

I made a shellscript, [FONT=Courier New]**watch-flush**[/FONT], that is part of the mkusb package. [FONT=Courier New]**watch-flush**[/FONT] watches the amount of dirty data at regular intervals and shows how the buffers are filled and flushed.
```

sudo add-apt-repository ppa:mkusb/ppa
sudo apt install mkusb
watch-flush

```

Edit: You can tell the system to hurry up flushing the buffers with the command

```

sync

```

---

### Post by rsteinmetz70112 on 2021-06-23
Running the command it doesn't seem to be filling up buffers. and they seem to be flushed pretty quickly.

```
# grep -e 'Dirty:' /proc/meminfo
Dirty:               576 kB
# grep -e 'Dirty:' /proc/meminfo
Dirty:               300 kB
# grep -e 'Dirty:' /proc/meminfo
Dirty:               300 kB
# grep -e 'Dirty:' /proc/meminfo
Dirty:                 0 kB
```

Sync runs almost instantly. 

```
# free
              total        used        free      shared  buff/cache   available
Mem:       16319620     2693748    12664452       30064      961420    12323888
Swap:       8388604        4908     8383696
# free -h
              total        used        free      shared  buff/cache   available
Mem:            15G        2.6G         12G         29M        940M         11G
Swap:          8.0G        4.8M        8.0G

```

free shows lots of memory available

None of this seems to increase the copy speed.

---

### Post by HermanAB on 2021-06-24
I wonder whether the command ionice will make a difference.

Something like
# ionice-c 2 -n 0 rsync yadda yadda
Or
$ sudo ionice -p PID

I have seen in the past that ionice can clear up io access inefficiencies very effectively.

---

### Post by rsteinmetz70112 on 2021-06-24
In my current  attempt to transfer files between two drives on the same computer rsync runs 3 processes all of them seem to be started by the original PID 3404

```
# ps -ef|grep rsync
root      3423  3404  0 Jun21 pts/0    00:03:54 rsync -av /media/rob /backup
root      3424  3423  0 Jun21 pts/0    00:00:00 rsync -av /media/rob /backup
root      3689  3424  0 Jun21 pts/0    00:05:03 rsync -av /media/rob /backup
```

So which PID would you use for ionice?
Or would yadda yadda = rsync -av /media/rob /backup

The copy process is proceeding slowly so I'm reluctant to start over and lose any large files currently in process although it's been running for days now - note the date on the process above.

---

### Post by sudodus on 2021-06-24
Have you checked with **top** or **htop** if rsync is busy or maybe waiting for some other process? 

You can also [install and start] **iotop** in order to watch the write progress and what process(es) that are involved.

```

sudo iotop -od2

```

What kind of drives are you reading from and writing to? How are they connected (SATA, eSATA, USB2, USB3, NVMe)?

I really don't know what is slowing down your process, so I am guessing here: Could there be hardware problems (for example that the hard drive has problems writing some sectors)?

---

### Post by rsteinmetz70112 on 2021-06-24
I've checked top and System Monitor neither show a significant loard on the computer., I haven't tried iotop.
The drives are both external connected vi USB ports, but I've experienced similar issues with transfers over the Internet and over the LAN.
There could be a problem with the drive I'm copying from as it is old and may have issues. The other drive is practically new and is showing not signs of problems.
There could be a hardware problem somewhere else.

---

### Post by Doug S on 2021-06-24
I don't think there is anything wrong. As previous posters have mentioned, speed changes after buffers backup.

For large file transfers, magnetic disk to different magnetic disk, I get: 
. ~175 megabytes per second, which is the disk read rate.
. then the buffers backup, and the rate drops to ~85 to 90 megabytes per second.

For many many small file (1024 bytes) transfers, magnetic disk to different magnetic disk, I get:
. 1 megabyte per second for about 159 files.
. then 500 kilo bytes per second until file 207
. then 333 kilo bytes per second until file 246
. then 250 kilo bytes per second until file 304
. at this point the buffers are fully backup up.
. then 3.26 kilo bytes per second on an exponential decay curve to 0.88 kilo bytes per second by file 40,000.

EDIT: Note calculations done from rsync log file. Example:
```
ab00039997.txt
          1,024 100%    0.88kB/s    0:00:01 (xfr#39998, to-chk=2/40000)
ab00039998.txt
          1,024 100%    0.88kB/s    0:00:01 (xfr#39999, to-chk=1/40000)
ab00039999.txt
          1,024 100%    0.88kB/s    0:00:01 (xfr#40000, to-chk=0/40000)

```Yet the entire thing took only:

```
doug@s19:/media/sda$ time rsync -av --progress /media/sda/ab* /media/sdb > ~/bla5

real    0m1.180s
user    0m0.450s
sys     0m0.930s
```So something is wrong with the math.

---

### Post by HermanAB on 2021-06-25
You can use ionice on every rsync instance.  You can also run rsync, watch it slow down, then run ionice and see whether it speeds up.

There were bugs in old USB drivers (about a decade ago) that were very much improved with a default ionice (no parameters needed) on a copy action.  Maybe you have one of those?

---

### Post by rsteinmetz70112 on 2021-06-25
OK I've tried the ionice command and there was no noticeable change.

Frequently checking the transfer of a large file (about 4GB)  you can see that in the 6 second between 12:58:49 and 12:58:55 the file size increased by 262,144 bytes or a little over 43K per second.

```
# date; ls -l  .??*
Fri Jun 25 12:58:49 CDT 2021
-rw------- 1 root root 2438987776 Jun 25 12:58 .files.tgz.rw0UpH
# date; ls -l  .??*
Fri Jun 25 12:58:55 CDT 2021
-rw------- 1 root root 2439249920 Jun 25 12:58 .files.tgz.rw0UpH
# date; ls -l  .??*
Fri Jun 25 12:59:04 CDT 2021
-rw------- 1 root root 2439249920 Jun 25 12:58 .files.tgz.rw0UpH
```

Note that from 12:58:55 to 12:59:04 there was no increase in size so the average rate would only be a little more than 17K/sec.

People keep mentions buffers, but which buffers are they talking about.  The buffers(cache) in the Hard Drive, the OS or somewhere else? The internal transfer rate for most hard drives is much higher than these numbers and assuming the buffers are operating efficiently the overall transfer should be higher. Even a USB2 connection can routinely operate at several megabytes/second.

Adding another data point after allowing the transfer to continue;  

```
# date; ls -l  .??*     Fri Jun 25 13:14:29 CDT 2021
-rw------- 1 root root 2447114240 Jun 25 13:14 .files.tgz.rw0UpH
```

This amounts to an elapsed time of 15:34 or 934 seconds resulting in a transfer rate of 8.7K/second. The longer time should allow for a closer approximation of the average transfer rate.

---

### Post by sudodus on 2021-06-25
It might be interesting to check, if you have the same slowdown in a live Ubuntu system (booted from USB) as you have in your installed system.

---

### Post by Doug S on 2021-06-27
> **rsteinmetz70112 said:**
> OK I've tried the ionice command and there was no noticeable change.
me either.
> **rsteinmetz70112 said:**
> 
People keep mentions buffers, but which buffers are they talking about.  The buffers(cache) in the Hard Drive, the OS or somewhere else? The internal transfer rate for most hard drives is much higher than these numbers and assuming the buffers are operating efficiently the overall transfer should be higher. Even a USB2 connection can routinely operate at several megabytes/second.
I am just talking about any buffers in the chain of things between sending the data and it actually getting onto the storage device, which is nowhere near my ram cash limits.
I had not realized until the numbers you gave, that your issue was so severe.
Example from my computer:

---

