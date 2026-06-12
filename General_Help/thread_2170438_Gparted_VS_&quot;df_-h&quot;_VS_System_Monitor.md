---
title: "Gparted VS &quot;df -h&quot; VS System Monitor"
date: 2013-08-26
forum: General Help
---

### Post by Binary-Synapse on 2013-08-26
Hello.

I have a question regarding HDD usage in my Ubuntu 12.04LTS system.
System Monitor reports 62,1GB used.
"df-h" reports 63,0 GB used.
GParted reports 73,07GB used.

Why the different values reported?
Which one should I trust?

Thank you

---

### Post by TheFu on 2013-08-26
62.1 - it is the smallest and filling any HDD to be full is bad for Linux systems.  Anything over 90% is bad for the OS partition.

Why are they different?  I didn't look up the answer, but ....

Gparted sees the partition size ... without a file system. File systems have a little overhead.

df -h  sees the file system size - the -h forces it to round.  That rounding may also be off either 1024b or 1000b - hard to say.

System Monitor - I've never used it, but it may be holding back storage like the file system does for root vs non-root users. On really full disks, the last few % free can only be written by root, not normal users. This is there to protect the machine from crashing.

If you really want to know the answer for each - you'll probably need to read the source code, however, you might get lucky by reading the manpage for each.

Personally, I'm not going to worry about 1-2G on a 20+G file system.

---

### Post by Binary-Synapse on 2013-08-26
Hello.

SI notation   =>1GB=1.000.000.000Bytes
IEC notation =>1G**i**B=1.073.741.824Bytes


> 62.1 - it is the smallest and filling any HDD to be full is bad for Linux systems.  Anything over 90% is bad for the OS partition.
I'm sorry but I didn't quite understood what you have said.
My HDD is not full! Space being used is about 10%.
My HDD capacity is 750GB ([COLOR=#ff0000]750 156 374 016 [/COLOR]Bytes total).
And that equals approx.. to 698,64G**i**B (IEC notation).




> Gparted sees the partition size ... without a file system. File systems have a little overhead.
Sorry, but this doesn't make sense to me!
If Gparted only sees the partition size without the filesystem overhead... well, in that case it should report the smallest value.
But it's returning the largest value! And it's a 10GiB difference when compared to all other programs!


> df -h  sees the file system size - the -h forces it to round.  That rounding may also be off either 1024b or 1000b - hard to say.
Yes the -h switch reports the value in "Human Readable Format" with powers of 1024.
And I'm also sure it uses IEC notation, because I compared it to the command "df -BG" which reports the same thing on /dev/sda1.


> System Monitor - I've never used it, but it may be holding back storage like the file system does for root vs non-root users. On really full disks, the last few % free can only be written by root, not normal users. This is there to protect the machine from crashing.

You could be right here.


> If you really want to know the answer for each - you'll probably need to read the source code, however, you might get lucky by reading the manpage for each.
Everything is well documented in the MAN pages, except for Disk Usage Analyzer (AKA baobab), which seems to use SI notation (powers of 1000).


> Personally, I'm not going to worry about 1-2G on a 20+G file system.
Yes but I have to worry, because I have to clone this disk to an 80GB capacity one.
That's why it's a concern to me.



In my first POST I should also have mentioned the following (it would have been clearer):
[COLOR=#ff0000]System Monitor[/COLOR]=62,1G**i**B (IEC notation, which means that 1G**[FONT=Thread-0000199c-Id-00000052]i[/FONT]**B = 1024M**[FONT=Thread-0000199c-Id-00000052]i[/FONT]**B = 1024^3 Bytes).
[COLOR=#ff0000]
df -h[/COLOR]=63G**i**B (IEC notation, which means that 1G**[FONT=Thread-0000199c-Id-00000052]i[/FONT]**B = 1024M**[FONT=Thread-0000199c-Id-00000052]i[/FONT]**B = 1024^3 Bytes).
[COLOR=#ff0000]
df -BG[/COLOR]=63G**i**B (this command also **FORCES** IEC notation, which means that 1G**[FONT=Thread-0000199c-Id-0000004e]i[/FONT]**B = 1024M**[FONT=Thread-0000199c-Id-0000004e]i[/FONT]**B = 1024^3 Bytes).
[COLOR=#ff0000]
Gparted[/COLOR]=73,07G**i**B (IEC notation, which means that 1G**[FONT=Thread-0000199c-Id-00000052]i[/FONT]**B = 1024M**[FONT=Thread-0000199c-Id-00000052]i[/FONT]**B = 1024^3 Bytes).
[COLOR=#ff0000]
Disk Usage Analyzer (AKA baobab)[/COLOR]=66,7GB
I don't know for sure if it's using IEC or SI notations though, since I didn't see nothing in the official documentation.
But it seems to be using SI, because it's reported value is approx. to command "df -H", which uses powers of 1000.


So the question remains:
Why is Gparted reporting a different value?


**Please also view the following screenshot:**
[http://imageshack.us/photo/my-images/833/rrei.png/](http://imageshack.us/photo/my-images/833/rrei.png/)


As we can see in the provided Screenshot, only about 10% of /dev/sda1 is in use.
I have a 2GB SWAP and the rest is for Ubuntu 12.04LTS.
I don't have any more partitions.
The provided Screenshot includes Gparted, df, System Monitor, and Disk Usage Analyzer outputs (on the same HDD).
All seem to report about the same thing except for Gparted!

Any explanation?

Thank you kindly

---

