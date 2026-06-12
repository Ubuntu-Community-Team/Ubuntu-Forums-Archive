---
title: "Clean unwanted files"
date: 2015-05-25
forum: General Help
---

### Post by RobGoss on 2015-05-25
Hello everyone, I have a simple question that someone might be able to answer for me. I was wondering if there was a program for Linux that would help me keep my system clean from unwanted files that's being stored on my system. I was trying Bleachbit but I'm not sure if I'm using it correctly and is it doing it's job.

If you could recommend something that will work as far as cleaning one's computer please advise. Thanks so much

---

### Post by ian-weisser on 2015-05-25
What, exactly, do you mean by 'unwanted files'?

This forum is littered with many happy users of bleachbit...and many unhappy users of bleachbit.
This forum is also littered with stories of "Hey, I deleted this file I didn't think important, and now my system is broken." But that happens on all OSs.

I find the 'cruft' less than it used to be, now that users have defined locations in /home/USER/.cache and /home/user/.config

---

### Post by RobGoss on 2015-05-25
So would you say there's no need for programs like this? I just want to keep my system cleans ans running good. At the same time I don't want to delete anything I should not. Thanks so much

---

### Post by v3.xx on 2015-05-25
People say things like bleachbit are not necessary and probably not, but I like and use BB.  Linux systems do not really need such tools, but I find them helpful.  

[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by RobGoss on 2015-05-25
> **v3.xx said:**
> People say things like bleachbit are not necessary and probably not, but I like and use BB.  Linux systems do not really need such tools, but I find them helpful.  

[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

What is BB?

---

### Post by slickymaster on 2015-05-25
> **ian-weisser said:**
> What, exactly, do you mean by 'unwanted files'?

This forum is littered with many happy users of bleachbit...and many unhappy users of bleachbit.
This forum is also littered with stories of "Hey, I deleted this file I didn't think important, and now my system is broken." But that happens on all OSs.

I find the 'cruft' less than it used to be, now that users have defined locations in /home/USER/.cache and /home/user/.config
This ^^^

---

### Post by slickymaster on 2015-05-25
> **robert159 said:**
> What is BB?
[BleachBit]("http://bleachbit.sourceforge.net/")

---

### Post by RobGoss on 2015-05-25
> **slickymaster said:**
> This ^^^


I was wonder what This ment :)

---

### Post by RobGoss on 2015-05-25
> **slickymaster said:**
> [BleachBit]("http://bleachbit.sourceforge.net/")


Thank you, I'm a bit confused because people say you don't really need programs like this because you're using Linux, but I say if it's a OS or Operation system, you need something to help keep things clean wouldn't  you?

---

### Post by slickymaster on 2015-05-25
> **robert159 said:**
> Thank you, I'm a bit confused because people say you don't really need programs like this because you're using Linux, but I say if it's a OS or Operation system, you need something to help keep things clean wouldn't  you?
apt does that for you. Just have a read at its man page```
man apt-get
```
```
 clean
           clean clears out the local repository of retrieved package files. It removes everything but the lock file from /var/cache/apt/archives/ and
           /var/cache/apt/archives/partial/.

       autoclean
           Like clean, autoclean clears out the local repository of retrieved package files. The difference is that it only removes package files that can no longer be
           downloaded, and are largely useless. This allows a cache to be maintained over a long period without it growing out of control. The configuration option
           APT::Clean-Installed will prevent installed packages from being erased if it is set to off.

       autoremove
           autoremove is used to remove packages that were automatically installed to satisfy dependencies for other packages and are now no longer needed.


```

---

### Post by Bashing-om on 2015-05-25
robert159; Whelllll ..

> 
but I say if it's a OS or Operation system, you need something to help keep things clean wouldn't you?


Umphhh ... I have been running some form of 'buntu since release 9.04 ( 6.04 was my introduction)  and I have never had the need to resort to other than the "normal" house cleaning tools that apt-get provides.
I do clean out old kernels and on occasion I run:
```

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

```
Then for an integrity check, and only for my peace of mind, I run:
```

df -h
df -i
sudo apt-get -f install
sudo dpkg -C

```

Keep in mind that ubuntu is a journaled file system and as such does not accumulate a lot of cruft .

Suffices for my needs, and pay attention to what the package manager tells me.

[INDENT][INDENT]works for me [/INDENT][/INDENT]

---

### Post by RobGoss on 2015-05-26
Thanks so much for the tips, being a Windows user for so long I guess it's a habit all I ever did was try to keep my Windows machine clean and virus free. Linux runs so smooth I just want everything to stay this way I never enjoyed my machine so much until I started using Linux Ubuntu. I will use your tips in my dayley task GREAT job and thank you.

---

### Post by travelzfactory on 2015-05-26
the healpful tool is
[COLOR=#000000][INDENT]
[http://www.ubuntugeek.com/cleaning-u...in-ubuntu.html]("http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html")

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)[/INDENT]
[/COLOR]

---

### Post by Keith_Helms on 2015-05-26
> **robert159 said:**
> Thanks so much for the tips, being a Windows user for so long I guess it's a habit all I ever did was try to keep my Windows machine clean and virus free. Linux runs so smooth I just want everything to stay this way I never enjoyed my machine so much until I started using Linux Ubuntu. I will use your tips in my dayley task GREAT job and thank you.

Fortunately, Linux does not have a registry and you don't have to reinstall it every couple/few years to keep it from grinding to a halt due to all the crud that has accumulated.

---

