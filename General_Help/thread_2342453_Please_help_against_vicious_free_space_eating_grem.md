---
title: "Please help against vicious free space eating gremlin."
date: 2016-11-06
forum: General Help
---

### Post by ubin2 on 2016-11-06
After restarting my PC, a specular and alarming problem popped up. It seems like something wants to eat all free available space on my partition. I discovered this after restarting. I don't know if it was happening before restarting.  Before I had a couple GB of free space, then I had zero, not even enough to start my browser. When I delete several gigabytes more, that free space rapidly disappears within seconds, I can see it disappearing as I switch back and forth on the file manager. 

 I reload my PC again, and there is space. Reload again, no space. Each  reload results in a different amount of free space (but not much) or no  space with no apparent pattern.

It seems if something claims the free space, like my browser cache, then whatever eats the free space, can't steal, like something is just sitting around waiting for there to be free space to eat up. It only steals space from my main partition. I have a second partition with a small amount of free space it doesn't steal from.

Currently I have zero space shown for my main HDD partition, I don't  dare reload again in case I can't get my browser up again. So I leave my PC running all the time now, not even putting it in sleep (that can screw things up anyway) Please keep  in mind a number of things I can't try due to lack of HDD space.

I am pretty sure home is on the same partition as the OS, and I don't  believe I have a separate partition for cache either, but am not  positive. I am aware that this is ill advised. Once I fix this issue, I plan to install new version with proper partitioning. But right now this  problem is crippling my options. I am also worried, could I possibly be  hacked or something? 

I got 8gb of RAM, so plenty.

---

### Post by &amp;KyT$0P# on 2016-11-06
How big is your partition?

[This thread]("https://ubuntuforums.org/showthread.php?t=2331523") shows how to troubleshoot these type issues.  So, first step, please post the output of this command -
```
cd /;sudo du -sx $(ls -A) | sort -n
```

---

### Post by Bucky Ball on 2016-11-06
2Gb of free space is not really enough headroom for the / operating system partition anyway. That will cause issues.

I'd boot from to a 'live' session (install media and 'Try Ubuntu') and backup your valuable data to an external device before going any further. Then I'd probably think about moving that personal data to another partition rather than inside the /home folder in /. You don't have enough room there for it by the looks. 

I'd move that data, make sure you have about 5Gb free in the / partition and see if problem persists.

---

### Post by cariboo on 2016-11-06
If you can actually do anything on your system, open a terminal and type the following commands:

```
sudo apt-get autoremove && sudo apt-get autoclean
```

the commands will remove any unneeded packages and remove old configuration files and downloaded packages in /var/cache/apt/archives.

---

### Post by ubin2 on 2016-11-07
Halogen, partition is 50gb. 

```
du: cannot access `home/a/.gvfs': Permission denied
du: cannot access `proc/32368/task/32368/fd/4': No such file or directory
du: cannot access `proc/32368/task/32368/fdinfo/4': No such file or directory
du: cannot access `proc/32368/fd/4': No such file or directory
du: cannot access `proc/32368/fdinfo/4': No such file or directory
0    initrd.img
0    initrd.img.old
0    lib64
0    proc
0    sys
0    vmlinuz
0    vmlinuz.old
4    data
4    mnt
4    recup_dir.1
4    selinux
4    srv
4    xorg.conf.new
16    lost+found
20    media
72    tmp
128    recup_dir.2
348    root
648    dev
8024    bin
8164    sbin
11912    lib32
15164    etc
190204    boot
557176    opt
1290220    lib
4920308    usr
6746788    var
31562960    home
```


> **Bucky Ball said:**
> 2Gb of free space is not really enough  headroom for the / operating system partition anyway. That will cause  issues.

*Face palms* That was the free space with the OS doing its thing. Besides, Ubuntu can run strictly from RAM and operating files/doesn't need cache at all.

> Then I'd probably think about moving that personal data to another  partition rather than inside the /home folder in /. You don't have  enough room there for it by the looks. 
> will remove any unneeded packages and remove old configuration files and downloaded packages in /var/cache/apt/archives.

](*,) Did you two not read what I wrote, or do you simply not believe me? It's not a matter of not having enough space directly, it's a matter of something eating the space. I was perfectly fine before, now suddenly somethings sucking up all the free space, and nothing that actually needs any of the free space it's consuming. As I said, if the free space is claimed, then this mysterious space sucker can't consume it. 

Is there a way to determine what is consuming the free space as it is being consumed? I could delete another large video file or something. Of course then the mysterious gremlin will just eat the space again in seconds, so how do I determine the nature of said gremlin? Some log of activity for what is going on that I can make happen?

**Is it possible my system has been hacked, that I am suffering from maleware?** I haven't sudo'd anything lately.

---

### Post by Bucky Ball on 2016-11-07
No idea, then. Good luck with it.

---

### Post by &amp;KyT$0P# on 2016-11-07
ubin2, do you want help or not?  If so, do follow the suggestions by Bucky Ball and cariboo.  They aren't daft you know.

According your output, the biggest folders are /var and /home.  Your /var is quite unusually large, in fact.

Let's get your personal data out of /home.  Fire up a live Ubuntu and **move all your personal data to another disk**, exactly as Bucky Ball suggested.  Once that's done, boot back into your installed system and run cariboo's command, which should clean up /var a bit.  Please post here the full output from running cariboo's command, if any.

Next, just watch and wait for the gremlins to eat up the new free space.  Then re-run the command I've suggested and post the new results.  This should help us pinpoint the gremlins' playground.

---

### Post by ubin2 on 2016-11-07
So what's next step after freeing up space? Let's say I move and delete 30 gigabyes of space, and seconds latter the gremlin eats it. What next after that for determining the gremlins identity? Is there no way to somehow spy on the gremlin as it's eating its meal?

What is /var typically used for?

I still haven't gotten a answer about the possibility of maleware/hacking and how to rule it out.

---

### Post by untrustytahr on 2016-11-07
> **ubin2 said:**
> 
Is there a way to determine what is consuming the free space as it is being consumed?

pidstat -d 1 60

Pidstat -d will give I/O information about processes under the control of the kernel.  The 1 60 means it will report at 1 second intervals for 60 seconds.  It's part of the sysstat package.

---

### Post by alexjpowell on 2016-11-07
is your /home/ folder encrypted

---

### Post by oldfred on 2016-11-07
If /var is full, do you have run away log files?
An app or even a missing boot setting can cause that.

       Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[http://ubuntuforums.org/showthread.php?t=2327103&page=3](http://ubuntuforums.org/showthread.php?t=2327103&page=3)
[http://ubuntuforums.org/showthread.php?t=2327570](http://ubuntuforums.org/showthread.php?t=2327570)

---

### Post by deadflowr on 2016-11-07
> **ubin2 said:**
> 
What is /var typically used for?
variable data, meaning it's a place where the system's data changes often.
A place where log files are, and the archived package files are, amongst other types of data that changes often (caches as another example).
(archived packages include both the packages for new updates and packages for new software you decided to install; like if you installed vlc or some other software from the software center, it will download the installer package here and leave it until you run a cleanup command of some kind.)

> I still haven't gotten a answer about the possibility of maleware/hacking and how to rule it out.
In linux systems you tend to want to rule out system erring first, as those are far more common.
Which is why knowing which area is getting eaten can narrow that down, until we can see exactly where a troubling file or folder is.
And usually when you find that troubled file/folder you can, or might, be able to link it to a particular application or system process that has gone rogue.

As for malware, we cannot rule it out, of course.
That really depends upon your own internet usages and behaviors.
If you have a habit of clicking on links left and right, then malware can be a strong possibility.
If you're cautious about what links you click, and do so very seldomly, then malware would be a very weak possibility.

Logically, it does a hacker little good to show it's hand.
A hacker would rather be in your system unseen for as long as possible.
A hacker would more likely give you more disk space, as they'd want to remove any trace they were ever in your system. A well as remove any deterrent the system might initially had before they hacked you.
But running something that eats up your space and triggers you to double check, does not point in the direction of a hacker's more common modus operandi.

Of course, though, anything is possible.
So ruling out either malware or hackery wholesale is foolhardy.
But in the same token, thinking it can be either or, is in reality far less likely.

---

### Post by &amp;KyT$0P# on 2016-11-07
> **ubin2 said:**
> So what's next step after freeing up space? Let's say I move and delete 30 gigabyes of space, and seconds latter the gremlin eats it. What next after that for determining the gremlins identity? 
Well, you'll now have a folder that's **very** abnormally large in size.  So we examine *that* folder using [FONT=Courier New]du[/FONT], same as above - just instead of [FONT=Courier New]cd /[/FONT] you would [FONT=Courier New]cd[/FONT] to that folder.

And then keep going down the directory tree, checking every abnormally large folder, until we pinpoint the problem enough to know what we're dealing with.

---

### Post by kpatz on 2016-11-07
/var looks unusually large for starters.  Also, /dev is using some space, which is atypical; dev is normally a special mounted directory that only has device entries in it; it shouldn't be using much if any space.

I'd rerun the command but with /var in the cd; like:```
cd /var;sudo du -sx $(ls -A) | sort -n
```and see what you get.

Afterward, free up some space using the suggestions made by others, see if your space disappears again, and if it does, re-run the suggested du commands to see where the space is going.  I'm guessing somewhere in /var.

---

### Post by ubin2 on 2016-11-07
BTW, is there a code BBC shortcut or do I have to type it out each time?
```
0    lock
4    crash
4    local
4    mail
4    opt
52    games
80    spool
264    run
3324    tmp
9400    backups
129664    cache
648192    lib
5956196    log
```

Yeah, seems log is very big. I don't know what these numbers represent. Is each one, a megabyte?  So my log is nearly 6gb? What is lib?

What is log usually for recording? How do I access that recording? How do I delete it?

---

### Post by dragonfly41 on 2016-11-07
Installing a log file viewer might help you to view and understand your log files which you can later purge.

I have KSystemLog installed.   It is in Ubuntu Software Centre.

---

### Post by deadflowr on 2016-11-07
> BTW, is there a code BBC shortcut or do I have to type it out each time?
Use the Reply to Thread or Go Advanced feature to access the more advanced toolbar options.
One option included in the advanced settings is the # symbol for code tags.
simply click it and paste the output between the code][/code.

Log files in the log folder represent a number of different logs.

You can run the du command again and aim it at that folder this time.
Perhaps like:
```
cd /var/log;sudo du -sx $(ls -A) | sort -n
```
then perhaps if a particulart log file seems odlly large post a portion of it with tail like so
```
 tail -n 100 /var/log/some-large-log-file's-name
