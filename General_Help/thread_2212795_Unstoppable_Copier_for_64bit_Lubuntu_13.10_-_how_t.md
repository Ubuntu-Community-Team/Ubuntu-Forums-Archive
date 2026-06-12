---
title: "Unstoppable Copier for 64bit Lubuntu 13.10 - how to install and use?"
date: 2014-03-23
forum: General Help
---

### Post by West Swan on 2014-03-23
Hello,

I am trying to install Unstoppable Copier on Lubuntu 13.10 which is 64bit.

I download from here [www.roadkil.net/program.php?ProgramID=29&Action=NewOSID&DownloadVersion=11&Installer=NO](www.roadkil.net/program.php?ProgramID=29&Action=NewOSID&DownloadVersion=11&Installer=NO)

It comes as a .gz format which I then extract to get to the unstopcp install file

I then use the following instructions which were in another post on this forum:



To run Unstoppable Copier in linux:

1. download and install library:
**sudo apt-get install libqt3-mt**

2. copy unstopcp to /usr/bin/
**sudo cp unstopcp /usr/bin/**

3. run it independently from terminal
**unstopcp&**

or making a shortcut from Edit Menus is prolly better to use to run the program.


I do all this (I think - it is a bit confusing) and I right click and choose to allow executions but nothing happens.  No error message or anything.  I'm confused :-)

If I had a 32bit version of Lubuntu all I would have to do is double click on the file and it would work.  I just tested this now using a 32bit  live parted magic cd and it opened immediately.



Otherwise is there a good alternative to unstoppable copier that also ignores corrupt files, file permissions etc?  This is the best part of unstoppable copier.  It just keeps copying whatever it can without me having to choose to skip skip skip skip all  etc.

Regards,

Paul

---

### Post by ajgreeny on 2014-03-23
I don't think you will get that to run in a 64 bit system as it is only 32 bit program, unless you know differently and it is meant to be multiarch.

However
> 3. run it independently from terminal
[B]unstopcp&

[/B]I suspect a typo here; it should be** unstopcp &**

---

### Post by West Swan on 2014-03-23
Hello,

They do have a 64bit version but for the life of me I couldn't get it to work so I installed Wine and used the Windows version.

It seems to work perfectly :-)

Regards,

Paul

---

### Post by syntaxerror74 on 2014-12-14
> **West Swan said:**
> 
If I had a 32bit version of Lubuntu all I would have to do is double click on the file and it would work.  I just tested this now using a 32bit  live parted magic cd and it opened immediately.

Huh? 
Lubuntu **Utopic 32-bit** running here, and now look at this:
```

unstopcp: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory
```

The reason why it works for you is not the "32-bit"; it is in fact because your live CD is still based on QT3 (entirely unlike v4 or even v5 installed here in recent distros).

And...hmmm...QT3...that was *indeed* a few moons ago.
Speaking of "long time ago"...

[http://ubuntuforums.org/showthread.php?t=1543768](http://ubuntuforums.org/showthread.php?t=1543768)

The above (now closed) thread is **4 years old**, and people where even *then* already stuck with this stuff.
Maybe this is a task for yours truly to go ahead and convince the developer to finally issue a version that can run under QT4 without any of those quirks?
Because...hey...what I am supposed to still use QT3 for here except due to requirements of this tool?
Plus, hadn't this one better be recompiled with **static** libraries used, instead of shared ones? 
Damn, I hate this binary-only stuff...and this is another good evidence WHY.

I can try around with some symlinking tricks...but as QT3 is so doggone different from QT4 (and higher), I think this is going to turn into an epic fail in the end...

---

