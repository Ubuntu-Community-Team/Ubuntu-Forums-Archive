---
title: "[SOLVED] Beagle File Indexing"
date: 2005-06-15
forum: General Help
---

### Post by manicka on 2005-06-15
I just can't get beagle to index files properly. It seems to start okay then gets stuck in certain directories. When I log out and back in the index seems to purge itself. I also get mutliple hits for the same file when it does index some files.

Any thoughts on what could be wrong?

I've tried versions 0.09, 0.0.10 and 0.0.11 and have all the packages suggested on the Ubuntu getting started page. I've used the deb package at backports and compiled my own using checkinstall or just 'make instal'l with mixed results.

I've tried 
beagled
beagled &
beagled --deny-backend liferea
and 
beagled --deny-backend liferea &

when starting the daemon

---

### Post by xvlun on 2005-06-15
please try version 0.0.11.1, the purging problem should be fixed as off today.

could the problem with stuck direcotries caused by nonstandard characters and erroneous encodings?

---

### Post by manicka on 2005-06-15
[QUOTE=xvlun]please try version 0.0.11.1, the purging problem should be fixed as off today.[/QUOTE]
Will do, thanks
[QUOTE=xvlun]could the problem with stuck direcotries caused by nonstandard characters and erroneous encodings?[/QUOTE] I don't think so, bit I'll investigate.

thanks again, ....ah the joys of alpha software  :)  ](*,)

---

### Post by manicka on 2005-06-16
0.0.11.1 runs okay and does't purge now,   but it just won't index my files beyond one or two levels of folders :-k ...sigh

---

### Post by Majlo on 2005-06-16
[QUOTE=manicka]0.0.11.1 runs okay and does't purge now,   but it just won't index my files beyond one or two levels of folders :-k ...sigh[/QUOTE]

I have the same problem with any version Beagle .Etc 0.0.9, 0.0.10, 0.0.11
Any suggestion ?

---

### Post by manicka on 2005-06-17
[QUOTE=manicka]0.0.11.1 runs okay and does't purge now,   but it just won't index my files beyond one or two levels of folders :-k ...sigh[/QUOTE]

Actually, spoke to soon. I'm still purging with 0.0.11.1

---

### Post by manicka on 2005-06-17
Bah... I'm giving up on this for a while. Life is too short  \\:D/ 

Think I'll just run beagle with the file backend denied until breezy and use the gnome file search for the time being. Actually, I'll probably give each release a whirl to see what happens.

Not a bad compromise really as it's better than no beagle at all. I've recently come from SuSE where beagle was working well for me and find that I've become very dependent on the mail and web indexing.

---

### Post by mike998 on 2005-06-18
Thought I would put this here just in case it helps with anyone.
I agree - Beagle looks really cool and I think it would be worth installing but life is just too short to get this working right now.