```
this will print out the last 100 lines of the file.
Which is where anything being repeated ad nauseam should show.

---

### Post by ArgentWarrior on 2016-11-07
Ubuntu comes with a disk usage analyzer, similar to WinDirStat. Run that and post what it says. 
When I first got started with Linux I filled my old laptop's 80GB hard drive a week after installing Ubuntu, that helped me figure it out.

---

### Post by ubin2 on 2016-11-07
> **alexjpowell said:**
> is your /home/ folder encrypted

No

> Installing a log file viewer


Except no space to install it, remember?

[B]
I don't know what these numbers represent. Is each one, a megabyte?[/B] **So my log is nearly 6gb?**

---

### Post by ArgentWarrior on 2016-11-07
> **ubin2 said:**
> No



Except no space to install it, remember?

[                                                      ]("https://ubuntuforums.org/member.php?u=1910378")[**[COLOR=#000000]@ArgentWarrior[/COLOR]**]("https://ubuntuforums.org/member.php?u=1910378")
Didn't work, "command not found". Probably has something to do with my version being 11.04. Yes I know, out of support, please help anyway. I've tried to update but it's too old to update. I have to replace, and I just haven't gotten around to it. But first I got to fix this issue.

[B]
I don't know what these numbers represent. Is each one, a megabyte?[/B] **So my log is nearly 6gb?**

I didn't mean actually run "WinDirStat", I just said that the tool Ubuntu comes with is similar in functionality. Search in the dash for a disk usage analyzer.

---

### Post by ubin2 on 2016-11-07
**I don't know what these numbers represent. Is each one, a megabyte?** **So my log is nearly 6gb?**

---

### Post by &amp;KyT$0P# on 2016-11-07
From [FONT=Courier New]man du[/FONT]
```
       Display   values  are  in  units  of  the  first  available  SIZE  from
       --block-size, and the DU_BLOCK_SIZE, BLOCK_SIZE and BLOCKSIZE  environ&#8208;
       ment  variables.   Otherwise,  units  default  to 1024 bytes (or 512 if
       POSIXLY_CORRECT is set).

```

---

### Post by ubin2 on 2016-11-07
So is that a yes? Each one is 1mb and my log is nearly 6b?  

Most of that man du thing is in some other language. How do I tell if it's a difference size than 1mb per unit?

---

### Post by mc4man on 2016-11-07
try this, find the big ones then look at them to maybe see issue
```

sudo ls -lA -R  /var/log
```

(- myself would likely just remove all the logs, reboot & see if any start growing to unnatural sizes. After all they are just logs...

---

### Post by ubin2 on 2016-11-07
I don't know how to remove the log anyway. How do I?

But before we go on, may I please get a answer about the size per unit shown in the terminal output, that I have asked about in several other posts.

---

### Post by &amp;KyT$0P# on 2016-11-07
> **ubin2 said:**
> So is that a yes? Each one is 1mb and my log is nearly 6b?  
Yes and no.  Each one is 1 KB (1024 bytes) and your /var is more than 6 GB.

> Most of that man du thing is in some other language. How do I tell if it's a difference size than 1mb per unit?
Run these commands -
```
env | grep BLOCK
env | grep POSIXLY_CORRECT
```
If no output from either, it's 1 KB per unit.

---

### Post by ubin2 on 2016-11-07
So here's the tail end of the biggest log like someone suggested I do earlier. I see TV guide coming up alot of the stuff I can understand.

```

/var/log$ tail -n 100 /var/log/nepenthes.log
[01112016 18:27:44 spam mgr event] <in virtual uint32_t nepenthes::EventManager::handleEvent(nepenthes::Event*)>
[01112016 18:35:03 debug net mgr] Socket TCP  (bind) 0.0.0.0:0 -> 0.0.0.0:80
    DialogueFactory ASN1 Dialogue Factory creates dialogues for the SMB and IIS flaw killbill showed us could Accept a Connection
