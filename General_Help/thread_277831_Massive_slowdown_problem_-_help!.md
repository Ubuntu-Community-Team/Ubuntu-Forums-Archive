---
title: "Massive slowdown problem - help!"
date: 2006-10-15
forum: General Help
---

### Post by eagle63 on 2006-10-15
Hey guys, I've got a really weird problem that I'm hoping someone can help me with.  I've just recently installed Dapper on my work computer.  It's an IBM P4, 2 gigs ram, and is used as a headless workstation.  (very standard hardware)

Anyway, what I'm finding is that sometime in the middle of the night, something is happening to it so that when I come in to work the next morning, it's EXTREMELY slow and sluggish.  I'm talking like 5 minutes per mouse-click for the screen to refresh.  I end up having to reboot it, which always fixes the problem - at least until the next evening when it happens all over again.

I've tried opening a terminal window and running "top" while it's sluggish, thinking that maybe the CPU is pegged or something.  Just the opposite - the CPU is virtually idle, and there is no swapping going on either.  I also looked in /var/log/messages for any type of weird error but it looks clean.  

I have absolutely no idea what is causing it to go into massive-slowdown mode, and I really don't even know where/how to start troubleshooting.  If anyone has any ideas I would grealy appreciate it.  Thanks!!

---

### Post by taurus on 2006-10-15
Look in /etc/crontab to see if you have your /etc/cron.daily set to be running late at night and look in /etc/cron.daily to make sure you don't have something heavy running each night!!!  

p.s.  Didn't you post the same message not that long ago, yesterday perhaps?

---

### Post by eagle63 on 2006-10-15
> **taurus said:**
> Look in /etc/crontab to see if you have your /etc/cron.daily set to be running late at night and look in /etc/cron.daily to make sure you don't have something heavy running each night!!!  

Hmmm, whatever is in there would be what was installed as part of the OS - I certainly didn't add anything.  Here's what's in that directory: 
/etc/cron.daily$ ls
0anacron  aptitude      find.notslocate  man-db  slocate   sysklogd apt     bsdmainutils  logrotate        samba   standard

> 
p.s.  Didn't you post the same message not that long ago, yesterday perhaps?

Nope, this is my first post on the subject.

---

### Post by taurus on 2006-10-15
Do you mount some network drives with samba???  If you have no use of samba, you can either move it somewhere else or delete it.  Also, if you leave your computer on all the time like mine in the office, you don't have to run slocate and man-db every single day.  Once a week is good enough.  In fact, I don't even have aptitude and apt running thru cron.  I just run aptitude to check for update a couple times a week, by hand.  So, see if your system's slowing down if you move all those services to somewhere else.  You can always move them back if you need to run them daily...

---

### Post by eagle63 on 2006-10-15
> **taurus said:**
> Do you mount some network drives with samba???  If you have no use of samba, you can either move it somewhere else or delete it.  Also, if you leave your computer on all the time like mine in the office, you don't have to run slocate and man-db every single day.  Once a week is good enough.  In fact, I don't even have aptitude and apt running thru cron.  I just run aptitude to check for update a couple times a week, by hand.  So, see if your system's slowing down if you move all those services to somewhere else.  You can always move them back if you need to run them daily...

Thanks for the help taurus.  I did enable Samba purely because my work's network was unable to resolve the computer's host name when I would SSH or VNC to it.  By enabling Samba, I can now connect to it without having to type the IP - which of course can change since it's DHCP.  Aside from that, I have no other use for Samba - I'm not mounting drives or anything.  

As for other cron jobs, I guess I could try making some of them run weekly, but please undestand that this slowdown I'm seeing is not just a little slowdown, it's a major slowdown.  As in something is critically wrong here - not just a little poor performance.  Also, the slowdown continues until I reboot the box.  

Here's something I was just thinking of: The CPU on this box is a Pentium 4 2.8 with Hyperthreading.  Is there some "special" kernel version I should be running?  (SMP or something...?)  After typing "uname -r" it looks like I'm on 2.6.15-27-386.  Should it really be the 686 kernel??  If so, why didn't it install that from the get-go?  This may be a 2nd issue, and not related to the slow-downs.

