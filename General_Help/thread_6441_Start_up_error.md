---
title: "Start up error"
date: 2004-11-28
forum: General Help
---

### Post by peter_barb on 2004-11-28
I seem to be getting an error when I start up ubuntu.

Well severall

Here is what happens..

Well to start off when it says 'Configuring network interfaces' that takes 5 minutes to load. Anyway to fix that?

I also get "fail" in "ror - Temporary failuar in name resolution"

Also I get two error messages about that.. I took a picture of it with my webcam..

[http://peterbarbosa.com/images/linux.jpg](http://peterbarbosa.com/images/linux.jpg)

---

### Post by WW on 2004-11-28
The modprobe errors involving shpchp and pciehp are common and apparently harmless:

[http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions#booterrors](http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions#booterrors)

You might find more information about it by searching for "pciehp" in this forum.

---

### Post by peter_barb on 2004-11-28
Okay how about

Well to start off when it says 'Configuring network interfaces' that takes 5 minutes to load. Anyway to fix that?

I also get "fail" in "ror - Temporary failuar in name resolution"

Also I am a newbie at Linux. It says I can fix those by adding "shpchp and pciehp". What are those and how do I add them ;-)

---

### Post by jiyuu0 on 2004-11-28
[QUOTE=peter_barb]
Well to start off when it says 'Configuring network interfaces' that takes 5 minutes to load. Anyway to fix that?
[/QUOTE]

If you are not using networking, you can either choose to disable the "networking" service on boot-up and when u need it just start it manually

else just hit Ctrl + C at "Configuring network interfaces" if you can't wait...

---

### Post by peter_barb on 2004-11-28
Thanks that works perfect, now I just gotta learn how to get rid of thsoe two messages, and that failing message :-)

---

### Post by jiyuu0 on 2004-11-28
[QUOTE=peter_barb]Thanks that works perfect, now I just gotta learn how to get rid of thsoe two messages, and that failing message :-)[/QUOTE]

to get rid of the two messages, either the link above or
[http://kitech.com.my/ubuntu/4.10/index.html#modprobefatalerror](http://kitech.com.my/ubuntu/4.10/index.html#modprobefatalerror)

---

### Post by WW on 2004-11-28
> Also I am a newbie at Linux. It says I can fix those by adding "shpchp and pciehp". What are those and how do I add them 
**shpchp** and **pciehp** are kernel modules that provide
drivers for some computer hardware.  Ubuntu tries to load them
without knowing in advance if your computer has the appropriate
hardware.  There is nothing wrong with this; the only "problem"
is the messages that are printed when the modules fail to find
the appropriate hardware. (Perhaps a friendlier message would
be something like [i]shpchp: This module will not be loaded
because your computer does not need it.[/i])

/etc/hotplug/blacklist is a text file.  Each line in the file is
the name of a module (or a comment).  During boot, Ubuntu
will not try to load any of the modules that it finds in this
file.  So to get rid of the modprobe errors at boot, you can
add two lines to this file, one containing **shpchp**, and
one containing **pciehp**. There are many ways to do this.
The wiki page

  [http://www.ubuntulinux.org/wiki/BootHotPlugErrors](http://www.ubuntulinux.org/wiki/BootHotPlugErrors)

suggests using the editor **gedit**, and that should work
fine.  Here's another way that is easy for me to explain:

1. Launch a terminal by selecting **Applications->System Tools->Terminal**.
This will bring up a terminal window.

2. Enter the following sequence of commands at the $ prompts:
```
cd /etc/hotplug
sudo sed -i.sav '$ashpchp\npciehp' blacklist
exit

```
The first command (**cd ...**) changes your current directory
to /etc/hotplug.

The second (admittedly rather cryptic) command (**sudo sed ...**)
does two things. It saves a copy of the file blacklist in blacklist.sav,
and adds two lines to blacklist, one containing **shpchp** and one
containing **pciehp**.  You will be asked for your password when
you run this command.

The last line (**exit**) will close the terminal window.

The next time you boot, you should not get the modprobe errors.

By the way, this probably has nothing to do with your network problems.

---

### Post by peter_barb on 2004-11-28
Works like a charm my friend.

Thanks :-)

Long live linux

---

### Post by bigmista on 2006-02-15
I get the same fatal error on bootup with the pciehp and shpchp. I want to be able to use these because I want to connect an external hard drive that contains my music. I'd like to be able to access this drive with my windows laptops. when I want to listen to music.

Can anyone help?

---