[01112016 18:35:03 spam net handler] <in virtual nepenthes::Socket* nepenthes::TCPSocket::acceptConnection()>
[01112016 18:35:03 spam net handler] Socket TCP  (accept) 127.0.0.1:40544 -> 127.0.0.1:80 
[01112016 18:35:03 spam net handler] Adding Dialogue ASN1 Dialogue Factory 
[01112016 18:35:03 spam mgr event] <in virtual uint32_t nepenthes::EventManager::handleEvent(nepenthes::Event*)>
[01112016 18:35:03 debug net mgr] Accepted Connection Socket TCP  (accept) 127.0.0.1:40544 -> 127.0.0.1:80 
31 Sockets in list
[01112016 18:35:03 spam net handler] <in virtual int32_t nepenthes::TCPSocket::doRecv()>
[01112016 18:35:03 spam mgr event] <in virtual uint32_t nepenthes::EventManager::handleEvent(nepenthes::Event*)>
[01112016 18:35:03 spam net handler] doRecv() 414
[01112016 18:35:03 spam sc handler] engine::unicode checking ...
[01112016 18:35:03 spam sc handler] xor::rbot64k checking 414...
[01112016 18:35:03 spam sc handler] xor::rbot256c checking 414...
[01112016 18:35:03 spam sc handler] xor::bielefeld checking 414...
[01112016 18:35:03 spam sc handler] xor::halle checking 414...
[01112016 18:35:03 spam sc handler] xor::adenau checking 414...
[01112016 18:35:03 spam sc handler] xor::kaltenborn checking 414...
[01112016 18:35:03 spam sc handler] xor::deggendorf checking 414...
[01112016 18:35:03 spam sc handler] xor::langenfeld checking 414...
[01112016 18:35:03 spam sc handler] xor::saalfeld checking 414...
[01112016 18:35:03 spam sc handler] xor::schoenberg checking 414...
[01112016 18:35:03 spam sc handler] xor::rosengarten checking 414...
[01112016 18:35:03 spam sc handler] xor::schauenburg checking 414...
[01112016 18:35:03 spam sc handler] xor::lichtenfels checking 414...
[01112016 18:35:03 spam sc handler] xor::msfPexEnvSub checking 414...
[01112016 18:35:03 spam sc handler] xor::msfPex checking 414...
[01112016 18:35:03 spam sc handler] xor::leimbach checking 414...
[01112016 18:35:03 spam sc handler] xor::marburganderlahn checking 414...
[01112016 18:35:03 spam sc handler] xor::hod checking 414...
[01112016 18:35:03 spam sc handler] alphanumericxor::skylined checking 414...
[01112016 18:35:03 spam sc handler] alphanumericxor::msfPexAlphaNum checking 414...
[01112016 18:35:03 spam sc handler] linkxor::link checking 414...
[01112016 18:35:03 spam sc handler] konstanzxor::konstanz checking 414...
[01112016 18:35:03 spam sc handler] bindshell::mainz checking 414...
[01112016 18:35:03 spam sc handler] bindshell::adenau checking 414...
[01112016 18:35:03 spam sc handler] bindshell::kaltenborn checking 414...
[01112016 18:35:03 spam sc handler] bindshell::wackerow checking 414...
[01112016 18:35:03 spam sc handler] bindshell::parthenstein checking 414...
[01112016 18:35:03 spam sc handler] bindshell::schoenborn checking 414...
[01112016 18:35:03 spam sc handler] bindshell::ravensburg checking 414...
[01112016 18:35:03 spam sc handler] bindshell::schauenburg checking 414...
[01112016 18:35:03 spam sc handler] bindshell::hatsquad_wins checking 414...
[01112016 18:35:03 spam sc handler] bindshell::mandragore checking 414...
[01112016 18:35:03 spam sc handler] bindshell::hod_netdde checking 414...
[01112016 18:35:03 spam sc handler] bindshell::saalfeld checking 414...
[01112016 18:35:03 spam sc handler] bindshell::augsburg checking 414...
[01112016 18:35:03 spam sc handler] connectbackshell::mandragore checking ...
[01112016 18:35:03 spam sc handler] connectbackshell::hod_netdde checking ...
[01112016 18:35:03 spam sc handler] connectbackshell::bielefeld checking ...
[01112016 18:35:03 spam sc handler] connectbackshell::konstanz checking ...
[01112016 18:35:03 spam sc handler] connectbackshell::egghunter checking ...
[01112016 18:35:03 spam sc handler] connectbackshell::langenfeld checking ...
[01112016 18:35:03 spam sc handler] connectbackshell::pinneberg checking ...
[01112016 18:35:03 spam sc handler] connectbackshell::lichtenfels checking ...
[01112016 18:35:03 spam sc handler] connectbackshell::msf_win32_reverse checking ...
[01112016 18:35:03 spam sc handler] connectbackshell::hatsquad_wins checking ...
[01112016 18:35:03 spam sc handler] connectbackshell::zuc_winshit checking ...
[01112016 18:35:03 spam sc handler] connectbackshell::hod_lsass checking ...
[01112016 18:35:03 spam sc handler] connectbackfiletransfer::halle checking ...
[01112016 18:35:03 spam sc handler] connectbackfiletransfer::linktransfer checking ...
[01112016 18:35:03 spam sc handler] connectbackfiletransfer::stuttgart checking ...
[01112016 18:35:03 spam sc handler] connectbackfiletransfer::wuerzburg checking ...
[01112016 18:35:03 spam sc handler] bindfiletransfer::bindllinktransfer checking ...
[01112016 18:35:03 spam sc handler] bindfiletransfer::amberg checking ...
[01112016 18:35:03 spam sc handler] execute::cmd checking ...
[01112016 18:35:03 spam sc handler] execute::createprocess checking ...
[01112016 18:35:03 spam sc handler] execute::winexec checking ...
[01112016 18:35:03 spam sc handler] execute::msf_win32_exec checking ...
[01112016 18:35:03 spam sc handler] url::anyurl checking ...
[01112016 18:35:03 info sc handler] url::anyurl: "http://www.tvguide.com/listings/"
[01112016 18:35:03 spam mgr event] <in virtual uint32_t nepenthes::EventManager::handleEvent(nepenthes::Event*)>
[01112016 18:35:03 spam handler event module] <in virtual uint32_t nepenthes::LogDownload::handleEvent(nepenthes::Event*)>
[01112016 18:35:03 spam down mgr] Checking Host www.tvguide.com for locality 
[01112016 18:35:03 info down mgr] Handler http download handler will download http://www.tvguide.com/listings/ 
[01112016 18:35:03 spam down handler] <in virtual bool nepenthes::HTTPDownloadHandler::download(nepenthes::Download*)>
[01112016 18:35:03 info down handler] Resolving host http://www.tvguide.com/listings/ ... 
[01112016 18:35:03 debug spam fixme] addDNS: Adding DNS www.tvguide.com for ()
[01112016 18:35:03 debug spam fixme] <in virtual bool nepenthes::DNSResolverADNS::resolveDNS(nepenthes::DNSQuery*)>
[01112016 18:35:03 spam mgr event] <in virtual uint32_t nepenthes::EventManager::handleEvent(nepenthes::Event*)>
[01112016 18:35:03 spam mgr event] <in virtual uint32_t nepenthes::EventManager::handleEvent(nepenthes::Event*)>
[01112016 18:35:03 debug spam fixme] <in virtual uint32_t nepenthes::DNSResolverADNS::handleEvent(nepenthes::Event*)>
[01112016 18:35:03 debug spam fixme] 1 DNS Resolves in Queue
[01112016 18:35:03 debug spam fixme] <in virtual uint32_t nepenthes::DNSResolverADNS::handleEvent(nepenthes::Event*)>
[01112016 18:35:03 debug spam fixme] 1 DNS Resolves in Queue
[01112016 18:35:03 debug spam fixme] <in virtual uint32_t nepenthes::DNSResolverADNS::handleEvent(nepenthes::Event*)>
[01112016 18:35:03 debug spam fixme] 1 DNS Resolves in Queue
[01112016 18:35:03 debug fixme] resolved dns www.tvguide.com (0 left) 
[01112016 18:35:03 debug spam fixme]  0 resolves 
[01112016 18:35:03 warn down handler] url www.tvguide.com unresolved, dropping download
[01112016 18:35:03 debug spam fixme] <in virtual nepenthes::Download::~Download()>
[01112016 18:35:03 debug spam fixme] <in virtual nepenthes::DownloadUrl::~DownloadUrl()>
[01112016 18:35:03 debug spam fixme] <in virtual nepenthes::DownloadBuffer::~DownloadBuffer()>
[01112016 18:35:34 spam net handler] <in virtual void nepenthes::TCPSocket::setStatus(socket_state)>
[01112016 18:35:34 debug net mgr] Deleting Socket Socket TCP  (accept) 127.0.0.1:40544 -> 127.0.0.1:80 due to timeout 
[01112016 18:35:34 spam net handler] <in virtual nepenthes::TCPSocket::~TCPSocket()>
[01112016 18:35:34 spam net handler] Socket TCP  (accept) 127.0.0.1:40544 -> 127.0.0.1:80 clearing DialogueList (1 entries)
[01112016 18:35:34 spam net handler]     Removing Dialogue "IISDialogue" 
[01112016 18:35:34 spam mgr event] <in virtual uint32_t nepenthes::EventManager::handleEvent(nepenthes::Event*)>

