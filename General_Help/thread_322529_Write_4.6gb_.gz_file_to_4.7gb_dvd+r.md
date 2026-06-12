---
title: "Write 4.6gb .gz file to 4.7gb dvd+r?"
date: 2006-12-20
forum: General Help
---

### Post by dannyboy79 on 2006-12-20
I found this cool backup utility a guy wrote that uses cpio and another little program called fsplit and it creates backups (compressed using gzip) of whatever I want. I wanted to backup my music, movies, and pics as I have over 1tb of total data onto dvd's. well this program has done what I wanted it to do, it has created all the backups with each .gz file being 4.6gb in size (which this guy stated he has been able to ftp over to his windows box and then burn onto a dvd) well I want to just burn them using my linux box no need to ftp them over to windows. well, I try to use nautilus and even though it lets me paste the file into it's window, then i hit write disk and it appears to write (there are 2 file, the 4.6gb .gz and a file called list, which is actually a file which contains all the files that were backed up along with their entire path information so when it comes time to do a recovery, I simply type in backup -r and it reads this list file and then spits all the files back out right where I backed them up from) so anyway, after it states the burn is complete, I check the dvd and the only thing on it is the list file and that's it. then I went to gnomebaker and that won't even let me select it? then in nerolinux, that states the file is to big for iso format? it asks if I want to switch to udf. I don't think I want to do that correct? so I am wondering why can I not burn this data when it doesn't contain more than what the dvd can hold?? what's weird also is that this guy has been burning these 4.606gb .gz files in windows for over 5 years. why can't linux do it? is there some kind of 2gb file size limit, I thought I may have read that on his website. he wrote this: Note 1: fsplit must be at least version 2.2 if you intend to burn DVDs. Earlier versions of fsplit (as included up to backup version 4.0) max out at 2Gb, which I didn't realise until I modified the script to allow for DVD-sized chunks. Your Unix/Linux file system also needs to be able to handle > 2Gb files, of course. In the case of Linux, this basically means elf2 or better. 
My DVD burner is actually on an adjacent Windoze XP PC, so once the chunks have been created on the Linux server, I just FTP them over to that machine to burn them. Of course, if you have a burner on the Linux server itself, you can just create them locally - using (eg) CdRoast. 
and what I downladed meets the requirements of fsplit etc etc. 

i wonder if I can just change the command to split the files smaller than 4.6gb.  maybe 4gb. i'll try that but maybe someone can answer my question so that I don't have to erase tons of .gz files and recreate archives of almost 1 tb of music, movies, and pics. thanks for anyone who can help.

---

### Post by orb9220 on 2006-12-20
Yes This has always been a pet peave with me. If the burn engine does not have overburn then you can only burn up to 4.4 gig which is really 4.38gb. And to top it off all media cannot be overburned due to quality issues.

For a problem free burn I always set my programs like dvd shrink to rip to 4.4gb.
DVD5 standard is 4.7gb and I cannot get it to fit on a single layer dvd and don't understand why that is. If I create any iso or size that is larger than 4.4 like 4.5 programs always say there is not enough space on dvd blank.

Go Figure

---

### Post by logos34 on 2006-12-21
The answer to this may be very simple: a single-layer dvd holds 4.7 GB, where 1 Gigabyte=1,000,000,000 bytes (base 10 or 10 to the 9th power), but the operating system measures kilo-, mega- and giga-bytes in binary form (base 2), where a kilobyte (KB)=1,024 bytes (2 to the 10 power), a megabyte (MB)=1,048,576 bytes (2 to the 20th), a gigabyte (GB)= 1,073,741,824 bytes (2 to 30th), and so on.  

So, try making your files no bigger than 4.38 GB and they should fit on a 4.7 GB dvd (4.38 x 1.073=4.69974 GB).  

It's all an advertising gimmick by the dvd and hard drive makers to confuse everybody and make their product specs look better.  (Most people who buy hard drives think they 'lose'  some space after formatting when in actual fact no such thing occurs -- the os merely measures gigabytes differently.)

---

### Post by dannyboy79 on 2006-12-21
easier said than done. this cool backup and splitting program was written to use fsplit which will only allow the files to be split into either 4.7 or 8.5 or whatever a double-layer disc is so this sucks!!!!! i did try to ftp it over to windows and was able to burn the file without a hitch in nero. this is ok for this time but next time looks like I'll have to find an alternate solution to backing up my movies, pics, and music. i use sbackup for my entire system minus media stuff which I back up once in awhile,  do you guys know if tar, while it's creating the archive, can make archives into say 4.3gb files without having to only select a certain amount? for example, i want to just be able to pick a folderthat contains say 20gb and tell it to back this up into chunks of 4.3gb so I can then write them to dvd's? that's why I thought this program was so cool. it works really sweet, I simply type in backup location of files i want backed up goes here -s4.7 and then it uses a .conf file located in /etc/ so that it knows where to put the backup archives and it even uses a file if I want to exclude anything so it's just top bad that fsplit only allows certain block sizes like 4.7 or 8.5!!! does anyone know of another program that could say take a 120gb tar file and then split it up into chunks so that they could be burned onto dvd? thanks for ya'll help this far.

---

### Post by logos34 on 2006-12-21
Disk ARchive?  

[http://dar.linux.free.fr/doc/Features.html](http://dar.linux.free.fr/doc/Features.html)

kde gui:
[http://kde-apps.org/content/show.php?content=10367](http://kde-apps.org/content/show.php?content=10367)

---

### Post by dannyboy79 on 2006-12-21
thaks, i'll give dar a try. i don't want to install a kde app though. don't like the dependencies it brings with it.

---

