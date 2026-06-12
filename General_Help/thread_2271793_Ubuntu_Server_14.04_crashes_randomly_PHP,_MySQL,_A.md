---
title: "Ubuntu Server 14.04 crashes randomly? PHP, MySQL, Apache2"
date: 2015-04-01
forum: General Help
---

### Post by psca119.tech on 2015-04-01
Hello, I am a private host for a few clients and for some reason my server randomly crash's sometimes, I have taken some notes on the probable causes on why the server might be crashing, however I have no real evidence or logs to go off of (I don't know what logs to look at or where, However live-time I have htop and sar. The stats on CPU are average, 80% idle, normal, and memory is average 5/12GB and I replaced the hard-drives multiple times now.) The symptoms:

- When I was running "PHPGraph" which was simply a php library, nothing much just a folder filled with PHP files that I call to generate a PieChart, which I wanted, but wasn't required, and then all the sudden, after 2-3 days it would just CRASH, and maybe even multiple times a day. (Not the software, like the whole server would FREEZE and I would need to restart it by hard-reset, I have tried CTRL+ALT+F1 and CTRL+ALT+F7 and all those keys and buttons but its just FROZEN.

- After I stopped calling and removed all the code that called to PHPGraph (svg graphics) the up-time I was very surprised increased to 5 days. But this is still not good enough. I am open to any suggestions or anything the community has to offer, I would like to learn while I fix this issue and work with Ubuntu more. It works great on my laptop, not sure why It won't work great for servers.

I think it is called a LAMP server? Yes, well It has/is: Linux, PHP, MySQL, Apache2, all the standard software.

I need my servers up soon otherwise I might loose clients :(

---

### Post by tgalati4 on 2015-04-02
If you have a hardware or power supply problem, the log files will not be helpful.  But look in /var/log for clues.  Also, have an extra ssh session (terminal only) logged in from another computer to see if you can shutdown cleanly in case your server appears to lock up again.  Not sure why a php process would crash your server; make sure your increase your memory size in php.ini because the default memory allocations are too low.

How old is the server?  When was the last time you cleaned it out?

---

### Post by psca119.tech on 2015-04-02
Hello! Yeah, when I mean it locks up, I mean, it has no control anymore, all connections are dropped, all process's are frozen, webpage won't load anymore, and it's basically dead. I don't think the server is too old, it was maintained 1 month ago and we got it in 2012. It's a head-less server running Ubuntu 14.04 with the following hardware (which has been checked recently, and seems fine, even with MEMTEST86):
- 1 TB HDD
- 12 GB DDR3 Memory
- No peripherals
- 1 GBPS integrated ethernet port
- Intel i3 dual-core (hyper-threading) 3.2 GHz
- New replaced power-supply, similar to this:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16817171092&nm_mc=KNC-GoogleAdwords-PC&cm_mmc=KNC-GoogleAdwords-PC-_-pla-_-Power+Supplies-_-N82E16817171092&gclid=CNmkp7up2MQCFcSCfgodbIcAMQ&gclsrc=aw.ds](http://www.newegg.com/Product/Product.aspx?Item=N82E16817171092&nm_mc=KNC-GoogleAdwords-PC&cm_mmc=KNC-GoogleAdwords-PC-_-pla-_-Power+Supplies-_-N82E16817171092&gclid=CNmkp7up2MQCFcSCfgodbIcAMQ&gclsrc=aw.ds)

What happens if PHP runs out of memory? where is that file?

---

### Post by SeijiSensei on 2015-04-02
The "memory_limit" parameter appears in php.ini.  On my CentOS servers, the default is 128M. 

If PHP exhausts memory you'll see an entry in /var/log/apache2/error_log unless you let the application write errors to the browser page.  I've run out of memory in PHP because of an endless loop in a for() structure that creates an array:
```

$n=0;
$my_array=array();
for ($i=0; $i<999; $i++) {
     $my_array[$n]=$n;
     $n++;
     $i--;
}

```
That will create an infinitely sized array and exhaust memory in PHP.  You can monitor the memory by adding 
```

* * * * * root /usr/bin/free | grep Mem: >> /var/log/memory.log

```
to /etc/crontab.  That will write a memory usage snapshot every minute to memory.log.

I'd also install **smartmontools** and use "sudo smartctl /dev/sda" to check the "SMART" status of the hard drive.  You might also re-seat the memory chips if you haven't done so in a while.  Sometimes problems like these happen intermittently because of heat buildup.

---

### Post by psca119.tech on 2015-04-02
I will try what you suggest :) thank you.

I just have no clue why it freezes, the server is still ON, but there is no HDD activity or anything. Simply stops responding.

The admins will be relieved if it was a simple memory leak or something, but for now I will try the php memory dump and apt install smartctl to test /dev/sda.

I will write my results back in a few days.

---

### Post by psca119.tech on 2015-04-13
Ah, well after running hundreds of different tests count-less times, The issue was "bad-blocks" on the hard-drive, appearing to fail soon. That's not too good. Also appeared to be a PHP memory leak with one of our libraries, we fixed that today and re-ran the test, it came out successful, so thank you all for your help! If anyone else has weird "crashing/freezing" please be sure to use the advice above/below, and the following tests I ran might be helpful:

Code:
> 
$ sudo apt-get install smartmontools
$ sudo smartctl -a /dev/sda
$ sudo smartctl -l error /dev/sda 


If you want to take a risk, I believe the command I ran for badblocks:

Code:
> 
$ sudo badblocks -sv /dev/sda
# I highly recommend not using the parameter -w just yet, unless you have recent backups.


And to run a PHP force memory leak as shown above, this will dump helpful logs by PHP to ensure that when PHP runs out of memory it properly dumps/gc's. Which was helpful to patch a PHP memory leak in one of our library's. Thank you once again community!

---

### Post by tgalati4 on 2015-04-14
Yes, those are all standard troubleshooting techniques.  It is sometimes difficult to isolate hardware versus software issues, but sometimes it is both.  If you have more problems, then look carefully at the replacement power supply.  If it is not an OEM supply, then it may not meet all of the specifications of the motherboard.

Glad you got it figured out.

---

