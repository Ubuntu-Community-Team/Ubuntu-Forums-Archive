---
title: "Ubuntu not have power management for HDD ?"
date: 2022-04-17
forum: General Help
---

### Post by aug7744 on 2022-04-17
Hello.
In windows have option to disable power off idle HDDs if the system have more than one disk.
I use Lubuntu and not see any option to configure an value in minutes to power off HDD.
Ubuntu have any configuration to power off idle disks ?
Thanks for reply.

---

### Post by TheFu on 2022-04-18
HDD power management is built into the firmware of the HDD.  There are a number of levels possible (254 levels) to be set using the **hdparm** tool. It is command line.  Not all HDDs support APM. [https://manpages.ubuntu.com/manpages/xenial/man8/hdparm.8.html](https://manpages.ubuntu.com/manpages/xenial/man8/hdparm.8.html) and [https://www.linux-magazine.com/Online/Features/Tune-Your-Hard-Disk-with-hdparm](https://www.linux-magazine.com/Online/Features/Tune-Your-Hard-Disk-with-hdparm) can explain better.

There are two different groups of people.  I'm in the group that prevents HDD spin down, because I believe the change in spin-up/down all the time is bad for drive lifetime.  Others think that spinning down a drive will have less wear and tear on the drive.  I don't know which group is "correct."  If our power bill was higher, perhaps I'd be in the spin-down always group.  For a laptop, I would want to spin down an HDD as a safety choice, since laptops get bumped all the time. Of course, nearly all laptops use SSDs now, so there isn't any spindown on a solid state (no moving parts) storage device.

---

### Post by aug7744 on 2022-04-18
@TheFu
Hello. All right you ?
I'm also in group dislike spin down.
Power consume is less of 5 watts.
In windows is simple choice an time to power off an HDD idle.

hdparm can configure to power off for example in 20 minutes inactivity ?
I have an extremely care about changing HDD firmware settings. The only time that I had changed was using Western Digital Idle 3.15 command line to change the spin down from the iinfamous WD HDD green caviar.

---

### Post by TheFu on 2022-04-18
5W is the startup power, not after is is already up and spinning.  Then it drops by 50-75%. The numbers are on the box for the HDD purchased.
I know nothing about Windows. The interface it dumbed down too much and we never **really** know what it does, regardless of what the GUI says.

I have an old WD-Green, that was spinning down and tried to stop it.  It wouldn't keep spinning no matter what I tried. I think it was something in the firmware.  The drive doesn't claim to be broken, but it often isn't available fast enough and gets dropped in the BIOS.  Firmware being too smart can be bad.

Unix/Linux systems are multi-user from the ground up, so there won't really be 20 minutes of inactivity on the OS partitions ... ever.  For data partitions, we can use autofs which will umount them a few minutes after the last file on that file system is closed and no others are open. There isn't any point-n-click interface for autofs.

I'm not the person to ask about GUI stuff, as I barely use any GUIs.  For me, GUIs are a way to have more terminal windows to get real work done.  Every Ubuntu flavor has a "XYZ Desktop Guide"  Lubuntu, Kubuntu, Mate, Gnome ... which have the GUI point-n-click answers that are available. If the answer you seek isn't in one of those, I expect it isn't implemented using any GUI, so handling it via a CLI tool is necessary.  That's what **hdparm** is, which I've already provided the available information concerning.  I won't make up an answer, since what each HDD model from every vendor does with the different APM settings is 100% proprietary. I've never seen that information shared anywhere, but feel free to look. Perhaps someone else found some and posted it online?  IDK.

---

### Post by HermanAB on 2022-04-19
Nobody read man pages anymore, because there is too much information in them:

$ man hdparm
...
DESCRIPTION
       hdparm provides a command line interface to various kernel
       interfaces supported by the Linux SATA/PATA/SAS "libata"
       subsystem and the older IDE driver subsystem.  Many newer (2008
       and later) USB drive enclosures now also support "SAT" (SCSI-ATA
       Command Translation) and therefore may also work with hdparm.
       E.g. recent WD "Passport" models and recent NexStar-3 enclosures.
       Some options may work correctly only with the latest kernels.
...
     -S     Put the drive into idle (low-power) mode, and also set the
              standby (spindown) timeout for the drive.  This timeout
              value is used by the drive to determine how long to wait
              (with no disk activity) before turning off the spindle
              motor to save power.  Under such circumstances, the drive
              may take as long as 30 seconds to respond to a subsequent
              disk access, though most drives are much quicker.  The
              encoding of the timeout value is somewhat peculiar.  A
              value of zero means "timeouts are disabled": the device
              will not automatically enter standby mode.  Values from 1
              to 240 specify multiples of 5 seconds, yielding timeouts
              from 5 seconds to 20 minutes.  Values from 241 to 251
              specify from 1 to 11 units of 30 minutes, yielding
              timeouts from 30 minutes to 5.5 hours.  A value of 252
              signifies a timeout of 21 minutes. A value of 253 sets a
              vendor-defined timeout period between 8 and 12 hours, and
              the value 254 is reserved.  255 is interpreted as 21
              minutes plus 15 seconds.  Note that some older drives may
              have very different interpretations of these values.
...
etc.

---

### Post by TheFu on 2022-04-19
> **HermanAB said:**
> Nobody read man pages anymore, because there is too much information in them: 

True. Definitely applies to me some times.  Plus the forum rules I recall don't like us simply pointing at manpages, through that was a key part of my early Unix training by my team and mentor.  They simply refused to answer any question that was covered in the manpage or, if on Windows, from the /? help option.  Of course, they'd just use a 4 letter term which is forbidden here. ;)