Thanks again for your help.

---

### Post by taurus on 2006-10-15
Okay, sounds to me like it's probably samba trying to mount some drives on the net but since those are using dynamic IP, that could be the problem.  So, remove samba if you don't need it.  Run it by hand if you need to access some network drives.

Also, you can upgrade your kernel to i686 if you wish.  You can do that with synaptic/apt-get/aptitude.

---

### Post by eagle63 on 2006-10-15
I'll try removing Samba, but then how do I solve the problem of having to use an IP address when connecting to the box?

---

### Post by taurus on 2006-10-15
It uses dynamic IP right!!!

---

### Post by eagle63 on 2006-10-15
Yes, it is dynamic - so if I'm unable to connect to it by typing the hostname, then I'm pretty much screwed.

---

### Post by taurus on 2006-10-15
If that box is on 24hours, then it should have the same IP address while it's running so you just have to mount it using samba only once!  Otherwise, you need to know what's the IP address of that box is to connect to it or mount it.

---

### Post by eagle63 on 2006-11-13
Ok, just wanted to follow-up on this question/problem I raised a few weeks back.  So far I'm still unable to resolve this problem.  I'm on my 3rd fresh install of Dapper and they've all exhibited this problem.

Just to recap, my system runs fantastic for about 24 hours at most, then mysteriously it quickly slows down to the point where simply running the "top" command from a terminal window takes about 5 minutes to show any results. (although it never completely freezes, just gets very slow...) When top finally shows results, the cpu is virutally idle (less than 2%) and the memory looks fine.  (no swapping)  At this point I'm pretty much forced to do a "sudo reboot" and wait about 20 minutes for it to actually reboot.  Once it's back up, it's great again for about a day until the whole process repeats itself.  

Here's an interesting thing I've noticed: when the slowdown hits,  the system clock is usually way behind - like 4 hours or more.  Maybe this isn't terribly earth-shattering news since if the system is slowing down then presumably the clock will slow down too - but nevertheless I figured I'd mention it.  

On my most recent install, I decided to NOT install any updated packages for a few days - instead I just ran with whatever was on the install CD just in case there was a weird update that causes the problem.  Unfortunately, the slowdown still happened by the next morning.  This was before installing Samba or anything else, so I can say with a certainty that Samba has nothing to do with it.  

The computer has a HyperThreaded P4.  I've tried disabling HT in the bios, but that made no difference.  I've also tried upgrading my kernel from the 386 version to a 686-SMP version.  Aside from now correctly showing 2 CPU's in my "system monitor", it hasn't fixed the slowdown problem either.  

I'm open to any ideas anyone has.  :)  Again, this is pretty standard hardware and used to run Windows just fine.  (IOW, I don't think there's anything defective or not working from a hardware standpoint) Plus, if the issue was due to bad hardware I would think it just wouldn't work at all - rather than work great for a period of time and then crap out.  

Thanks again for any ideas!

---

### Post by koenn on 2006-11-13
> Yes, it is dynamic - so if I'm unable to connect to it by typing the hostname, then I'm pretty much screwed.

Like Taurus said, if those machines are on 24/7 they will probably never get a different IP address : half-way through the dhcp lease, they will start requesting a lease renewal from the dhcp server, in order to keep their address. the lengt of the dhcp lease is configured on the dhcp server. 

to be able to access those machines by hostname i.s.o. ip address ... well, that's what DNS is for, no ? And ideally, your network is set up with dynamically updated DNS so that either the dhcp server, either the hosts themselves inform the dns server of hostname - ip-address matches. 

So if you only need the samba for address resolution (probably the WINS in samba ?), and you think samba is screwing things up,  you can replace it by DNS.


edit: oops, missed that part about samba having nothing to do with it.

---

### Post by eagle63 on 2006-11-13
Yeah, I actually need Samba because I need to access some files on other Windows servers on our network - so it wasn't purely a DNS thing.  

