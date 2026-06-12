---
title: "High RAM use in 16.04 on 64-bit System"
date: 2016-12-05
forum: General Help
---

### Post by BlueAZ on 2016-12-05
Hi,   I'm noticing much higher RAM use in 16.04 on my 64-bit AMD system.  I've used LTS versions of Ubuntu for over 5 years now and never had this problem before.  I have a system load indicator, so I can see it graphically all the time.  It seems to just keep increasing and doesn't go down again.  This results in program screens graying out when I start them or ask them to do anything.  I can't have more than one program open at a time, or things really freeze up or crash.
I've searched and found this on Launchpad:  [h=1][SIZE=3]Ubuntu 16.04 Unity desktop uses much more ram Bug #1572801[/SIZE][/h]Many others having this problem, but no real solution yet.  Like others, I have checked System Monitor and found many derivations of 'Evolution' running and eating up large chunks of RAM.  I looked it up and realized I could get rid of it, as I don't use it.  But when I used Synaptic to find Evolution listings, mark them all for removal, and click 'Apply', it told me that 90 new things would be downloaded & installed along with the 8 or 10 Evolution things being removed.  I couldn't find a way to not acquire all this new stuff I didn't understand, so I canceled it.
At this point, it would be nice if someone qualified & knowledgeable could take a look at this...  Please?

---

### Post by karl96 on 2016-12-05
Strange, i've heard of metapackages threatening to remove large amounts of packages but not the other way around. Possibly you have a broken system in terms of packaging (when did you last update?) which is why it requires all of this new stuff.

It actually isn't that important if it does pull it in, as long as the services are disabled they'll just consume disk space instead of ram.

to check for broken dependencies
Run ```
 apt-get check 
``` or ```
 apt-get -f remove evolution 
```. I use ```
 apt-get install --no-install-recommends 
``` to prevent installing recommended packages but not entirely sure on packages being pulled in on removal.

Do you have swap space? You could simply extend your swap partition to bypass the issue.

---

### Post by BlueAZ on 2016-12-05
Thanks!  Here's what I get when I run that first code: ```
 -A:~$ apt-get check
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```
When I've tried to remove Evolution in the Terminal, it just tells me that no such package is installed (?!!?)  But I am able to Kill the Evolution processes within the System Monitor.
Still using to much RAM.  Can I kill the process Compiz?
Thanks again,   Blue

---

### Post by karl96 on 2016-12-05
Run ```
whereis evolution
```

There must be a binary on the system somewhere, manually deleting it will prevent it from launching.

Edit:
Compiz is a window manager, if you're using Compiz as your main window manager killing it is a bad idea, but if not yes, it is quite a demanding window manager and unnecessary to many.

Edit 2:
Manually deleting binaries should only be done when the packages are broken.

---

### Post by BlueAZ on 2016-12-05
Thank you Karl96.  I ran the whereis evolution command and was directed to /usr/lib/evolution.  I went there and found 2 folders, one just named Evolution and another named EvolutionData...  But I could not remove them.  (Move to Trash was grayed out, couldn't use Shift-Delete, even on the individual files within.)  So I don't know how to manually delete them.
Does this have to do with the earlier code response about /var/lib/dpkg/lock - open ?  And the Terminal asking me if I was root?  I'm the sole owner and user of this computer.  Do I have to become root to root out Evolution?!
Also, if Compiz is so demanding, is there another window manager I could use instead?  I don't do any complex gaming or 3D stuff.
Again,  Many thanks,   Blue

---

### Post by cariboo on 2016-12-05
What do you consider high ram usage? Running:

```
free -m
```

in a terminal I get the following result:

```
free -m
              total        used        free      shared  buff/cache   available