---

### Post by HermanAB on 2022-04-20
I used to have a coffee mug with the abbreviation for Please Read The Very Nice Manual printed on it. :)

---

### Post by QIII on 2022-04-20
We're actually all for guiding people to the man pages.

What we don't want is simple, cryptic answers like "*RTVNM*" or "*man bar*".

We encourage answers like "If you use *man bar* and scroll down to section X, there are a few suggestions for the flag to use to set the behavior you are looking for.  In my experience, the flag -@ causes more problems than it solves, so I would avoid that."

Personally, I use the man pages and I think we should instruct people in their use.

---

### Post by TheFu on 2022-04-20
Thanks for the clarification.  

Of course all of us here recognize that learning to read the man pages takes time.  They are more like a newspaper article than a novel or instruction book (How To Learn Ubuntu).  Newspaper articles start with the most important ideas first, then delve into more and more details as we read farther. Same for well-written manpages.

When I was first learning Unix, reading manpages was hard. They are so very rich in important details it is a bunch of information to take in.  There isn't a manpage-team, so each is written by the project team for the program. A few programmers aren't known for being great literature writers. ;) They can be dry reading.  30 years ago, some of the manpages had jokes in them. Then the corporate-types got their hands on them and purged all the jokes.  I recall tunefs had a line near the end - "You can tune an FS, but you can't tune a fish."   Ok, perhaps bad jokes, but they were trying with this reference to a popular rock band. [https://unixhistory.livejournal.com/1808.html](https://unixhistory.livejournal.com/1808.html)

---

### Post by HermanAB on 2022-04-20
Tuna fish?  OK, OK, I’ll see myself out…

---

### Post by dragonfly41 on 2022-04-20
> [COLOR=#000000]They are more like a newspaper article than a novel or instruction book (How To Learn Ubuntu). Newspaper articles start with the most important ideas first, then delve into more and more details as we read farther. Same for well-written manpages[/COLOR]

Perhaps I can suggest using a concordance tool (semantic analysis) which simplifies the task of understanding many such tomes? All the text files are thrown into a hopper and key words are searched.

---

### Post by TheFu on 2022-04-20
Manpage searching sorta sucks if you don't know the command name.  Sure, there's apropos (aka man -k), but that only searches the single line name-summary, not the entire manpage.
There's also a webtool that breaks down a command and shows the related manpage paragraphs based on each option.  **explainshell.com** Can be very useful for those complex 1-like commands, but the manpage they use as reference many not match the version on each of our systems.  In reality, that's usually a 5% problem with 95%+ of the time, it is accurate.

---

