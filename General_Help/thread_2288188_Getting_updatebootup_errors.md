---
title: "Getting update/bootup errors"
date: 2015-07-25
forum: General Help
---

### Post by fall2 on 2015-07-25
Lubuntu 14.04


The last update that was a base update I received an error and could not install the whole update. I sent a report.

 When I just turned on my laptop first white then yellow writing popped up I read error in the yellow writing but I did not have time to read more. This is not the first time I booted up my pc since the last update but the first time I noticed a error.

This is concerning because I still have web browser problems starting in early July.
"http://ubuntuforums.org/showthread.php?t=2286960"


I was thinking of trying Xubuntu anyways or another ubuntu based OS but I don't know if it would correct the errors.

I'll do what ever, I just want a easy fix.


1; can and how do I look at the bootup error to report the bootup error?

2; if I install Ubuntu, Xubuntu or another OS will it fix it? easy fix??

3; directions.

---

### Post by fall2 on 2015-07-25
Maybe there are some general maintenance commands I could put in a term?

---

### Post by Bashing-om on 2015-07-25
fall2; Welp;

With out seeing the exact error reported, will be impossible to be explicit in the advise.
However, we can generalize as the error is presented at boot time, there is a file system error.
If you can get to terminal, one can run a rudimentary file system check.
```

sudo touch /forcefsck
sudo shutdown -r now

```
Which will set the file system check flag for the next boot, and "shutdown -r" will make that happen.

[INDENT][INDENT]maybe, all this takes to resolve, maybe we get indications we need to go deeper.
[/INDENT][/INDENT]

---

### Post by fall2 on 2015-07-26
Bashing-om
scan went smooth.

I also cannot shutdown my pc from the menu or by a terminal. That might of had something to do with it. I don't know I guess its better.

---

### Post by Bashing-om on 2015-07-26
fall2; Well ...

In small steps, startup difficulties as the 1st priority. Do you now boot with no errors reported ?

[INDENT][INDENT]sometimes we wonder
[INDENT][INDENT][INDENT]then again sometimes
[INDENT][INDENT][INDENT][INDENT]it's a wonder to behold
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by fall2 on 2015-07-26
Yes bashing-om, at least with no errors the last few times booting up.

---

### Post by Bashing-om on 2015-07-26
fall2; Great !

May we conclude that this situation is under control ?
If so;
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

If another situation, open a new thread and we will address the new issue.

[INDENT][INDENT]look'n good
[/INDENT][/INDENT]

---

### Post by fall2 on 2015-07-26
Ran "sudo apt-get autoremove" and the files "libglade2-0" and "python-glade2" showed up and I removed them. This may not have anything to do with, well anything. Just thought I would tell you.

Just going to edit this post a bit and add, my lubuntu os was 1 or 2 seconds faster loading after this. "bonus"

---

### Post by Bashing-om on 2015-07-27
fall2; All good ;

I can believe that the two files removed were obsolete, and no longer required.

If ya do :
```

apt show libglade2-0
dpkg -l libglade2-0
apt show python-glade2
dpkg -l python-glade2

```
I expect you will find the versions now match as to what is available in the repository as to what is actually installed on the system.

[INDENT][INDENT]pretty smart system
[/INDENT][/INDENT]

---

