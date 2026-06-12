---
title: "dd linux command in shell"
date: 2013-07-09
forum: General Help
---

### Post by ivlevkir on 2013-07-09
I'm using the dd command to create a bootable usb from iso file:


*sudo dd if=~/Desktop/ubuntu.iso of=/dev/sdx bs=1M*


After pressing enter it momentarily exits and gives me:


*915+0 records in 915+0 records out 959447040 bytes (959 MB) copied,*
*0.539375 s, 1.8 GB/s*


So it's like running in background because I can see that the flash drive is working. Eventually it will stop copying and I can remove the drive successfully but the question is **why doesn't dd command wait for copying to finish. Why does it run in background. And how can I make it wait?**

---

### Post by slickymaster on 2013-07-09
> **ivlevkir said:**
> I'm using the dd command to create a bootable usb from iso file:


*sudo dd if=~/Desktop/ubuntu.iso of=/dev/sdx bs=1M*


After pressing enter it momentarily exits and gives me:


*915+0 records in 915+0 records out 959447040 bytes (959 MB) copied,*
*0.539375 s, 1.8 GB/s*


So it's like running in background because I can see that the flash drive is working. Eventually it will stop copying and I can remove the drive successfully but the question is **why doesn't dd command wait for copying to finish. Why does it run in background. And how can I make it wait?**

According to [http://www.gnu.org/software/coreutils/manual/html_node/dd-invocation.html](http://www.gnu.org/software/coreutils/manual/html_node/dd-invocation.html):> Sending an ‘INFO’ signal to a running dd process makes it print I/O statistics to standard error and then resume copying. In the example below, dd is run in the background to copy 10 million blocks. The kill command makes it output intermediate I/O statistics, and when dd completes normally or is killed by the SIGINT signal, it outputs the final statistics.```


     $ dd if=/dev/zero of=/dev/null count=10MB & pid=$!
     $ kill -s INFO $pid; wait $pid
     3385223+0 records in
     3385223+0 records out
     1733234176 bytes (1.7 GB) copied, 6.42173 seconds, 270 MB/s
     10000000+0 records in
     10000000+0 records out
     5120000000 bytes (5.1 GB) copied, 18.913 seconds, 271 MB/s
```
On systems lacking the ‘INFO’ signal dd responds to the ‘USR1’ signal instead, unless the POSIXLY_CORRECT environment variable is set.

An exit status of zero indicates success, and a nonzero value indicates failure.

---

### Post by Cheesemill on 2013-07-10
The dd command thinks that the copying ***has*** finished as it has written all of the data it's been asked too.

It's actually the underlying disk caching of the OS that accepts all of the data as fast as dd can spit it out and then sends the 'I've finished' command to dd while it is in fact still copying the data.

To make sure that you know when the copying has actually finished you can add the sync command to the end of your dd command so that all cached data is written before you are returned to the terminal prompt...
```
sudo dd if=~/Desktop/ubuntu.iso of=/dev/sdx bs=1M && sync
```

---

