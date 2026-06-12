---
title: "[SOLVED] Problems with starting administrative applications in 8.04"
date: 2008-05-21
forum: General Help
---

### Post by festlig-faetter on 2008-05-21
Hi everybody.
I recently upgraded my distribution from 7.10 to 8.04. But ever since, i can't launch any application that initates the 'Starting Administrative Application' to display in the bottom panel.
It shows up for about 10 sek. until it goes away, and the started application is never heard from again. :confused:
So far the applications i'm having trouble with is:

Software Sources
Synaptic Package Manager
Update Manager (that i can start, but can't get it to 'install upgrades')
And probably other, that i haven't found yet...

I have also tried to launch from a terminal:
```
gksudo nautilus
```
But the result is the same.:


Hope to hear from you.


Best wishes

Jesper

---

### Post by tinker312 on 2008-05-24
I'm having the same issue with running the administrative application.  I think this is the gui for sudo. Anyways, I think my issue is related to my hostname. Not sure why but that is the troubleshooting path I'm starting with.


Hey festlig-faetter.  Looks like this issue has came up before and fixed. Check out this thread.  [http://ubuntuforums.org/showthread.php?t=729690](http://ubuntuforums.org/showthread.php?t=729690)  

It fixed my issue.  It happened because I was tinkering around trying to connect to a windows network.  Turns out I had to install samba because it wasn't installed by default :)

---

### Post by LawrenceSalberg on 2008-05-26
Hmmm... having the same problem with 8.04, but no issues regarding Hosts as referenced above. 

But maybe there is something to it after all? I suddenly can't login to my XP Laptop via my Ubuntu desktop either. Shows the "Windows Network" and my "Workgroup" (or whatever Linux folks call it), but no Laptop. I did nothing and it was working just fine this morning before 22 updates came through the update channel.

Quite frustrating. Can't get into Synaptic Package Manager or Hardware Drivers. And of course, Update Manager loads, but if I click "Check" I'm doomed to Starting Administrative Application for about 10-15 seconds in the Taskbar, but no password request.

For reference, I run a decently fast machine with 2Gb of memory. I found an old thread from 2005 that seemed to be discussing the same issue way back on Ubuntu 5, but no resolution. Only common idea back then was that folks might have been running machines that were too slow. Well, whatever the problem might be now, I know that isn't it.

---

### Post by jetsam on 2008-05-26
Lawrence: Do you get an error message if you type:
```
sudo ls
```
in a terminal?

---

### Post by LawrenceSalberg on 2008-05-26
@Jetsam: No. Works as it normally does/should.

---

### Post by jetsam on 2008-05-26
Hmmm....  haven't a clue about your problem, then  :???:

Today's updates worked ok for me.  They included a kernel update and some gnome keyring updates.  I sort of suspect the gnome-keyring updates as causing your problem, but there are other possibilities.  

You asked in the other thread about a detailed change log for Ubuntu.  

I usually check the Synaptic history log under files-->history.  That's not good for you because you can't get into Synaptic.   

There should be a text file attached to this message with the names of the last two batches of updates to Hardy.

---

### Post by Gunman1982 on 2008-05-26
Open a console and execute 'sudo apt-get check'. That checks fro broken dependencies in packages.

---

### Post by festlig-faetter on 2008-05-28
Hi tinker312 (thinker? :) 
It solved my problem at least, thanks a lot.

---

### Post by error420 on 2008-05-29
> **tinker312 said:**
> I'm having the same issue with running the administrative application.  I think this is the gui for sudo. Anyways, I think my issue is related to my hostname. Not sure why but that is the troubleshooting path I'm starting with.


Hey festlig-faetter.  Looks like this issue has came up before and fixed. Check out this thread.  [http://ubuntuforums.org/showthread.php?t=729690](http://ubuntuforums.org/showthread.php?t=729690)  

It fixed my issue.  It happened because I was tinkering around trying to connect to a windows network.  Turns out I had to install samba because it wasn't installed by default :)


The link stated above fixed my issue. It was just not resolving the computer name due to networking issues on my work Domain under aliases. I went to network settings (system>>preferences>>network) and under the "hosts" tab my computer was known as ...(%HostName%.dadeschools.net) ... I just removed the .dadeschools.net part and restarted. Now administrative applications like update manager work correctly by asking me for my gksudo password. :) Thanks Tinker312!

---

