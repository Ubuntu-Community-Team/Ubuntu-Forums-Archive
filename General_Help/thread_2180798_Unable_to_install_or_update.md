---
title: "Unable to install or update"
date: 2013-10-14
forum: General Help
---

### Post by Tristan_Williams on 2013-10-14
I realize there are duplicates of this question, and here they are, hopefully they can help solve the problem:
[http://ubuntuforums.org/showthread.php?t=2179758](http://ubuntuforums.org/showthread.php?t=2179758)
[http://ubuntuforums.org/showthread.php?t=2180109](http://ubuntuforums.org/showthread.php?t=2180109)

It has been almost a month since i have been able to install or update anything.

Things are starting to seriously break. Some examples:
- Firefox and chromium, when trying to go to any website, simply download a file. upon opening the file, it just re-downloads itself. (I fixed the problem in firefox by changing proxy setting to "no proxy")

- Ubuntu Software center, synaptic package manager, aptitude, apt-get, and .deb files (yes all of them) are unable to install, update, or even locate any package or software, no matter which mirror, server, or source i choose, add, activate, etc... PPA's simply cant be added. Existing sources refuse to work.

- Firefox, Chromium, Ardour, Hydrogen, QjackCtl, and almost all system and settings related tools are slowly starting to break. Firefox is taking more and more CPU usage every day.


As you can see from the links above, I have tried many solutions, none of which worked. I have completely re-written my sources.list file (yes its written correctly, no errors)
This is becoming a massively huge burden on everything
My brother and sisters homeschool depends partly on this computer, and so does my income.

PLEASE PLEASE PLEASE help. I will provide any further info that anyone needs, and private messages to me are welcome if you want to help fix this.

Thanks in advance

---

### Post by 4dummies on 2013-10-14
Wow, that sounds serious.

Truly, I would not even want to try fixing such a mess.  Instead, I'd do a fresh install.  Now you probably have a bunch of configuration things you want to preserve, and there are ways to do that.  But even diagnosing what by now are likely multiple problems is going to keep you from having a running system, probably for a long time.

So: preserve the output of 
  dkpg --get-selections
so that you can get all of your packages back.

If you can, make a list of anything you installed by hand (not from the repositories).  I have about a dozen, like CALibre, Opera and a few others.  Dump or inventory everything in /usr/local and /opt.

Make copes (thumb drive, or some such) of all of /etc and /root.
Dump your entire home directory.

If you have a regular backup procedure, do that too.  It will duplicate the stuff I mentioned above, but they will be more convenient to access.

Now, if you can, prepare a new partition to hold the new system.  If you can't, you're going to have to overwrite the existing partition.  

Install the SAME version of the OS that you had before. This ensures that any configuration files you restore will at least be in the correct format.

Take that dump of selections and run it into (as stdin)
  dpkg --set-selections
then
  apt-get dselect -upgrade

And start restoring the other things you dumped.

Good luck.

---

### Post by Tristan_Williams on 2013-10-14
How would I  inventory everything in /usr/local and /opt?

how would I copy /etc and /root?

And how will i re-implement these into the newly installed OS?

---

### Post by ian-weisser on 2013-10-14
You already know you have a proxy issue. That seems pretty clear.
Since you don't recall how or when you created the proxy, and there are *many* possibilities, I'm just waiting for you to remember more information.

---

### Post by YannosB on 2013-10-14
Don't know if this can help, but may lead you to a more direct answer> I began experiencing very similar problems... I found I was getting 'dependancies' errors in gdebi installer and it told me to do an suido apt-get install ..??? (sorry I did not copy the command and archive it as I usally do, just went Term and executed.)
 Anyway the command apparently went through all my installs and did something that 'hooked' bad dependencies.. then it dl'd and replaced them and I've been good since.

 So, all this to offer a 'half-moon' shot... ask if any of the more seasoned users know the suido command for apt-get to fix broken dependencies.. your problem sounds so very much like what I was going through... I hope this at least leads you closer... and could save you a total reinstall...

---

### Post by Tristan_Williams on 2013-10-14
At this point I am done trying to fix the issue. I will simply document my settings, preferences, and applications. After I do that I will just reinstall Ubuntu Studio, reinstall all my applications, and put settings back where they belong... Any suggestions of new things i should try?

---

### Post by Tristan_Williams on 2013-10-14
Thank you for the suggestion YannosB That did in fact fix some of the problem.

However, like 4dummies said, there are many many things in this system that have been broken, that recovery of the system is almost impossible (keyword ALMOST)

>  I hope this at least leads you closer... and could save you a total reinstall...
I sincerely appreciate your effort to help, but the system is beyond recovery, and a total reinstall in inevitable.

---

### Post by Bucky Ball on 2013-10-14
Pardon me for being a little off topic, but ... if this machine is so important for so many things, why are you not running an LTS release? Interim releases are supported for nine months now and 13.04 will be dead soon anyway. 12.04 LTS is supported until April 2017 and LTS releases are advised for production/work/server machines, or anything that needs to be stable and reliable for a long period. 

Stick with the interims and you are going to be reinstalling/upgrading every nine months and dealing with whatever problems this throws up. Not great if you are needing this machine for home schooling and your livelihood. I personally wouldn't go there. 

I generally have the LTS as my main squeeze (ESSENTIAL I have a reliable install) and have three spare partitions for any other playthings. Doesn't matter if they break. Just fallback to the LTS and business as usual. 

Good luck. ;)

---

### Post by YannosB on 2013-10-14
sudo apt-get install -f
 try it first, as it could do it with very little pain... :P

 Thanks to Bashing-om for finding the command -f for fix.

---

### Post by YannosB on 2013-10-15
well.. unfortunately that's life in the digital realm.. hope it goes better from here....

---

### Post by YannosB on 2013-10-15
sage advice as always Bucky Ball.....

---

### Post by Tristan_Williams on 2013-10-15
Welp... Hard drive's formatted, Ubuntu Studio Reinstalled, and somehow getting all my settings back the way they were was somewhat painless... Thanks for all your help everyone!

---

### Post by Bucky Ball on 2013-10-15
Good news! Please mark thread as solved from thread tools (top right) to help others, and post a new thread for any further issues/problems/questions. ;)

---