Mem:          15942        2572         803          76       12566       12959
Swap:          1999           8        1991
```

As you can see my system is using 2573MiB running Chromium, Thunderbird, [Serviio]("http://serviio.org/") and an open terminal. I still have over 12GiB buffered/available.

---

### Post by BlueAZ on 2016-12-06
Thanks cariboo,   This a.m. I was notified of an update to 4.40-53 and did it.  At the time, my system was showing a RAM use of 4 Gb + 2 Gb of swap with NO open programs.  I managed to get & install the update, had to try 2x to restart and now memory use is lower.  So maybe the problem was fixed in this new kernel update.  System is now using less than 2 Gb RAM and no swap, with Thunderbird and Firefox open.  This is a big improvement, and I hope it lasts!
I'll keep the forum posted.

---

### Post by karl96 on 2016-12-06
Hi, you'll need to be root to delete system wide files, /var/lib/dpkg/lock just means apt is already in use, could possibly be stuck or updating in the background. Evolution shouldn't be in /usr/lib though (the libraries should), the binaries should be in /usr/bin (I think?), it won't be able to run without the libraries either so it should work though.

---

### Post by BlueAZ on 2017-07-19
OK, this issue seemed to be resolved for several months, but is now back!  I keep 16.04 updated daily, and the high memory use started a few days ago.  Nothing else on my system has been changed, just regular updates.  This time, so much of my 4 Gb of RAM is getting used that screens gray out for half a minute before showing up normally.  These are programs and websites I frequently use, so I can tell the difference.  And a check of System Monitor shows that absolutely 0 Swap is in use while this is happening, a new wrinkle since last time.
I am still unable to make up my own Terminal entries beyond 'sudo apt-get update', so please keep it simple.
Thanks!

---

### Post by vocx on 2017-07-19
> **BlueAZ said:**
> OK, this issue seemed to be resolved for several months, but is now back!  I keep 16.04 updated daily, and the high memory use started a few days ago.  Nothing else on my system has been changed, just regular updates.  This time, so much of my 4 Gb of RAM is getting used that screens gray out for half a minute before showing up normally.  These are programs and websites I frequently use, so I can tell the difference.  And a check of System Monitor shows that absolutely 0 Swap is in use while this is happening, a new wrinkle since last time.
I am still unable to make up my own Terminal entries beyond 'sudo apt-get update', so please keep it simple.
Thanks!
I suggest you install "htop". It is a program, that like system monitor, shows what processes are under use, but in the terminal. You can sort the programs by CPU use or Memory, and also terminate (kill) programs. This is useful if you see a runaway program suddenly taking a lot of resources.
```

sudo apt install htop
htop