```

But yeah, seems like deleting 6gb of log is a good idea. How do I go about doing that? And how do I stop it from making more log?

---

### Post by dragonfly41 on 2016-11-07
I'm guessing that in your case a picture is worth a thousand words.

Try launching Disk Usage Analyser (baobob).

Applications > System Tools > Disk Usage Analyser

Select your Ubuntu partition from the partitions shown and click to start analysis

Rotating logo is seen .. this will continue rotating for several minutes until all files are indexed.
Be very patient until analysis is completed.
When completed you will see a pie diagram of disk usage.

Click on the var folder.   Then on sub folders such as www, log, cache

The sizes will be shown in either GB or MB or kB.

Hover over the pie diagram slices and you will see where the space is being eaten.

....

Re: your last post it seems that you have installed **Nepenthes honeypot**

Reading here ...

[http://www.nepenthespharm.com/](http://www.nepenthespharm.com/)

[https://blog.infosanity.co.uk/2009/04/12/honeypotting-with-nepenthes/](https://blog.infosanity.co.uk/2009/04/12/honeypotting-with-nepenthes/)

> 
[COLOR=#555555]If my honeypot system is any indication, these systems will and do get pounded heavily from prospective intruders, over the lifetime of my honeypot systm I have collected in excess of 850 unique malware samples. In fact when the system was first installed it captured it&#8217;s first malicious binary within 30 minutes of gaining a live network connection (in this case an IRC bot).[/COLOR]


So you will have to turn off the honeypot and purge your swarm of bees you have attracted.

---

### Post by ubin2 on 2016-11-07
I don't think I have ever installed it, somehow it was installed without my permission? I have absolutely no reason to have installed such a thing on my system, and I don't understand how it could be on here. 
So **how do I** "turn off the honeypot and purge your swarm of bees you have attracted."? And delete this program?

I know I have looked at a disk usage pie chart program thingy before, but there is no "Disk usage analyser" in applications> system tools. Is it important that I examine the log space usage before deleting them? **How do I delete this 6gb of log?**

---

### Post by kpatz on 2016-11-07
Nepenthes is a honeypot used for capturing malware.  Typically one would install this if they wanted to do something like this.  If it's on your system and you didn't install it yourself it's possible you either got hacked, or you ran something you downloaded that installed it.

Apparently it used to be in the Ubuntu repositories but it isn't anymore, but it can still be downloaded and installed from somewhere.

What do you get if you run the command:```
sudo dpkg --get-selections | grep nepenthes
```If you get a package name, run dpkg -s with the name you got as a parameter.  So, if the package name is nepenthes, run```
sudo dpkg -s nepenthes
```

To uninstall it, run```
sudo dpkg --purge nepenthes
``` substituting the actual package name for nepenthes.

But if you didn't install it, you may have been hacked, and the best bet after that is to back up anything important, reformat and reinstall.

P.S. Is your system connected directly to the internet or through a router?  If this honeypot is capturing enough stuff to fill your partition with log files it seems it's connected directly.  I'd disconnect the machine from the internet at least until you figure out what to do--taking it offline may stop the log from filling up so fast.

---

### Post by ubin2 on 2016-11-07
I was poking around for antivirus's for ubuntu some time back. Maybe I installed nepenthes as part of that? I mean maybe I was tired and thought it sounded security like and installed it.  Regardless it's installed now and any damage is probably already done, besides I can't be on this forum seeking help if I am off line and won't be able to figure out anything on my own. And no router, just a external DSL modem.

> So, if the package name is nepenthes, run 	Code:
 	sudo dpkg -s nepenthes
```
Package: nepenthes

