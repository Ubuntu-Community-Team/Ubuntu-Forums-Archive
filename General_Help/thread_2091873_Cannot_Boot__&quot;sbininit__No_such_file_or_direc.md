---
title: "Cannot Boot:  &quot;/sbin/init:  No such file or directory&quot;"
date: 2012-12-06
forum: General Help
---

### Post by svtguy88 on 2012-12-06
Well, I'm not entirely sure what happened, but my Ubuntu partition is hosed.  If I try to do a standard boot, I'm stuck with a blank monitor after the Grub menu.  Selecting "Recovery Mode" shows me the following:  

```
run-init:  /sbin/init:  No such file or directory
Kernel panic - not syncying:  Attempted to kill init!
Pid:  1, comm:  run-init Not tainted 3.2.0-34-generic #53-Ubuntu

```

The stack trace follows that, and the system hangs.

My first thought was that the filesystem got corrupted somehow (maybe an update or a nasty reboot), so I booted to my my flash drive (Ubuntu Live CD).  Following a few other similar threads online, I ran:

```
sudo debugfs
crli <8>
quit
```

Followed by this:

```
sudo fsck -yv /dev/sda1
```

fsck found a _bunch_ of errors and fixed them, but I still get stuck with the same error when I try to boot...

Ideas?

---

### Post by rnerwein on 2012-12-06
> **pkmgarf said:**
> Well, I'm not entirely sure what happened, but my Ubuntu partition is hosed.  If I try to do a standard boot, I'm stuck with a blank monitor after the Grub menu.  Selecting "Recovery Mode" shows me the following:  

```
run-init:  /sbin/init:  No such file or directory
Kernel panic - not syncying:  Attempted to kill init!
Pid:  1, comm:  run-init Not tainted 3.2.0-34-generic #53-Ubuntu

```The stack trace follows that, and the system hangs.

My first thought was that the filesystem got corrupted somehow (maybe an update or a nasty reboot), so I booted to my my flash drive (Ubuntu Live CD).  Following a few other similar threads online, I ran:

```
sudo debugfs
crli <8>
quit
```Followed by this:

```
sudo fsck -yv /dev/sda1
```fsck found a _bunch_ of errors and fixed them, but I still get stuck with the same error when I try to boot...

Ideas?
is there some stuff in /lost+found ?
is /sbin/init present and a real  ELF 64-bit LSB shared object ( don't lough i got a shell script in init long long ago after a panic in solaris 6) --> file init
cheers

---

### Post by svtguy88 on 2012-12-08
Finally got a chance to look at this again.

There is a LOT of stuff in lost+found -- like 15 GB.  /sbin/init is present, and looks to be valid.

What should I go about doing?  I'm almost thinking of just grabbing my home folder and reinstalling.

---

### Post by rnerwein on 2012-12-08
> **pkmgarf said:**
> Finally got a chance to look at this again.

There is a LOT of stuff in lost+found -- like 15 GB.  /sbin/init is present, and looks to be valid.

What should I go about doing?  I'm almost thinking of just grabbing my home folder and reinstalling.
oh 15 GB
to rescue files from there you need the checksums and .....
i would prefer -> rescue your privat data and configurations and then make a fresh install.
what i do for a quick reinstall is:
dpkg --get-selections | grep -v deinstall > allepakete.`date +%y.%m.%d.%H.%M`
and after reinstalled:
sudo dpkg --set-selections <  allepakete.the_date_and_time_i_want
sudo apt-get -y update
sudo apt-get dselect-upgrade
my privat data get back from the rsync saved data
cheers

---

### Post by svtguy88 on 2012-12-09
This just keeps getting better...

I went to backup my home folder, and it's not there. The entire /home directory is gone.

Not sure what to do...I *really* would like to rescue my home folder, but I don't understand why it's missing now.

*edit*

Stll don't know why my home folder disappeared.  I could have sworn it was there after I ran fsck.  Anyway, using the instructions [here]("http://karuppuswamy.com/wordpress/2010/06/09/how-to-recover-files-from-lostfound-after-fsck-in-linux-how-i-did-it-in-ubuntu/") as an outline, I'm in the process of salvaging the directories I actually need from my old home folder.  The process is sort of a pain (figuring out which lost+found directory belongs where), but at least I cn save my data...

This machine is my main desktop, and also used for web development, so I was starting t get concerned that I lost my Eclipse workspace.  Guess it's time to look into setting up a real backup system.

---

### Post by rnerwein on 2012-12-09
> **pkmgarf said:**
> This just keeps getting better...

I went to backup my home folder, and it's not there. The entire /home directory is gone.

Not sure what to do...I *really* would like to rescue my home folder, but I don't understand why it's missing now.

*edit*

Stll don't know why my home folder disappeared.  I could have sworn it was there after I ran fsck.  Anyway, using the instructions [here]("http://karuppuswamy.com/wordpress/2010/06/09/how-to-recover-files-from-lostfound-after-fsck-in-linux-how-i-did-it-in-ubuntu/") as an outline, I'm in the process of salvaging the directories I actually need from my old home folder.  The process is sort of a pain (figuring out which lost+found directory belongs where), but at least I cn save my data...

This machine is my main desktop, and also used for web development, so I was starting t get concerned that I lost my Eclipse workspace.  Guess it's time to look into setting up a real backup system.
oh yeah - to set up a real backup system will be done first when you lost of date (happend to me about 25 years ago - got a real head crash on my private data. thats mean there was nothing to recover witout a polished disk :-(  ).
at the moment i just use rsync to two of my boxes via wired lan.
in your former post a have seen that you was using [COLOR=Red]crli[/COLOR] . clear inode is a very very hot affair. on a normal install it's not present and that can imagine must have a reason.
[COLOR=Red]crli[/COLOR] is the change of the last exit - or a ticket to hell !
if you cleared the inode of your home directory - the entry point in the VTOC is gone !
make up a backup system - best is redudant. one on a second disk and one on another box.
cheers

---

### Post by svtguy88 on 2012-12-10
Well, all is well now.  I'm back up and running (now on 12.10), and  I managed to get all the important bits out of my home folder.

As for a backup system -- it's been on my to-do list for a long time.  I've been just copying my home folder from the desktop/dev box over to my server (which has a nice backup system employed already), but this route requires me remembering to actually push everything to the server in a timely manner.  Whatever I end up doing, it's going to be automated, as my most recent backup was 2+ weeks ago...

I'll have to throw some sort of rsync script together.

---

