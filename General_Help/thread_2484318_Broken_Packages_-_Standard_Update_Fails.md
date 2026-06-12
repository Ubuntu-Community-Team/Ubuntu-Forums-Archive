---
title: "Broken Packages - Standard Update Fails"
date: 2023-02-22
forum: General Help
---

### Post by Geoffrey_Arndt on 2023-02-22
I could use some help to fix my broken package manager (running Ubuntu 22.04.2)


I've tried inactivating 3rd party sources and rerunning the update - no luck.


It's been YEARS since I've had any issues with package management and I've forgotten some of the skills I've used in the past.


Here's the error feedback


Correcting dependencies... failed.
The following packages have unmet dependencies:
 libgl1-mesa-dri : Depends: libglapi-mesa (= 22.2.0-1pop0~1664294850~22.04~4e1b64f~dev) but 22.3.4-1pop1~1675300365~22.04~6b66c01~dev is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
greg1@Galago-UltraPro2u:~$ 


But, from some old notes I had, I also tried the following sequence of CLI commands - also with no luck . . . 


> sudo apt clean
> sudo apt update
> sudo dpkg --configure -a
> sudo apt install -f
> sudo apt full-upgrade
> sudo apt autoremove --purge


Any help is appreciated - - this System 76 Galago (with basic Intel graphics) has been a workhorse for about a decade - - really hope it can be fixed.


G.Geoffrey Arndt
Omaha, NE

---

### Post by Bashing-om on 2023-02-22
Geoffrey_Arndt; Hummmm ...

As we have in 22.04
> 
sysop@x2204mini:~$ apt list libglapi-mesa
Listing... Done
libglapi-mesa/jammy-updates,now 22.2.5-0ubuntu0.1~22.04.1 amd64 [installed]


that ^  begs the question where "22.2.0-1pop0~1664294850~22.04~4e1b64f~dev" derives from.

Post back the return from terminal command:
```

apt policy libgl1-mesa-dri libglapi-mesa

```

And we see what there is to work toward.

[INDENT]there is a process
[/INDENT]

---

### Post by Geoffrey_Arndt on 2023-02-22
OK -thanks - - here is the output:

(note:   I don't recall installing anything outside of the standard Ubuntu prompted system updates.  I did note the last such install was larger than normal, but I never pay much attention anymore and just let the system "do it's thing" . . )

greg1@Galago-UltraPro2u:~$ apt policy libgl1-mesa-dri libglapi-mesa
libgl1-mesa-dri:
  Installed: 22.2.0-1pop0~1664294850~22.04~4e1b64f~dev
  Candidate: 22.2.5-0ubuntu0.1~22.04.1
  Version table:
     22.2.5-0ubuntu0.1~22.04.1 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 Packages
 *** 22.2.0-1pop0~1664294850~22.04~4e1b64f~dev 100
        100 /var/lib/dpkg/status
     22.0.1-1ubuntu2 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main amd64 Packages
libglapi-mesa:
  Installed: 22.3.4-1pop1~1675300365~22.04~6b66c01~dev
  Candidate: 22.3.4-1pop1~1675300365~22.04~6b66c01~dev
  Version table:
 *** 22.3.4-1pop1~1675300365~22.04~6b66c01~dev 100
        100 /var/lib/dpkg/status
     22.2.5-0ubuntu0.1~22.04.1 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 Packages
     22.0.1-1ubuntu2 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main amd64 Packages
greg1@Galago-UltraPro2u:~$ ^C
greg1@Galago-UltraPro2u:~$

---

### Post by Bashing-om on 2023-02-22
Geoffrey_Arndt; Well well well ....

Not what I had anticipated to see - however

Let's try
```

sudo apt --purge autoremove libgl1-mesa-dri
sudo apt install libgl1-mesa-dri

```
see if that does not bring in the current version: 22.2.5-0ubuntu0.1~22.04.1

else tell us what we do need now to do.

[INDENT]where there's a will there's a way[/INDENT]

---

### Post by Geoffrey_Arndt on 2023-02-22
OK . . . . good news!   I ran the commands from your latest post and that didn't resolve the issue (still had same error message) - - but apt suggested another purge command which I ran, and then I ran the 6 lines of CLI code in my original message.   There were plenty of updates that ran, and the updates finished successfully.   Now Synaptic package manager runs normal and also shows no broken packages.

So - - you set me on the right road, I just had to go down that road a bit further.    Thanks very much for your help, I truly appreciate it. 



Greg Geoffrey Arndt
Omaha, NE.

---

### Post by Bashing-om on 2023-02-22
Geoffrey_Arndt; Great

Glad I could help :D

As this situation is now conluded
 Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean, and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

-up up and away :D -

---

