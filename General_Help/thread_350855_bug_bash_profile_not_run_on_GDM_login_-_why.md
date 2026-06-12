---
title: "bug: bash_profile not run on GDM login - why???"
date: 2007-02-01
forum: General Help
---

### Post by johann_p on 2007-02-01
It seems that my .bash_profile script is not being executed when I login with GDM. When I login in a graphical terminal, via ssh, or from a console window with "su -l username" it works just fine.
My user has bash defined as loging shell.

I would expect a *LOGIN* manager like gdm to start a login shell and hence run .bash_profile.

So is this a known bug?

---

### Post by dmwit on 2007-02-01
> **johann_p said:**
> I would expect a *LOGIN* manager like gdm to start a login shell and hence run .bash_profile.

I'm pretty sure it doesn't work like that... ;-)
You may have more luck with .profile instead, though I can't remember off the top of my head whether Gnome uses that one.  But even better, try System -> Preferences -> Sessions or so.  There should be a tab that allows you to list startup programs to run.

~d

---

### Post by johann_p on 2007-02-01
> **dmwit said:**
> I'm pretty sure it doesn't work like that... ;-)
What do you mean doesn't work like this?

.bash_profile MUST be read in from a login shell unless it is invoked with --noprofile, according to "man bash":
> 
       When  bash is invoked as an interactive login shell, or as a non-inter&#8208;
       active shell with the --login option, it first reads and executes  com&#8208;
       mands  from  the file /etc/profile, if that file exists.  After reading
       that file, it looks for ~/.bash_profile, ~/.bash_login, and ~/.profile,
       in  that order, and reads and executes commands from the first one that
       exists and is readable. 
Since GDM does, well, log in, and since it is interactive, I would expect it to run bash as  an interactive login shell according to Linux standards.

*That* is exactly what .bash_profile is for.
Why does GNOME or Ubuntu break that?

If every login manager or Linux distro has their own way of how to set login stuff what we get is a terrible -- and unnecessary -- mess.

So, is there any reason why this should not be considered a bug?

---

### Post by ngch on 2007-02-02
GDM is not considered a login shell, hence it probably does not execute .bash_profile by default. This explains why your alteration to .bash_profile works when you login from a console window. This is probably by design.

The explanation can be found in this page:
[http://gnomesupport.org/forums/viewtopic.php?t=11559]("http://gnomesupport.org/forums/viewtopic.php?t=11559")

Addition info can be found here:
[http://ubuntuforums.org/archive/index.php/t-28664.html]("http://ubuntuforums.org/archive/index.php/t-28664.html")

---

### Post by johann_p on 2007-02-03
Well since GDM lets me *LOG IN* it definitely should be considered a login shell. I do not know why the GNOME people insist in messing up such things for not good reason and I really cannot see  how messing this up makes anything easier for anyone (thats the myth GNOME people tend to spread about GNOME).

Ah well ... I did some hacking to make this work no matter how I log in.

---

### Post by dagnabit dang doohickey on 2007-02-03
I recently noticed this behavior a couple of days ago when trying to modify my PATH for some shell script a few days ago.

startx -> login shell
gdm -> not-login shell

The quick solution is to go to your X terminal's preferences and check the setting that reads something similar to "Run command as login shell." BTW, this setting has no effect if you use startx.

---

### Post by DragonTU84 on 2007-02-03
I completely agree with johann_p's point.

I am supposed to remember that .bash_profile is the source for startup needs EXCEPT in GNOME???

How many other "features" will I have to remember?

---

### Post by 3rd Rook on 2007-06-19
Wow!  I can't believe this either!

I solved this on my machine (after several hours of reading rant posts) by adding the following line  to the end of my** /etc/profile** (as root).

```
. ~/.bash_profile
```

Now, whatever I have in my .bash_profile will get run each time I login.

I still can't believe that I had to do it though!

</RANT>

---

### Post by Mr. C. on 2007-06-19
GDM is a graphical equivalent to getty; neither are shells.  They are shell-launching facilities which essentially monitor the "terminal" for a login.

The concept of "login shell" unfortunately was rendered confusing once X Window and Sun Windows sessions become popular.  User's with multiple terminals were seen as being logged-in dozens of times, which really makes very little sense.  In addition, the mechanisms actually used to start various graphical sessions further complicate the matter.

The login, interactive, and non-interactive shell issue has always been a source of confusion, and depending upon how you are accustomed to connecting to the systems, one mechanism may work in one case, but not another.

Unix/Linux is full of such inconsistencies - just learn to navigate around them, or prepare for life-long frustrations.

MrC

---

