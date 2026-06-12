---
title: "how to prepare /home for clean reinstall?"
date: 2008-07-05
forum: General Help
---

### Post by ChrisC on 2008-07-05
I've been using Ubuntu for several years now.  I started dabbling in 2005 with 4.10/warty and 5.04/hoary, and then went for broke with the 5.10/breezy release, migrating all of my activity over to it (from Windows 95!).  In June 2006 I did a dist-upgrade to the 6.06/dapper LTS release.

I'm ready now to take the plunge with 8.04 LTS, however this time I'm going to do a fresh install, not a dist-upgrade, so that I start with a clean OS installation with a pure 8.04 config setup.  That said, I'm going to keep the data in the /home directory intact -- when doing the installs 2-3 years ago, I had the foresight to keep the /home partition separate.

There are a few apps that I would like to keep the configs on, mostly critically Thunderbird, but also a few minor apps (gtkpod, putty) that have a bit of config history in them that I'd like to retain.  Doing the 8.04/LTS install alongside the existing home partition should do that trick.

However, I do *NOT* want 8.04/hardy to get confused by any other old configs in my /home partition.  For example, I see that there are .gconf, .gnome and .gnome2 directories in my /home/username directory.  20+ years of computing experience has taught me that installs go much worse if they are trying to migrate an old config.  I will happily do a vanilla install, see what I get, and re-tweak from there.

So I would need to DELETE those config directories before doing the install.  I can probably figure out how to actually do that (drop out of gnome/X to a command line, I guess), but I really need the help of you all to determine WHAT to delete to ensure that I've scrubbed my system clean of any offending configs.  All I plan to keep are a few application configs as described above.

Any suggestions of directories to delete just prior to the 8.04 install?  Here are some that I'm wondering about:
~/.config
~/.gconf
~/.gconfd
~/.gnome
~/.gnome2
~/.gnome2-private
~/.nautilus

Any others?  How about /etc things to delete?

---

### Post by linfidel on 2008-07-05
I think you mainly know what to keep or delete - if you don't care about your settings for the basic utils, delete the directories.  If you have any bash settings you like, you could rename .bashrc and retrieve them later - that's easy to merge in.  I'd keep .bash_history - nothing there to interfere.

Aside from /home, you will need to reformat the root filesystem, if I remember correctly, so nothing else matters if they are all in the same partition.

---

### Post by mikewhatever on 2008-07-05
I can only imagine what your home looks like, but it's probably a terrible mess. Is there no profile exporting function at least in Thunderbird? What about simply backing up and then copying back what's needed? I've done that with .aMule to keep the profile a couple of times.
/etc in in root which would need to be formatted anyway.

---

### Post by cariboo on 2008-07-05
I usually get rid of all the **.** files and directories accept for firefox and thunderbird, the rest I don't really care about as they are recreated in a fresh install.

---

### Post by ChrisC on 2008-07-07
Thanks guys for the replies!

I realized after I posted that of course /etc would get wiped out ... fine with me :)

OK, so if I'm going to get rid of a bunch of directories like this, just prior to reinstall, how exactly to do that?  Of the top of my head, I guess I would do this:
 - logout of my account (which is set to auto login when I boot)
 - Ctrl-Backspace to drop out of X
 - log in as root
 - Ctrl-Backspace to drop out of X (again, if needed)
 - sudo the deletes

Or can someone suggest a better way?  An init level?

---

### Post by cariboo on 2008-07-07
You can delete the files using nautilus or you favorite file manager. Personally I use mc.

Jim

---

### Post by linfidel on 2008-07-07
> **ChrisC said:**
> Thanks guys for the replies!

I realized after I posted that of course /etc would get wiped out ... fine with me :)

OK, so if I'm going to get rid of a bunch of directories like this, just prior to reinstall, how exactly to do that?  Of the top of my head, I guess I would do this:
 - logout of my account (which is set to auto login when I boot)
 - Ctrl-Backspace to drop out of X
 - log in as root
 - Ctrl-Backspace to drop out of X (again, if needed)
 - sudo the deletes

Or can someone suggest a better way?  An init level?You can delete them as yourself; but to make sure they don't get recreated, don't run or configure anything afterward.  I'd close all the programs that are running, and if you're using Compiz, perhaps run a failsafe gnome login first.  But I don't think you need to jump through all those hoops you mentioned, since they're your files.  But it wouldn't hurt if you logged out from X, then used one of the TTY terminals to do it, if you're comfortable with that.

---

### Post by ChrisC on 2008-07-07
The reason I want to back out of Gnome/X to do the deletes is because I want to delete the .gnome* directories, among others.

Thanks again for the advice!

---

### Post by Seb71 on 2008-07-08
I used a Live CD to delete the directories from /home that I did not want to keep.

---

### Post by AndyCooll on 2008-07-08
> **Seb71 said:**
> I used a Live CD to delete the directories from /home that I did not want to keep.
Or if you don't mind using the command line, after booting up the pc, instead of logging in the usual way you could switch to a terminal session (e.g. CTRL+ALT+F2) and delete the folders you want from there.

:cool:

---

### Post by ChrisC on 2008-07-12
Thanks again.  I did a test run earlier this week, and the sequence that works is:

sudo /etc/init.d/gdm stop

That drops me to a command prompt, still logged in as myself.  Or maybe logged out, I forget, but I can easily then log in and it will stay in CLI mode.  If I want to get back into graphical mode, then

sudo /etc/init.d/gdm start

---

### Post by boblemur on 2008-07-12
im on expert, but id suggest that you take a backup of your entire home ( if you have the space...

then format it and paste back the config files that you DO NEED rather than trying to prune out the ones you dont think you should keep...

id say its always nicer to start fresh... and then restore rather than have it all still their...

especialy because you sound like their are only a few applications that you need to keep the settings for... so i think you should wipe it all clean and then reinstall your program and as you go along and find that you want ur old settings for that app back.. copy the .<app> file back... 

that way you get as much new settings for your applications as you can get, and only keep the ones that you NEED...

so thats my advice but as i said i am no expert

---

### Post by linfidel on 2008-07-12
> **ChrisC said:**
> Thanks again.  I did a test run earlier this week, and the sequence that works is:

sudo /etc/init.d/gdm stop

That drops me to a command prompt, still logged in as myself.  Or maybe logged out, I forget, but I can easily then log in and it will stay in CLI mode.  If I want to get back into graphical mode, then

sudo /etc/init.d/gdm start
I still don't get it - did you ever try to just delete (or rename) the .gnome directories, or whatever you wanted to delete?  It's usually best to try the simple approach first.

I was able to use Nautilus without sudo to rename or delete all the .gnome* directories, so why did you have to jump through hoops?

It seems to me you had answers that you ignored because you were intent on doing something else.  It sounds like you asked how to delete the files, but what you really wanted to know was how to jump through the hoops to do it the hard way.  Perhaps you forgot it was linux, and thought you were still in Windows?  In Windows, I'm sure it would be hard to do.  But with Linux, many people have a separate /home directory (like me), and so can install a new root system, or upgrade, or reinstall, without needing to reset all the preferences.  I have lots of settings for shell scripts, aliases, and other configurations that I don't like to redo. I find it usually works fine. 

You don't need to pay for support, you just need to ask the right questions.  :-)

---