Status: install ok installed
Priority: optional
Section: net
Installed-Size: 39064
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 0.2.2-6ubuntu2
Depends: libadns1 (>= 1.4), libc6 (>= 2.8), libcap2 (>= 2.10), libcurl3-gnutls (>= 7.16.2-1), libgcc1 (>= 1:4.1.1), libmagic1, libpcap0.8 (>= 0.9.8), libpcre3 (>= 8.10), libstdc++6 (>= 4.5), zlib1g (>= 1:1.1.4), adduser
Conffiles:
 /etc/nepenthes/signatures/shellcode-signatures.sc c24bd1794309e23cb3800140e4d33fe2
 /etc/nepenthes/nepenthes.conf 5110e4c9a1eff98b5181e0bbfc305a3f
 /etc/nepenthes/vuln-lsass.conf 6c898e40efafd4103c34e214a8f14439
 /etc/nepenthes/download-ftp.conf d677ffd8b09e8e74bf138d8249aa1634
 /etc/nepenthes/submit-postgres.conf 7353f49121b86b89fc9fa656a4d360ef
 /etc/nepenthes/log-surfnet.conf 6a52b6e5790afac12de24623e4be851a
 /etc/nepenthes/vuln-dameware.conf 25e5ac684891cb6e4a9cc90763d16bfd
 /etc/nepenthes/download-csend.conf 8b6e18d11ef994a39d5bfcd49946dec0
 /etc/nepenthes/shellcode-generic.conf 2c8d8c2438979f8ab272d87cdd07c075
 /etc/nepenthes/submit-gotek.conf 101970f1b0ef5036e9fb84d1acf62b98
 /etc/nepenthes/vuln-msmq.conf a377099193720aa903b336e00efbb37e
 /etc/nepenthes/vuln-netbiosname.conf ec1e0aefc34a55f2620b2e3bac24bea8
 /etc/nepenthes/x-2.conf 40ef59c69b648128438b25a0745a6f96
 /etc/nepenthes/vuln-mssql.conf 8b24f3ce80a832b06d94f57e9f0a5b56
 /etc/nepenthes/log-download.conf 9459011c840d1440f6128c13df88b8d8
 /etc/nepenthes/vuln-upnp.conf 62cf8e1c284cc24632675be73c10b9f2
 /etc/nepenthes/download-tftp.conf e52b9a4a4d7a91734dcd3d1b2a182c95
 /etc/nepenthes/module-honeytrap.conf 24ab326ac5868e781d277171e0062795
 /etc/nepenthes/vuln-mydoom.conf 0ca5735de0463d7fbcba0738932743e3
 /etc/nepenthes/vuln-pnp.conf 6d7973859ac47a0065a19f59c29bd75a
 /etc/nepenthes/submit-file.conf afa272510e810edbbed24f857edb5f1b
 /etc/nepenthes/download-link.conf 9aa99df1c64ce3fa3cc5f3c20ae6a477
 /etc/nepenthes/vuln-ftpd.conf 785a65216a4d0b6eaac4243ed0f66270
 /etc/nepenthes/vuln-sasserftpd.conf 3ab072c68e633de1ba19c317405efff0
 /etc/nepenthes/vuln-kuang2.conf 583b25ac22980a573a63aed7e8ff04ad
 /etc/nepenthes/submit-http.conf 271c9a8b9964d81a9b86868deecf0cfb
 /etc/nepenthes/vuln-optix.conf 967dfe7d05796f739206fed3156447e6
 /etc/nepenthes/vuln-asn1.conf 40bf5dbe7330c6a9e2c63546d5c52ecc
 /etc/nepenthes/vuln-iis.conf d71743793cc1819f12042f84f58f8ef1
 /etc/nepenthes/download-curl.conf ca44f3b7ef15cb0810c3d0be396dadf0
 /etc/nepenthes/vuln-bagle.conf 9ff04877ef7962f6b3491379194dcfa0
 /etc/nepenthes/vuln-wins.conf 54a408a69f2fc0f690a653342ef3f387
 /etc/nepenthes/submit-mwserv.conf 930a74c84088b69ab534098ecb6b306a
 /etc/nepenthes/submit-norman.conf e43092b6794824c05a0985a016f77e26
 /etc/nepenthes/module-portwatch.conf 01165e7a3e0d221fb870472d1381357e
 /etc/nepenthes/vuln-sub7.conf 467f3f11f45c2f857c881e847cdad241
 /etc/nepenthes/vuln-netdde.conf 869b19965d776c23ef92338c29117f8b
 /etc/nepenthes/vuln-msdtc.conf 1709aecb3836ac9149a11a73d317b367
 /etc/nepenthes/vuln-dcom.conf f87def3c3dc4192368c1fa558b88526d
 /etc/nepenthes/log-irc.conf b4c5e597540c6b3afdf751c571cc7581
 /etc/nepenthes/vuln-veritas.conf 6cf74a771103e070eb5f7dc1a7bd3c7b
 /etc/nepenthes/log-prelude.conf 8e9731c6665a2a1a6473c6a2be9cd72d
 /etc/init.d/nepenthes 3c1c5f3abf697108bd619e2101352ec0
Description: versatile tool to collect malware by emulating widespread vulnerabilities
 Nepenthes is a low interaction honeypot which emulates known vulnerabilities
 to collect information about potential attacks. It is designed to emulate
 vulnerabilities worms use to spread, and to capture these worms. As there are
 many possible ways for worms to spread, Nepenthes is modular. There are
 module interface to
   * resolve dns asynchronous
   * emulate vulnerabilities
   * download files
   * submit the downloaded files
   * trigger events (sounds abstract and it is, but is still quite useful)
   * shellcode handler
