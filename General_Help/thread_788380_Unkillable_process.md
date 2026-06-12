---
title: "Unkillable process?"
date: 2008-05-09
forum: General Help
---

### Post by Ameneon on 2008-05-09
Using 8.04 and Gnome, I just discovered that totem was hanging from an earlier instance some days back, as shown in top;

  462 #####      20   0  162m  45m  23m D   96  2.2   5680:44 totem   

- basically using all the cpu time on the core it's running on. Now, obviously this isn't a very major problem or I'd have noticed before but still, a bit of a nuisance, as neither kill -9 462 or any other attempted kill (through system monitor or command line) have managed to get rid of the runaway process. I could reboot of course but...I don't wanna (naw seriously I will of course if that's the only way, I've just never encountered unkillable processes before on linux).

So, what to do?

---

### Post by wirelessmonkey on 2008-05-09
Give sudo killall totem a try

---

### Post by Ameneon on 2008-05-09
TY, unfortunately it didn't even bother to shrug at that one. Should've mentioned I tried sudo kill as well earlier, sorry. But thanks for the suggestion.

---

### Post by didooofidooo on 2008-05-09
what i know is that "kill -9" will kill any process because it sends a terminate signal to the kernel itself not to the process so i don't think that if you typed "sudo kill -9 [PID]" the process won't die
or try "killall totem"

---

### Post by didooofidooo on 2008-05-09
oh i forgot ... use "ps aux" and see which other processes totem uses and kill them

---

### Post by Ameneon on 2008-05-09
Thanks to you too, however no other processes are shown invoking totem or the file in speak either one. htop shows a number of processes for totem but does not seem able to kill them either. Rather peculiar.

---

### Post by arvevans on 2008-05-09
Do you by any chance have totem set to run automatically/continuously in System/Settings/Sessions?  

When you use "sudo kill -9 PID", does the PID number change to a new one on the next "ps -aux" listing?  If the PID number is changing, then you are killing totem but it is somehow getting re-spawned.

Obviously you have verified that you are using the real PID and not the VSZ or some other number (PID is in the second column of a "ps-aux" output).

Go to a Terminal screen, type "man kill" to see the manual page for the kill command.  There are additional commands referenced in the man page which may shed some light on the problem.

_._

---

### Post by Anduu on 2008-05-09
Try this...

Open System Monitor and open the processes tab.Then select View in the main menu and select All Processes and tick the Dependencies box.

This will give you a tree type view of your running processes.Find totem and you will probably see it is being run as a subprocess of another.

Kill the main process that Totem is under.That should do the trick.

---

### Post by Ameneon on 2008-05-10
Thanks again :)

Unfortunately (well, for the sake of the answer anyway) totem is not being respawned, PID is the same it has been all along. Also checked for dependencies, and totem appears to run under init, however so does the other user applications it appears, so I don't get the impression that's critical but perhaps I'm wrong?

Attached a screenie of system monitor:

---

### Post by Ameneon on 2008-05-10
Welp, I decided to reboot in any event as I was going to update the XP installation to SP3 anyway, but thanks to all for your suggestions. Guess there are quirks like these everywhere. Now if only FF is trimmed a bit so it doesn't eat quite so much CPU time and memory all will be peace and love in the land of 8.04..

---

### Post by glyph on 2008-05-16
I've experienced this too.

I believe this is a kernel bug in Hardy, which I've reported here: [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/230993](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/230993)

Please update the bug with details of how / when it happened, since it is currently a very vague report.

---

### Post by BlueSkyNIS on 2008-05-17
I can confirm this because I also couldn't kill it, see -> [http://ubuntuforums.org/showthread.php?p=4978931#post4978931]("http://ubuntuforums.org/showthread.php?p=4978931#post4978931")

](*,) #-o :confused:

---

### Post by amorangi on 2008-05-17
Same problem here, tried various combinations of kill etc, and from System Monitor etc. Totem just didn't want to die - a reboot was the only thing that would work - I've never encountered this before.

---

### Post by BlueSkyNIS on 2008-05-18
Please, make your input into bugs report: [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/230993]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/230993")

---

### Post by Geneset on 2008-07-18
Ok, its by no strech a solution, but it does the job i need. 

I changed the Nice values to 19, 
now everything i need runs happily and it'll fix itself the next time i reboot.

---

### Post by Breakablec on 2008-07-29
I am reproducing this problem now, and the process seems respawning all the time.

```
break@break-desktop:~$ ps aux | grep totem
break     8882  0.0  0.0   3004   748 pts/0    R+   23:46   0:00 grep totem
break@break-desktop:~$ ps aux | grep totem
break     8013 83.9  6.7 177376 69836 ?        Dl   20:17 175:03 totem file:///home/break/Desktop/a.avi
break     8884  0.0  0.0   3004   752 pts/0    R+   23:46   0:00 grep totem
break@break-desktop:~$ sudo killall -9 totem
break@break-desktop:~$ ps aux | grep totem
break     8013 83.9  6.7 177376 69836 ?        Dl   20:17 175:07 totem file:///home/break/Desktop/a.avi
break     8887  0.0  0.0   3008   776 pts/0    S+   23:46   0:00 grep totem
```

It could be some kind of codecs problem I guess. How do you debug one?

---

### Post by mosty friedman on 2008-07-29
try this dude, click Alt+F2 then type in the space xkill, the mouse cursor will turn into a skull, click on the the thing that u'd like to kill wether its a window that's not responding or an icon or whatever. best of luck

---

### Post by Breakablec on 2008-07-30
The process is not something that has X window or any other visible part.

---

### Post by p_alexander on 2008-08-06
Launchpad bug indicated above was marked as dupe of this one:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213053]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213053")

Also can confirm that Totem is also not the only program affected and it is likely related to a kernel bug. My problem occurred with Pidgin as the unkillable app.

---

