---
title: "File tranfer speeds drop off by half?"
date: 2018-01-30
forum: General Help
---

### Post by frank72 on 2018-01-30
Is it normal for file transfer speeds to drop by half?

When I start a file transfer I get about 65 mbs but it steadily drops to 30.

Also seems to be hogging resources....

This is completely fresh install of !6.04
Thanx

---

### Post by TheFu on 2018-01-30
File transfers have to write to disk at the speed the disk can support.  RAM is used for disk buffers, so while there is free RAM, the transfers will be very fast.  Until the buffers are full, then the speed of the disks (reading and writing) are usually the limitation.

You can watch the disk buffers using the 'free' command and other system-wide monitoring tools.

---

### Post by cruzer001 on 2018-01-30
I use Nemo and also seen this behavior.  While it is true what TheFu has said, I have found other file managers can (at times) do a better job.  PcManFM can be faster than Nemo and I have also had cases where a zip file will show a higher transfer rate than the same unzip file.  Nemo and Nautilus (for me) doesn't seem to care about how much ram is available (I have 24G), they will slow down when xfering large files.  Its a mystery to me why this is, just my findings.

---

### Post by TheFu on 2018-01-30
Different programs will use different libraries to transfer files.  I don't really use GUIs, so my transfers happen using NFS or rsync (w/ssh) on the LAN and sftp or sshfs when over the internet.

Network transfers are shown in Mbps unless a GUI is used, then GUI programmers like MBps.  bits vs bytes, which is a factor of 8 different for any lurkers.

I suspect the OP is seen 65 MBps which is 520 Mbps.  That is respectable for a GigE wired connection, but a spinning disk just can't keep up with that level of performance. Most spinning will only do 80+ Mbps - expensive ones can get to 150Mbps.  Cheap SSDs are about 170Mbps writes and expensive SSDs using PCIe interfaces can go to 32Gbps.  My $100 128G SSD with an m.2 SATA connection does. This is all local, no networking on an i3 with 4G of RAM. ```

$ bonnie++ -h -d /tmp  -r 4000
Writing a byte at a time...done
Writing intelligently...done
Rewriting...done
Reading a byte at a time...done
Reading intelligently...done
start 'em...done...done...done...done...done...
Create files in sequential order...done.
Stat files in sequential order...done.
Delete files in sequential order...done.
Create files in random order...done.
Stat files in random order...done.
Delete files in random order...done.
Version  1.97       ------Sequential Output------ --Sequential Input- --Random-
Concurrency   1     -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
cc3550           8G   864  99 77866   7 72051   8  2947  99 235458  14  9676 125
Latency             14345us    2216ms     749ms    4939us     131ms    1748us
Version  1.97       ------Sequential Create------ --------Random Create--------
cc3550              -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++
Latency              2205us     881us     689us     668us      23us     981us
1.97,1.97,cc3550,1,1517338312,8G,,864,99,77866,7,72051,8,2947,99,235458,14,9676,125,16,,,,,+++++,+++,+++++,+++,+++++,+++,+++++,+++,+++++,+++,+++++,+++,14345us,2216ms,749ms,4939us,131ms,1748us,2205us,881us,689us,668us,23us,981us
```

About 76 MB/s. Meh. It is a cheap SSD. There is a way to format the output as HTML, but I didn't remember to do that this time. Sorry.

It requires 5+ min to run, but I don't know of any better way to learn about local disk performance.  Copying files between different disks inside the same computer tests different things.  All of this is handy for troubleshooting different parts of the subsystem - controller, cables, PSU, and the disk.

Obviously, the network would be a limiting factor for most people if the transfers are over the internet or wifi. WiFi causes all sorts of issues that humans seldom notice until it is really, really bad. But computers see the wifi bandwidth jumping higher and lower constantly, which disrupts total performance.

---