```

I think System Monitor shows only the processes run under your name, but "htop" shows also those by the "root" user, that is, the system itself. If a program by root is taking a lot of CPU processing power or RAM it may be a background process, and that is usually Xorg or Compiz, which deal with the graphics you see on the screen. You should check your graphics card, to see which drivers are installed. Maybe if you use restricted drivers, you will notice your system is more responsive, as the CPU doesn't need to work that hard to render your screen. Graphical programs, videos, flash applications, and things like that, may cause lockups because they are notorious memory consumers, and if your graphics card or your flash version, for example, are buggy, you may experience these problems. 

By the way, I just mention this, using a lot of RAM is not a problem itself. Linux uses a lot of RAM because it caches most of it for future use. Of course, if you really get the gray screen behavior, this is a problem. It is either running out of memory, or the CPU cores are maxed out (running each core at 100%, for example). You can use "htop" to verify this.

---

### Post by BlueAZ on 2017-07-19
Thanks VOCX!  I do have htop, just forgot to check it.  Now that I have, I found that ClamAV is using lots of memory, even though it's not open.  Is that normal?  There are two entries for ClamAV, each using 14% of my RAM, far more than anything else.  I tried to 'kill' it, but it wouldn't die...  That's scary!
Yes, I use a proprietary driver for my GPU and it works fine.  As I said, I was doing things I normally do, but with the abnormal memory suck.
So, do I really need ClamAV?  I find it hard to use anyway, as I can't get it to scan my whole system.  If I can do without it, how do I kill it?
Many Thanks!

---

### Post by vocx on 2017-07-19
> **BlueAZ said:**
> Hi,   I'm noticing much higher RAM use in 16.04 on my 64-bit AMD system.  I've used LTS versions of Ubuntu for over 5 years now and never had this problem before.
...


> **BlueAZ said:**
> Thanks!  Here's what I get when I run that first code: ```
 -A:~$ apt-get check
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```
When I've tried to remove Evolution in the Terminal, it just tells me that no such package is installed (?!!?)  But I am able to Kill the Evolution processes within the System Monitor.
Still using to much RAM.  Can I kill the process Compiz?
Thanks again,   Blue

You really have been using Ubuntu for 5 years, but you don't use the terminal much? I think you need to use the terminal a bit more, just to lose the fear of it. It will help you understand your system better, and it also simplifies the troubleshooting because it is easier to say, "type this", instead of talking about an interface, for example, "open that window, click here, then there and change the option". Using the terminal is more direct.

> **karl96 said:**
> Run ```
whereis evolution
```

There must be a binary on the system somewhere, manually deleting it will prevent it from launching.

Edit:
Compiz is a window manager, if you're using Compiz as your main window manager killing it is a bad idea, but if not yes, it is quite a demanding window manager and unnecessary to many.

Edit 2:
Manually deleting binaries should only be done when the packages are broken.
By the way, reading the posts of karl96, I have to say that he provided confusing information. He started suggesting deleting binaries, and the lock file, and what not. Just forget about that. Evolution is a program that integrates with your calendar on the top right of the screen, besides working as an email client, alarm, and things like that. It should definitely not consume a lot of memory if you are not using it, unless it has a bug. I don't use Evolution, but it is installed in my system, and I basically don't think about it. It consumes maybe 400 MB RAM total. It is a non-issue.

> **BlueAZ said:**
> ...
Also, if Compiz is so demanding, is there another window manager I could use instead?  I don't do any complex gaming or 3D stuff.
Again,  Many thanks,   Blue
You mention here you don't need 3D stuff, so maybe you don't need to be running Unity, and you would prefer a simpler, less resource intensive interface, like MATE. You could install that. Since I don't have the problems you experience I run Unity without issue, but maybe you should try other desktops, XFCE, LXQT, MATE, etc. I hear they are closer to Gnome 2, so they are more lightweight.

---

### Post by vocx on 2017-07-19
> **BlueAZ said:**
> Thanks VOCX!  I do have htop, just forgot to check it.  Now that I have, I found that ClamAV is using lots of memory, even though it's not open.  Is that normal?  There are two entries for ClamAV, each using 14% of my RAM, far more than anything else.  I tried to 'kill' it, but it wouldn't die...  That's scary!
Yes, I use a proprietary driver for my GPU and it works fine.  As I said, I was doing things I normally do, but with the abnormal memory suck.
So, do I really need ClamAV?  I find it hard to use anyway, as I can't get it to scan my whole system.  If I can do without it, how do I kill it?
Many Thanks!
If ClamAV is running as the user "root", or as another user that is not yourself, then you cannot kill it, because you don't have permission. For that, you need to use "sudo".
```

sudo pkill clamav

```
This will search the processes named "clamav" and then send the SIGTERM (kill) signal to it. You can also kill it with the process id number. In "htop" this is the same as selecting the appropriate process with the arrows in your keyboard and hitting «F9», SIGTERM, «Enter».
```

sudo kill [process id]

```

If you see two instances of ClamAV both using exactly 14% memory, it is possible that there is only one process. The output of "htop" is a bit strange, sometimes it shows repeated processes, and this has to do with the number of "threads" launched, and a few advanced things like that.

Do you really need ClamAV? Well, only you can answer that. Do you know how it works? Did you install it for a particular reason? Most probably you don't need it because your system won't get Windows' virus anyway. Only if you operated an email server, where you had to scan many incoming and outgoing messages, you would need it. If you can do without it, don't just kill it, but remove it from your system.
```

sudo apt remove clamav

```

---

### Post by BenginM on 2017-07-19
Salutations!

i wont add much upon what vocx mentioned ..

I also happen to have an AMD CPU with Radeon HD Graphics on my desktop machine using the free driver radeon flyin' ubuntu gnome 16.04 with 4G RAMs ..

mostly i have three Firefox windows open with many tabs, irssi inside gnu screen ina terminal .. with that, the CPU and RAM are as shown in this image:

[ATTACH=CONFIG]276062[/ATTACH]

Now mind you .. if i run virtualbox in the back .. the RAM and CPUs ratios jumps higher ..

[ATTACH=CONFIG]276063[/ATTACH]

I suppose we both should upgrade more RAMs or use a minimal installation setup , like openbox with X11 server . just a food for thought!

---