Original-Maintainer: Luciano Bello <luciano@debian.org>
```

So will uninstalling nepenthes remove the honeypot too? What about the log?

---

### Post by kpatz on 2016-11-07
After uninstalling nepenthes, go into your /var/log directory and delete any files or directories within that reference nepenthes.  You should get your space back.

I'd also recommend running a firewall if you don't use a router.  Read up on ufw, it's the simplest way to set up a firewall in Ubuntu.

---

### Post by ubin2 on 2016-11-07
3.6gb log for nepenthes + a 26mb download log.  But I did get a bit of free space now that it has been purged. 

I think my modem has it's own primative firewall and AFAIK ubuntu comes bundled with it's own default firewall, doesn't it?

So I can just delete the entire folder var/log? Or leave the folder/directory and just delete everything in it? Well for deleting anything in here, how do i give myself permission?

---

### Post by alexjpowell on 2016-11-08
sudo su
cd /var/log
find -type f -name '*text*'

Validate the results to make sure they are not stupid
find -type f -name '*text*' -delete

---

### Post by ubin2 on 2016-11-08
"find -type f -name '*text*'" did nothing.

 I don't know how I am supposed to validate results or know if results are stupid. Don't even know what results are usual/what results to look for.

Should I delete var/log completely, including folder?  Is there a way to open the directory using the point and click file navigator but with root delete permission?

---

### Post by &amp;KyT$0P# on 2016-11-08
> **ubin2 said:**
> AFAIK ubuntu comes bundled with it's own default firewall, doesn't it?
The firewall in Ubuntu, [FONT=Courier New]iptables[/FONT] and [FONT=Courier New]ip6tables[/FONT], is by default set to do nothing.

> **ubin2 said:**
> "find -type f -name '*text*'" did nothing.

 I don't know how I am supposed to validate results or know if results are stupid. Don't even know what results are usual/what results to look for.
That command will search for and list all log files which the name contains "text" in all lowercase.  I too don't understand why single those out specifically.

> Should I delete var/log completely, including folder?
That sounds dangerous.  I'd only delete rotated logs.  Those are the files which names end in a dot followed by a number.  For example, syslog.1, syslog.2.gz

> Is there a way to open the directory using the point and click file navigator but with root delete permission?
```
sudo -H <your_file_manager>
```

Most likely you have nautilus, so -
```
sudo -H nautilus
```

---

### Post by ubin2 on 2016-11-09
> [QUOTE]Should I delete var/log completely, including folder?
That sounds dangerous.[/QUOTE]

What is the danger?

BTW, is there a way to check, signs to check for, for whether my system is still secure?

If my system was compromised to a degree, could I still download a new OS ISO/live disk and installing from that, be secure?

---

### Post by oldfred on 2016-11-09
Many applications are writing log files. 
If you delete that folder you probably will total crash system.
Only delete the log file with issues.

I do houseclean old log files, if no issues.
 # empty trash
# remove log files if no issues
cd /var/log
sudo rm -f messages.*
sudo rm -v /var/log/*.gz

---

### Post by ubin2 on 2016-11-09
Is there a way to check, signs to check for, for whether my system is still secure?

If my system was compromised to a degree, could I still download a new OS ISO/live disk and installing from that, be secure?

---

### Post by &amp;KyT$0P# on 2016-11-10
> **ubin2 said:**
> If my system was compromised to a degree, could I still download a new OS ISO/live disk and installing from that, be secure?
Likely yes, as long as you don't make that from a compromised system.  Use a known-clean computer to download the ISO and create the live media.

The malware would have to be in your machine's firmware to remain a problem then.  How likely do you think that is?

---

### Post by alexjpowell on 2016-11-10
> **ubin2 said:**
> "find -type f -name '*text*'" did nothing.

 I don't know how I am supposed to validate results or know if results are stupid. Don't even know what results are usual/what results to look for.

Should I delete var/log completely, including folder?  Is there a way to open the directory using the point and click file navigator but with root delete permission?

Hi,
You need to replace 'text' with what you're searching for

With * before and after to specify a wildcard

---

### Post by alexjpowell on 2016-11-10
> **ubin2 said:**
> Is there a way to check, signs to check for, for whether my system is still secure?

If my system was compromised to a degree, could I still download a new OS ISO/live disk and installing from that, be secure?

Run a virus scan

---

### Post by &amp;KyT$0P# on 2016-11-10
> **alexjpowell said:**
> Run a virus scan
alexjpowell, that question is trickier than you think.

Anti-malware stuff on Linux is not like Windows or Mac OS.  On Linux, anti-malware can be useful, but you **must** have the right mindset about it - [https://ubuntuforums.org/showthread.php?t=2337052&p=13546076&viewfull=1#post13546076]("https://ubuntuforums.org/showthread.php?t=2337052&p=13546076&viewfull=1#post13546076")

Don't run a malware scan from the compromised system.  You can't trust the results.  Instead, boot up a live media (see [my previous post]("https://ubuntuforums.org/showthread.php?t=2342453&p=13568005&viewfull=1#post13568005")) and do it from there.

---

### Post by dragonfly41 on 2016-11-10
Also don't forget to check your router and any vulnerable ports using an external probe ...

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

### Post by ubin2 on 2016-11-11
> **halogen2 said:**
> 
                     [IMG]https://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **ubin2**                     [[IMG]https://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("https://ubuntuforums.org/showthread.php?p=13567998#post13567998")                 
                 > If my system was compromised to a degree, could I still download a new OS ISO/live disk and installing from that, be secure?


Likely yes, as long as you don't make that from a compromised system.  Use a known-clean computer to download the ISO and create the live media.

The malware would have to be in your machine's firmware to remain a problem then.  How likely do you think that is?

You seem to have misunderstood my question. I asked, if this machine is compromised to a degree, can I still likely use said machine to get a new OS ISO and make a install live from it? Assuming my system is compromised a bit, with it being Ubuntu, that doesn't necessarily it can corrupt a ISO and live flash making. Obviously from a known clean would be fine, but even known clean is a bit.. you can never know absolutely sure a system is absolutely clean, like, ever, not 100%. But is there a way to be reasonably sure that a new OS download and live disking would be safe from corruption / way to check it for said download and live usb, being free from corruption? Even using this machine and OS in question.

And a issue with the OS is far from bios/CMOS infection if that is what you mean by "firmware" But if you want to get technical, true firmware can't be infected, because you can't install anything on it or change it, it's static, that's what makes it different from software.

Regarding antivirus, they really don't exist for Linux. Further complicating it is how out of date my OS is.** Is there ways I can tentatively check for system corruption? I know I can't be 100% sure if doing it from the system in question, but surely there are signs to look for and test for?**

BTW, no one besides me has physical access to my PC. So unless some government is out to get me, broke in, corrupted my PC and than left without a trace, any first person corruption isn't likely to say the least (and I'm not a international spy). And I don't just install anything, most of the stuff installed by me were from Ubuntu software center.

---

### Post by Bucky Ball on 2016-11-11
Download the bittorrent file from the [alternative downloads page here]("https://www.ubuntu.com/download/alternative-downloads") and torrent the ISO.

Once you have it, [check the md5sum by following this]("https://help.ubuntu.com/community/HowToMD5SUM#Check_the_iso_file") then [go here]("https://help.ubuntu.com/community/UbuntuHashes") to find the appropriate hash for the ISO you downloaded.

Do they match, the hash your ISO gave in the terminal and the one listed on the hash page? If so, you're good to go.

---

### Post by ubin2 on 2016-11-11
So if the download is good, even if I use this system to make a live USB of that download, that live USB will also be good? Some maleware can't corrupt it at that stage?

And if the system is compromised to a degree, I can still trust the md5sum number I get from terminal?

---

### Post by &amp;KyT$0P# on 2016-11-11
> **ubin2 said:**
> ** Is there ways I can tentatively check for system corruption? I know I can't be 100% sure if doing it from the system in question, but surely there are signs to look for and test for?**
See [this]("https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned").

---

### Post by ubin2 on 2016-11-12
Hmm, seems like this will be alot of iffy work. May I post some of this for you guys to look over?

Let's say I do see some worrying signs, I ask again, how much can a partially compromised system really infect a ISO or assuming md5sum sum checks out, the terminal display or the live USB install?  

P.S. I keep on having to repeat the same questions to get answers. Might I please not have to do this so much?

---

### Post by &amp;KyT$0P# on 2016-11-12
> **ubin2 said:**
> Hmm, seems like this will be alot of iffy work. May I post some of this for you guys to look over?
Sure, as long as it doesn't contain any info you'd rather not share with the entire Internet.

> P.S. I keep on having to repeat the same questions to get answers. Might I please not have to do this so much?
I know it's frustrating but it's the nature of the beast.  Unfortunately with us being in different timezones and different schedules, the people who can answer might not be online when you first ask.  And if too many posts pile up in the mean time, the unanswered question might end up a bit lost.

Plus some of your questions are tricky and we don't want to give you wrong advice.  I for one rather not respond when I'm unsure of what I'd be saying.

So don't feel singled out.  It happens to us too.  I've made many "bump" type post, in fact I'm going to go do another one right now.

---

### Post by oldfred on 2016-11-12
Did you ever resolve that is was not just a run-away log file. Due to missing settings in boot?

A lot of users think they may have virus issues as with Windows it is common. But with Linux much less so.

---

### Post by ventrical on 2016-11-12
> **ubin2 said:**
> You seem to have misunderstood my question. I asked, if this machine is compromised to a degree, can I still likely use said machine to get a new OS ISO and make a install live from it? 

 If it is a hardware problem , no.

Please share your hardware specs.

Go to terminal: Ctrl+Alt +t

Then

```

sudo apt-get install inxi

```

Then:

```


inxi -Fxz