I'm starting to wonder if I should try installing Fedora Core 6 instead to see if that makes any difference.  Not that I want to leave Ubuntu but it might be a good experiment to try when I have some time...

---

### Post by koenn on 2006-11-13
> I'm open to any ideas anyone has
here's a few:

1- disk space ? eg temp directory filling up or processes having trouble writing to disk (tem, logs, ....)
do
```
df -h
```
to see used/free space, eg when system slows down and after reboot, to compare

2- look in 'top' for zombied processes ?

3- no swapping ? I thought Linux always used the swap area because it likes to keep the memory +/- completely used, and the swaps to have 'whatever is likely to be needed next' available in RAM.
 eg on my PC right now I have
Mem:   1034632k total,  1019292k used,    15340k free,    34604k buffers
Swap:  1574320k total,    18424k used,  1555896k free,   669600k cached

So OK, it's only using 18MB of swab, but it *is* using it.
random thought : if you really have no swapping going on, maybe you have a problem with the swap are that slows things down after a given period of activity ?

---

### Post by eagle63 on 2006-11-13
Good idea on the disk space usage, I just checked now and copied/pasted what the results are - I'll double check tonight/tomorrow morning once the slowdown hits to compare.

As for the swap, I guess what I meant is that the used swap (according to top) doesn't seem to change during the slowdown as compared to what it was previously.  For example, currently top shows about 19 megs of used swap.  I'll see what is is after the slowdown, but I expect that it won't be any different.  

I'll post back tomorrow with my findings.  Thanks for the tips!

---

### Post by eagle63 on 2006-11-14
Ok, so everything was fine last night but now this morning at exactly 9:11am the slowdown hit.  I was working away and all of a sudden BAM - my VNC session just froze.  (this is a headless workstation that I connect to remotely)  I SSH'd in, and was able to log-in although it took almost 5 minutes. 

Running "top" didn't reveal anything.  CPU was virtually idle, there were zero zombie processes, and the swap was unchanged from yesterday.  (about 19 megs used)  Running df -h showed that my disk usage was also unchanged from yesterday.  Plenty of room in all partitions.  

Hmmm....  I wonder if it's something network-related going on, though I have no idea what.  This problem is weird because the performance doesn't slowly degrade over time - it's runs great and then suddenly hits a massive slowdown.  

Any other ideas of things we could check/troubleshoot?  Thanks!!

---

### Post by eagle63 on 2006-11-15
Another update: 

Once again this morning at exactly 9:11am the slowdown problem struck.  That's definitely not a coincidence, so hopefully we can track down what the issue is.  Again I checked cpu usage, etc, and everything looked normal.  I looked at crontab, and it doesn't look like there are any jobs scheduled to run at that time.  Here's /etc/crontab:
```

# m h dom mon dow user  command
17 *    * * *   root    run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily
47 6    * * 7   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.weekly
52 6    1 * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.monthly

```

I'm checking with one of our network admins to see if there could be some process going on that's trying to hit my box at that time.  If it's not network related, than I have no clue what could be causing this - especially be cause it seems to be happening at a consistent time.  Thanks again for any ideas anyone has.

---

### Post by qstix on 2007-03-07
Hi

eagle63, did you solve this problem?

I've got more or less exactly the same problem.
I'm running a semi-headless server with dapper 6.06 LAMP.
Hardware: IBM(!) NetVista 512 MB RAM, P4 2.0 GHz.
Similar to eagle63:s machine.. Could the problem be hardware related?

Most of the time I connect from my windows laptop with PuTTY (SSH client for Win)
or NX-client.

I started to investigate if the problem might have something to do with cron but I can't find a clear time pattern when these slowdowns occur.

I also cannot find anything that might cause the slowdown such as high CPU usage, zombie or dead processes.
My logs look clean too.

The only things I really can point out now is that the system clock gets way behind.

