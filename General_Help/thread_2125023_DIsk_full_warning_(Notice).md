---
title: "DIsk full warning (Notice)"
date: 2013-03-12
forum: General Help
---

### Post by jadtech on 2013-03-12
I am running  Ubuntu 12.04 I have been running it on this lap top since I bought it last spring a year give or take a few weeks ..

it does have windows installed thoughI have never booted or used windows  since I have had the computer .. 

this HP haslike a 700 GB HD though I only freed and formated like 50 or 60 GB for Ubuntu when I installed it , it has been having odd behaviour  such as seeming to slow to a stop dark screen the side bar scrolls but nothing else  goes till things go back to normal  not sure if this is a simptom of the  laptop disk space getting nearer to full  or not  Today this after noon out of no where I get a notice that says somrething like disk near full 1.5 gb space left empty trash to continue .. 

i am pretty good with Ubuntu but no expert yet so I have no clue how to confirm disk space , conky I load shows only less then 25% of the space is used not sure if that  is an honest scale or is off  for what ever reason  either way I only fomated 50 or 60 gig  the reast of the 700GB disk is empty never used   and wiindow and recovery partition .. 

my question if the disk is full is there any way to just open more space without starting over I really dont care if windows gets messed up I have never used it  .. 

I am thinking also some how I have got things so I am getting beta updates  I receive what I believe is  a huge number of updates weekly the last few months  and the lap top has been having strange behaviour running hard at times ..

is it possble to fix the disk space with out a reinstall , info that could be handy is I only have  2 patitions for ubuntu main partition and a swap .

---

### Post by jadtech on 2013-03-12
ok it is officail I did a check and the 56 GB partition I  set for Ubuntu is at almost 54GB the disk is so full  mail program crashes because of a lack of space to receive mail ..  right next to it g parted shows me 613 gb of free disk space where window 7  resides .. 

Not sure why it is full other then update I hardly install any programs  what so ever maybe 7 in the last year, I have delteed nearly everything else  to make space  to keep the browser going here.. 

the lap top has been running rough for weeks so I am guesing it has been close for a few months and fragmented pretty badly ..

still  my question is there any way to  expand the Ubuntu parttion without out a complete reinstall  I really  dont care if  expanding messes up the windows any how I left it there at the time  as more of a securlty thing I was still fair ly news to ubuntu still ..

---

### Post by decrepit on 2013-03-13
If you have a live CD with gparted on it, you should just be able to shrink the windows partition and expand the ubuntu partition into the freed space.
Make sure the live cd doesn't automatically mount your hard drive though. 

You have emptied the trash I hope?
The file browser should show where all the data is.

---

### Post by jadtech on 2013-03-13
ok since there was no reply I went ahead and attempted to figure this out on my own .

in short  yes you can grow the partition without  reinstalling , I have opened up 400 gb of space , did it with Gparted and everything rebooted no problem  the change took just over an hour ..

the lap top is running  100X bettwe then it had in a few months it is back to speed no more lagging on program load ing and such eveninternet seems quicker  I may  do a reinstall any how as  ubuntu has other issues on this machine  I believe I got a beta few beta updates thatr caused my the good wireless driver from working one that is working has ver weak recive and looses connection even 2 feet from the router.

either way this problem is solved  the big key is to remember to unmount all partitions including turning off the swap because all the partitions are inside a partition and if one is mounted none of then can be moc=ved or resized ..

---

### Post by Mark Phelps on 2013-03-13
First of all, expecting folks to get back to you with details responses in 11 hours is unreasonable.  You should know that this is a worldwide forum, and the person with the best response could be 18 hours away!

Second, did you shrink Win7 using GParted? IF so, have you tried booting back into it? If you did the first, you MIGHT be lucky and be one of the few that used GParted and did NOT corrupt Win7 in the process.  Had you waited, I would have seen this thread and advised you NOT to use Gparted.

In future, it might be better if you showed more patience before doing something potentially harmful to your system like repartitioning.

---

### Post by sdb2028 on 2013-03-16
Just an added note to your full disk problem, your disk should not be full from just installing a few applications. Just expanding your partitions will only work untill your drive fills again. Your underlying problem could be one such as I had , which is massive  sized logs in /var/log.
To check this run "sudo ls -lha /var/log" (without " ") and look for files which are several gigs. Probably will be kern.log or syslog, but check for others. I found that my initial problem was coming from using Dropbox, it was creating syslog and kern.log files in the 30g range. Turned off Dropbox and ran "sudo cp /dev/null /var/log/syslog" to zero out the log file, (also on kern.log). You can use this method to clear the log and retain it initial file status.
You may need to figure out which application is the culprit on your system (may not be the same as mine) and turn it of or uninstall it.

---