```

Then:

copy and paste here.

 Sounds to me you have combination of problems with harddrive, ddr and BIOS but we need to see some hardware specs.  Otherwise we are playing 20 questions .. going around in circles .. and difficult problem to solve without hardware info. A bad SATA cable connect or loosely fitted memory module can cause similar behaviour and emulate virus/buggy activity that you are mentioning.

Regards..

---

### Post by ubin2 on 2016-11-17
Obviously if it is a hardware problem, than my system wouldn't be compromised. That is** painfully** obvious ventrical, I might not be a genius, but I feel like I'm being talked to like I am a idiot when I get told something like. That is just my feelings, not a accusation towards you, I'm sure you didn't mean to make me feel like a idiot.

The question was, "if this machine is compromised to a degree, can I still likely use said  machine to get a new OS ISO and make a install live from it?" Compromised means software. (or fancy spy tech, but again, I am not a international spy)

And how is hardware specs going to tell you if a Sata cable or RAM stick is lose? I did build this PC myself out of quality brand new parts I purchased, I did make sure all cables and cards were firmly in.  I really can't imagine knowing which motherboard and CPU I went with or the model of my HDD would tell you anything. Please explain, both so I can understand where you are coming from better and because I am damn curious how this could help/apply, maybe I will be able to learn something new about computers from this. Besides, it would be a super hassle digging up all that info. I'd either have to look into my old purchase records from the websites (and have to log in using a potentially compromised system) or pull parts out of the PC and find the labels (no can do right now)

Anyway, earlier in this thread (for those who don't want to bother or lack the time to read previous posts) it was established that I had Nepenthes installed, I can not be sure if I had installed this myself or not. Nepenthes was making a giant ass log file which when deleted freed up like ~4gb. No one has has physical access to my PC. And the few programs I have installed mostly have come from Ubuntu software center,(only a few exceptions that were really necessary and given by guidance/research).  All the content from Ubuntu software center is carefully vetted to not be maleware, right? So probably just that I had installed Napenthes, forgot about it, and it isn't a hardware or software issue, right? I mean considering what I said here, what do you figure my odds of being compromised is?

But again back to my question, lets say worst case scenario, since it's always good to cover all your bases. Let's say I am somehow somewhat compromised with maleware (can't be fully compromised, no real suspicious activity other than the Napenthes thing, unless it's all just being recorded somewhere, someone just bidding their time to strike with ID theft or something)  That doesn't necessarily mean any ISO is corrupted, right? If I download the ISO through torrent and checksum it, could a semicompromised system fake the checksum output to make it seem legit? And if I can be sure the download is all good, could the act of making a live USB of it from the compromised system, realistically somehow pass that compromisedness, virus or whatever else, to the live USB and onto the fresh install?

---

### Post by kpatz on 2016-11-17
If you really want to play it safe, download the iso from another, known clean, machine.

Do you still have the original iso you installed from in the first place?

---

### Post by ubin2 on 2016-11-17
Again, there is no way to know any machine is clean. Originally I put it on a USB drive from a old winxp machine, who knows, that machine could have been compromised. But there needs to be a limit to how paranoid we should be otherwise how can we do anything.

So short of that, please answer my questions about risks.

---

### Post by dragonfly41 on 2016-11-17
> [COLOR=#000000]Originally I put it on a USB drive [/COLOR][COLOR=#000000]a old winxp machine, who knows, that machine could have been compromised.

winxp is long past its sell by date and is vulnerable, so that scenario is quite possible.

Why not install VirtualBox and install Ubuntu into a VM inside VirtualBox?  
This will give you a reasonably secure sandbox for sensitive applications (Ubuntu within Ubuntu).
Then within the VM Ubuntu you can prepare an installation USB to replace the suspected compromised system.



[/COLOR]

---

### Post by ubin2 on 2016-11-17
I know very little about Virtual Box, and my OS is too out of date to install much of anything new anyway. And are you saying that with a possibly partially compromised system that checksum/mdsum numbers could be falseified or live USB could be corrupted? But installing a VM on said suspect system and then doing all that within, is safe? I don't get it.

---

### Post by &amp;KyT$0P# on 2016-11-17
If you have any live media at all, for any version of any OS, use that live system to download the Ubuntu ISO and create the new Ubuntu live media.  That should get you a known-clean start, as much as it's possible to know any system is clean.

As for risks of using your existing system, here's an idea.  The utility to make a live media in Ubuntu is [FONT=Courier New]dd[/FONT].  So how about we check that the sha224 hash of [FONT=Courier New]dd[/FONT] on your 11.04 system, matches what I get for the same [FONT=Courier New]dd[/FONT] version?

I'll download the package from [the old-releases site]("http://old-releases.ubuntu.com/"), but I don't know which one you've got.

Please post the output of this command -
```
dpkg-query -S $(which dd)
```

Then this command -
```
dpkg-query -s <packagename>
```
replacing <packagename> with the package name from the first command.

---

### Post by dragonfly41 on 2016-11-17
Pursuing this hypothetical case of an interloper I found these discussions ...

[http://security.stackexchange.com/questions/86234/how-do-i-check-the-hash-of-an-iso](http://security.stackexchange.com/questions/86234/how-do-i-check-the-hash-of-an-iso)

[https://askubuntu.com/questions/326397/verifiying-ubuntu-iso-with-repository-gpg-keys](https://askubuntu.com/questions/326397/verifiying-ubuntu-iso-with-repository-gpg-keys)

[https://help.ubuntu.com/community/VerifyIsoHowto](https://help.ubuntu.com/community/VerifyIsoHowto)

...

*Quis custodiet ipsos custodes?*

---

### Post by ubin2 on 2016-11-24
If my system was somehow somewhat compromised, and I felt confident the ISO was legit/uncorrupted, then made a live USB from that ISO for installing with the system in question, how possible would would it be for the theoretical hacker to compromise the live USB?  All three of Dragonfly's links only deal with hash verification and not the step after that.

---

### Post by &amp;KyT$0P# on 2016-11-24
If I understand correctly, they'd pretty much have to do that as it's being written.  Because the rest of the time your USB would be plugged in, the potentially-compromised OS won't be running.

How possible is that?  Well, if the utility that writes the live USB isn't compromised... then in order for there to be a problem, I would think your kernel would have to be compromised, no?  And that'd be a lot bigger than "somewhat compromised".

Again, post the info of the package containing [FONT=Courier New]dd[/FONT] on your system, and I'll try to download it and post some hashes for you to check against.

---

### Post by ubin2 on 2016-11-24
So with things as I described, does it sound like something as bad as kernel compromise?

---

### Post by &amp;KyT$0P# on 2016-11-24
I don't know.  Someone else might, with a little more info.

To clarify, did all the visible signs of the problem go away when you deinstalled Nepenthes and deleted its logfiles?

Do you see glaringly obvious irregularities in [FONT=Courier New]/var/log/syslog[/FONT], such as out-of-order timestamps?

Also worth looking at net connections of your computer.  Close any browsers, email clients, etc - any applications that you've knowingly got connecting to the Internet.  Then run this in a Terminal -
```
sudo netstat -apv > ~/netstat-test1.txt
```
Please open the resulting text file ([FONT=Courier New]~/netstat-test1.txt[/FONT]) and post here the "Active Internet connections" section.  (I don't think we need to see the "Active UNIX sockets" section.)
And yes, it's normal and expected to have some Internet connection entries in that situation, so don't panic just out of seeing stuff listed.

EDIT
Also please post the Terminal output of that netstat command, if there is any.

---

### Post by truepurple2 on 2017-01-12
> **halogen2 said:**
> 
To clarify, did all the visible signs of the problem go away when you deinstalled Nepenthes and deleted its logfiles?
The issue of space vanishing went away and I got back much space. Well whether bits of space here or there vanished, I don't know, but I haven't run out of space since. Recently I was struggling bringing up certain websites with different levels of success with different browsers. It was after I temporarily lost my internet thanks to a late bill. Seems to be working now though.

> **halogen2 said:**
> 
Do you see glaringly obvious irregularities in [FONT=Courier New]/var/log/syslog[/FONT], such as out-of-order timestamps?
Rapidly scrolling down page, I don't see any out of order time stamps. Ever so often it would tell me syslog change and would I like to update it. One of those times there is a single blank line, not sure if that means anything. Could that be someone mid process of deleting a line? Or is that normal for the system?
[https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned](https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned) there is time spaces bigger than 5 minutes in there. 

Any other irregularities, I wouldn't know if I stared straight at it. Here, [http://pastebin.com/QxTAbBbe](http://pastebin.com/QxTAbBbe) do you see anything irregular?

> Also worth looking at net connections of your computer.  Close any browsers, email clients, etc - any applications that you've knowingly got connecting to the Internet.  Then run this in a Terminal -
```
sudo netstat -apv > ~/netstat-test1.txt
```
It doesn't work. After a long pause.
netstat: no support for `AF IPX' on this system.
netstat: no support for `AF AX25' on this system.
netstat: no support for `AF X25' on this system.
netstat: no support for `AF NETROM' on this system.
  And no "netstat" file can be found.

Maybe worth noting, I have purchased stuff using this PC and paid bills using it, and no mystery charges.

---

### Post by truepurple2 on 2017-01-16
Can anyone help please?

---

### Post by truepurple2 on 2017-01-27
I answered the questions asked of me, if not to help me, why was I asked these questions?  Please help.

---

### Post by howefield on 2017-01-27
> **truepurple2 said:**
> I answered the questions asked of me, if not to help me, why was I asked these questions?  Please help.

You weren't asked any questions, ubin2 was....

---

### Post by truepurple2 on 2017-02-03
I am ubin2, I use the webpage log back in already filled thing when I log in after my log in expires, so not sure why it's giving a different username all of a sudden.

---

### Post by coffeecat on 2017-02-03
> **truepurple2 said:**
> I am ubin2, I use the autofill thing when I login after my login expires, so not sure why it's giving a different username all of a sudden.

It was entirely within your control. You have two Ubuntu One SSO accounts, each with a different email address and now linked to two different forum accounts. All explained here: [https://ubuntuforums.org/showthread.php?t=2230004](https://ubuntuforums.org/showthread.php?t=2230004) .

If you need help with sorting our your two accounts, please post in the [Resolution Centre](https://ubuntuforums.org/forumdisplay.php?f=123).

---

### Post by &amp;KyT$0P# on 2017-02-03
> **truepurple2 said:**
> Any other irregularities, I wouldn't know if I stared straight at it. Here, [http://pastebin.com/QxTAbBbe](http://pastebin.com/QxTAbBbe) do you see anything irregular?
Did you reboot the system around line 28 and again around line 1025?  If so, nothing sticks out to me.  But again, I'm no expert.

> It doesn't work. After a long pause.
netstat: no support for `AF IPX' on this system.
netstat: no support for `AF AX25' on this system.
netstat: no support for `AF X25' on this system.
netstat: no support for `AF NETROM' on this system.
And no "netstat" file can be found.
The relevant output went to a file named [FONT=Courier New]netstat-test1.txt[/FONT], located directly in your home folder.

> Maybe worth noting, I have purchased stuff using this PC and paid bills using it, and no mystery charges. 
That **is** worth noting and a good sign :)

---

### Post by truepurple2 on 2017-02-04
> Did you reboot the system around line 28 and again around line 1025
No  idea. Thanks to fans that sound like they are dying in agony from a  blender after my computer is off even for a short amount of time,(takes a  good amount of time of them being down before they settle/quiet down) I  leave my PC on all the time now. I have restarted to fix issues though.

Found it. [netstat-test1.txt]("http://pastebin.com/kVaDCA91")

Seeing "w2.hackademix.net" in the list does not seem like it would be a good sign. But maybe it's nothing.

---

### Post by &amp;KyT$0P# on 2017-02-04
What's [FONT=Courier New]avgtcpd[/FONT]?

That netstat otherwise looks fine to me, you just have Firefox and Opera browsers open.

> **truepurple2 said:**
> Seeing "w2.hackademix.net" in the list does not seem like it would be a good sign. But maybe it's nothing.
That domain is associated with NoScript - [https://forums.informaction.com/viewtopic.php?f=7&t=22463]("https://forums.informaction.com/viewtopic.php?f=7&t=22463")

---

### Post by truepurple2 on 2017-02-07
I have been using Tomboy notes program to make notes etc. a bunch of stuff from there has vanished. Is this a worrying sign of hacker? Is there a way to find out what happened to the data and/or recover it?

---

### Post by &amp;KyT$0P# on 2017-02-07
Since you started [this thread]("https://ubuntuforums.org/showthread.php?t=2351899"), and I don't use Tomboy, I'll only reply to this part -
> **truepurple2 said:**
> I have been using Tomboy notes program to make notes etc. a bunch of stuff from there has vanished. Is this a worrying sign of hacker? 
That wouldn't be my first concern.  Rather odd thing for a hacker/malware to do.  Especially if nothing else is affected and everything else works fine.

---

### Post by &amp;KyT$0P# on 2017-02-07
Anyway, back to determining how compromised your system is or isn't.  Do you see any lines in [FONT=Courier New]/var/log/syslog[/FONT] similar to these, from a time you **_know_** you didn't reboot? -
```
Jan 11 09:32:28 myubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan 11 09:32:28 myubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Jan 11 09:32:28 myubuntu kernel: [    0.000000] Linux version 2.6.38-16-generic (buildd@batsu) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) ) #67-Ubuntu SMP Thu Sep 6 17:58:38 UTC 2012 (Ubuntu 2.6.38-16.67-generic 2.6.38.8)
Jan 11 09:32:28 myubuntu kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-16-generic root=UUID=1e8ea1f1-4065-414b-8724-c23425fe903e ro quiet splash vt.handoff=7
```


A quick search for [FONT=Courier New]avgtcpd[/FONT] indicated it's part of AVG for Linux.  The port numbers in your netstat output are consistent with that as well.  Do you have AVG for Linux?

---

### Post by truepurple2 on 2017-02-08
I was looking for antivirus for Linux for awhile. It could be from that.

I didn't know that knowing when I rebooted would be useful information. So I can not say for sure any particular time is a time I didn't reboot. I also have a very irregular day and sleeping pattern so it really could be at any time.

---

### Post by &amp;KyT$0P# on 2017-02-08
Thanks for the info.  I think you can now find out how compromised your system looks -
> **truepurple2 said:**
> I didn't know that knowing when I rebooted would be useful information.
Neither did I, until looking at that syslog paste.

For the next few days or so, could you please keep track of the times of rebooting?  Then if you see log messages like those I [quoted]("https://ubuntuforums.org/showthread.php?t=2342453&p=13604319&viewfull=1#post13604319"), but from some **other** time, we'll know something's wrong.

But if you only see those type messages from times you **did** reboot, your system appears OK to me.  i.e. likely not compromised.

Let us know, thanks. :)

---