[QUOTE=mike998]After seeing many posts on Beagle, I decided to install it.  I have followed the instructions to install it at the following page : [http://beaglewiki.org/index.php/UbuntuInstall](http://http://beaglewiki.org/index.php/UbuntuInstall) 
The only difference is that my hard drive is partitioned to just a root, swap and that's it.  Here's my /etc/fstab:
```
mike@wolfspider:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro,user_xattr 0       1
/dev/hdc5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
``` 
This is due to the partitioning that is default with the system install...
I have run the daemon using the following command : beagled --fg --debug
However, when beagle gets to the first directory in my home directory it seems to stick, and won't index any files beyond that.  Here is the output:
```
DEBUG: Starting task File System Crawler
DEBUG: Crawl Task Scheduling /home/mike/Shorts (state=PossiblyClean)
DEBUG: Finished task File System Crawler in .00s
DEBUG: Starting task Crawling /home/mike/Shorts
DEBUG: *** What should we do with /home/mike/Shorts/batman_dead_end_full_screen.mpg?
DEBUG: *** Doing nothing to /home/mike/Shorts/batman_dead_end_full_screen.mpg
DEBUG: *** What should we do with /home/mike/Shorts/Grayson_web_large.mov?
DEBUG: *** Doing nothing to /home/mike/Shorts/Grayson_web_large.mov
DEBUG: *** What should we do with /home/mike/Shorts/Worlds_Finest_Hi.mov?
DEBUG: *** Doing nothing to /home/mike/Shorts/Worlds_Finest_Hi.mov
DEBUG: *** What should we do with /home/mike/Shorts/weapon_of_choice_-_fatboy_slim.asf?
DEBUG: *** Doing nothing to /home/mike/Shorts/weapon_of_choice_-_fatboy_slim.asfDEBUG: *** What should we do with /home/mike/Shorts/artofthesaber.mov?
DEBUG: *** Doing nothing to /home/mike/Shorts/artofthesaber.mov
DEBUG: *** What should we do with /home/mike/Shorts/artofthesaber_concept.mov?
DEBUG: *** Doing nothing to /home/mike/Shorts/artofthesaber_concept.mov
DEBUG: *** What should we do with /home/mike/Shorts/BattleStar Galactica - 2004 Pilot movie [Full] (Exxon's VP6).avi?
DEBUG: *** Doing nothing to /home/mike/Shorts/BattleStar Galactica - 2004 Pilot movie [Full] (Exxon's VP6).avi
DEBUG: *** What should we do with /home/mike/Shorts?
DEBUG: *** Doing nothing to /home/mike/Shorts
DEBUG: worker added: name=HandleConnection (899) refcount=1
DEBUG: worker removed: name=HandleConnection (899)
DEBUG: Done sending request
DEBUG: Finished task Crawling /home/mike/Shorts in .02s
``` 
Which repeats over and over...  Does anyone have any idea why this is?  I really like the look of beagle and it would make it easier to find stuff, but it's just plain not working.[/QUOTE]

---

### Post by burlap on 2005-06-22
0.0.11.1 is purging, this is an example. 

Beagle got stuck, CPU usage went up to 60-80%, finishing session made it purge file index. 

I can't really figure out what is more relevant, but responsible files seem to be mysql manuals (html file of 3.7 MB, tar.gz of 1MB, pdf of 4 MB, 35 html files of 4 MB in total):
1. I found this:```
05-06-22 16.53.17.99 08349 IndexH DEBUG: + file:///home/burlap/dokumenty/worek/instrukcja/mysql/manual-split.tar.gz
05-06-22 16.53.18.33 08349 IndexH DEBUG: + file:///home/burlap/dokumenty/worek/instrukcja/mysql
05-06-22 16.53.18.33 08349 IndexH DEBUG: No filter for /home/burlap/dokumenty/worek/instrukcja/mysql
05-06-22 16.53.18.34 08349 IndexH DEBUG: + file:///home/burlap/dokumenty/worek/instrukcja/mysql/manual.html
05-06-22 16.53.19.29 08349 IndexH DEBUG: Helper Size: VmRSS=47,8 MB, size=4,67, 91,8%
05-06-22 16.53.20.29 08349 IndexH DEBUG: Helper Size: VmRSS=48,0 MB, size=4,69, 92,3%
05-06-22 16.53.21.30 08349 IndexH DEBUG: Helper Size: VmRSS=50,1 MB, size=4,90, 97,6%
05-06-22 16.53.22.30 08349 IndexH DEBUG: Helper Size: VmRSS=52,3 MB, size=5,12, 102,9%
05-06-22 16.53.22.30 08349 IndexH DEBUG: Process too big, shutting down!
05-06-22 16.53.22.59 08349 IndexH DEBUG: Calling BeginShutdown
05-06-22 16.53.22.59 08349 IndexH DEBUG: Beginning shutdown event
05-06-22 16.53.22.63 08349 IndexH DEBUG: CancelIfBlocking Beagle.Daemon.ConnectionHandler
05-06-22 16.53.22.63 08349 IndexH DEBUG: Done with shutdown event
05-06-22 16.53.22.63 08349 IndexH DEBUG: (1) Waiting for 2 workers...
05-06-22 16.53.22.63 08349 IndexH DEBUG: waiting for HandleConnection (345)
05-06-22 16.53.22.63 08349 IndexH DEBUG: waiting for server 'socket-helper'
05-06-22 16.53.22.85 08349 IndexH DEBUG: worker removed: name=server 'socket-helper'
05-06-22 16.53.22.85 08349 IndexH DEBUG: (2) Waiting for 1 worker...
05-06-22 16.53.22.85 08349 IndexH DEBUG: waiting for HandleConnection (345)
05-06-22 16.53.22.85 08349 IndexH DEBUG: Server 'socket-helper' shut down
```
2. But also beagle produced lots of sleeping pdfinfo and pdftotext processes (I haven't counted but it must have been around 60).

When it restarted, I found the following in the logs:
```
05-06-22 17.18.08.15 10922 Beagle DEBUG: Found dangling locks in /home/burlap/.beagle/FileSystemIndex/Locks
05-06-22 17.18.08.15 10922 Beagle DEBUG: Purging /home/burlap/.beagle/FileSystemIndex
```
I don't know which is more relevant and if it helps at all. Beagled index 6000 files in one sesssion, when I logged out and back in, it was ok, and after index-info showed 7200 it got stuck. I logged out and file index got purged, maybe I was not patient enough but I have a laptop and my fingertips were already burning.

---

### Post by manicka on 2005-06-23
[QUOTE=burlap]0.0.11.1 is purging, this is an example. 
Beagle got stuck, CPU usage went up to 60-80%, finishing session made it purge file index. 
[/QUOTE]
I get the same type of outputs in debug. I've turned off file indexing for now (beagled --deny-backend files ) as webpages, mail, chat, liferea etc are indexing perfectly and I'll stick with gnome file search until it's sorted out. Hopefully all will be well by breezy. 

Quite frustrating really  ](*,)  but I guess 80% functionality is better than none.

---

### Post by burlap on 2005-06-24
Again, so far it does work for me. It turned out that the mysql manual pdf was corrupt (mysql fault) and it killed beagle. 

So you might look into the logs to see if there is anything that makes your beagle get stuck - and remove it (i.e. to an ignored path). 

(Of course it's not all so nice: liferea backend doesn't work, although I have 1800+ news indexed... I'm investigating...  ](*,) )

---