I discovered another weird thing: When I try to run **top**
from PuTTY it takes about 1 minute before the result shows up.
BUT when I resizes the SSH terminal window after running **top** the result shows up instantly! :confused: 

[I]Thanks to anyone that can help me/us..
If you need some more info please just tell med and I will provide you with what might be useful.[/I]

---

### Post by eagle63 on 2007-03-07
> **qstix said:**
> Hi

eagle63, did you solve this problem?

I've got more or less exactly the same problem.
I'm running a semi-headless server with dapper 6.06 LAMP.
Hardware: IBM(!) NetVista 512 MB RAM, P4 2.0 GHz.
Similar to eagle63:s machine.. Could the problem be hardware related?

Most of the time I connect from my windows laptop with PuTTY (SSH client for Win)
or NX-client.

I started to investigate if the problem might have something to do with cron but I can't find a clear time pattern when these slowdowns occur.

I also cannot find anything that might cause the slowdown such as high CPU usage, zombie or dead processes.
My logs look clean too.

The only things I really can point out now is that the system clock gets way behind.

I discovered another weird thing: When I try to run **top**
from PuTTY it takes about 1 minute before the result shows up.
BUT when I resizes the SSH terminal window after running **top** the result shows up instantly! :confused: 

[I]Thanks to anyone that can help me/us..
If you need some more info please just tell med and I will provide you with what might be useful.[/I]

Hey there, no unfortunately I'm still suffering through this annoying problem.  Because this computer is at my work, I've been dealing with our internal IT manager to see if he can help me.  So far, one of our leading theories is that it's some type of DNS issue - but nothing we've tried has helped.  

It does sound like we have similar hardware, and I suppose that **could** be the issue...  Usually though, if there's a hardware problem it generally causes a full-blown lockup.  Not just a slowdown like we're seeing.  What I'd love to do is take the box home and run it on my home network for a week and see if has any problems.  Unfortunately, I don't think IT would let me do that.  

I haven't given up though, and I will definitely post back here if I end up solving it.  One interesting thing I recently discovered was that there's another guy in our office who's running Linux and does NOT have this issue.  The 2 differences, though, are that he's running Red Hat Enterprise Linux AND he's running on different hardware.  (I think an IBM blade, not sure though)  Nevertheless, it is interesting and I intend to find out what settings he's got on his box and see if it differs from mine.  

Good luck, hopefully we'll figure this one out!

---

### Post by qstix on 2007-03-07
After posting in this thread I found a few other having the same problem..
I will now try to boot with noapic kernel parameter as stated in
[[COLOR="Blue"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=109901&page=3") thread: [[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=109901&page=3[/COLOR]]("http://ubuntuforums.org/showthread.php?t=109901&page=3")

---

### Post by qstix on 2007-03-12
Well well..

I now have an uptime of almost 5 days with no slowdown issues at all, which quite certainly proofs that my problem is solved!
:D

The solution is as I stated in my last post:
Booting with noapic kernel parameter.
Just add the parameter
```
noapic
```
to the default kernel row in Grub's *menu.lst*.
Or, if you want to try it out before adding it permanently, just pass the parameter to the kernel at boot time..

Eagle63, hope this will help you too!
If so, change the topic to [resolved]..

---

### Post by eagle63 on 2007-03-12
You beat me to the punch!  I was planning to reply to this thread stating that I too am almost to 5 days of uptime since adding those kernel parameters.  I followed the threads you posted earlier and sure enough, they were right.  I added both "noapic" and nolapic" to my kernel parameters by editing /boot/grub/menu.lst.  Not sure if you need both or not - I was just following the suggestion of one of the posters.

Anyway, that did the trick - and boy am I a happier Ubuntu user now!  Thanks for replying to this thread, I don't know how I never stumbled across any of those other threads as I did do quite a bit of searching before I started this thread.  (must have not used the right keywords) Also, I was obviously incorrect about my assumption that it was a network thing.  I DO think there are some DNS issues in my office which are causing some small flaky issues, but they are definitely separate from the slowdown thing.  

Thanks again,

---

