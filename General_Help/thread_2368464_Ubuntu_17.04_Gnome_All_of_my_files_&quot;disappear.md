---
title: "Ubuntu 17.04 Gnome: All of my files &quot;disappear&quot; and then computer crashes"
date: 2017-08-11
forum: General Help
---

### Post by bvz on 2017-08-11
I am repeatedly getting a situation where I will be using my machine (fresh 17.04 gnome install) when suddenly all of the files "disappear".  What I mean by that is suddenly I have no icons in my dash, no icons in my applications menu.  I cannot start up any apps that aren't already running.

If I have a terminal window open, I can cd through my file hierarchy, but I cannot run ls.  For example, if my cwd was /var/log and I run 'ls' it complains that 'ls' is no longer available.  I can cd .. and then be in /var, but I still can't 'ls' anything.  I can cd to root and then back to /var/log, but there are no files that I can see (or at least 'ls' is no longer working).  I can't open a new terminal window because it complains about missing files.

If I have nedit open, I can't "open" any files because no files show up in the file open dialog.  Any files I currently have open suddenly are orphaned, and nedit asks me if I want to save them with a new name because the original is no longer there.  In the open dialog I can navigate the hierarchy by typing in actual paths, but I cannot select a file that way (even if I know the file name).

None of my icons show up when I try to log out, but the empty circle that used to hold the power button icon is still there (and still works). I can also select my name and choose "log out".

When I do, I get a login screen with my name, but no icon.  I try to log back in, but then the screen goes to text and I get a bunch of text like:

/dev/sda5: recovering journal
/dev/sda5: Clearing orphaned inode 13019176 (uid=1000, gid=1000, mode=0100644, size=32768)
...
and so on

Then I slowly get lines like this:

[  738.776225] EXT4-fs error (device sda5): ext4_find_entry:1463: inode #12845057: comm (plymouth): reading directory Iblock 0
and more like that.



I am new to Linux administration (I use it all day long at work, but this is my home machine).

Any clue what is going on?  I have installed a new SSD when I set this machine up.  Could that be busted?  Or overheating?

Any suggestions on how I should debug this?

I hate Windows, but I really have to get my work done and cannot spend too many more hours trying to get Linux to behave (I just spent 6 days trying to get a VPN working before just giving up on it).  That said, when it works I really really really prefer Linux to Windows and am willing to invest a little bit more time getting this machine to work.

Thanks for any and all help!

---

### Post by efflandt on 2017-08-11
Check dmesg when that happens ( **dmesg | less** ) and see if that shows drive errors. Also check permissions in your home directory. If a drive gets too many errors, Linux remounts it read-only, so often a sign of a failing drive is when you cannot save a file in your own home directory because the partition has become read-only (no write permission).

I have never had any flash memory or SSD fail. The SSD I have had longest is an 80 GB Intel that I first used during Ubuntu 11.04 beta, but never ran 11.04 release, I skipped to 11.10, 12.04, then kept 12.04 on it as a backup system when installing 14.04 on my hard drive. Although I now also have a Crucial 512 GB mSATA SSD from failed laptop in SATA enclosure on my desktop that I have been running 16.10 from (which I either need to replace with 16.04 LTS or go to 17.04).

I have had some hard drives fail (usually gradually), most recently the Seagate drive on my PC that I bought in 2010 when 3 years old. That is why I know about auto remounting read-only, but I don't remember files temporarily disappearing.

---

### Post by bvz on 2017-08-11
Thanks for the quick reply.

It happened again.  This time I spent a little more time trying to diagnose it.  But to little avail.

I ran dmesg | less right when I rebooted this morning.  Nothing came up that looked suspicious (as far as I can tell).  There were no warnings or errors that I could see.  Just a bunch of messages about loading things and initializing things.  I left it running for when it crashed.  Once it crashed, I did not see any additional messages that seemed out of the ordinary (though it may have stopped reporting anything).  I can still page up and page down through the list though.

Once it crashes, I cannot run anything anymore.  It is literally as though every single file (but not directory) on disk is no longer available.

Any attempts to run anything fails because the underlying files are not accessible.  For example, 'ls' just reports "command not found".  

/bin/ls is the same.

The only commands that I am able to run (in an already open terminal window) are 'cd' and 'pwd'

Any running apps continue to run as long as they aren't dependent on accessing files.  For example, I am running a 3D application called "Clarisse".  I can continue to render, rotate the models, change attributes, etc.  Nothing there stops running because it has all of its resources loaded into memory.

Files, of course, can't locate any files and just shows me empty directories.

All of my chrome on the windows disappears (no close buttons, etc) but I can still move windows around and click inside of them.

I tried to ping the system from my Mac, but I couldn't remember the ip address and, of course, ifconfig would not run.

I am connecting to the internet through my Mac (my mac is connecting to the internet via WiFi and sharing it out over an ethernet cable to the Linux box).  I don't know if that is relevant.

Once I try to log out, the same thing happens.  I get a pretty screen that I can click on to lift up and show my login screen.  But the login screen does not show any icons.  If I try to log in, it just dumps me to that same text screen with the same messages as before 

I don't think this is a hardware error since I can still cd around in the terminal (i.e. for some reason enough of the shell functionality remains that I can use the cd command).  That does not sound like a hardware disk problem to me.  Also, when I reboot, everything is back up.

I was starting to push my computer a little today, but it also seems to happen when I am not doing very much (intensity wise).

The computer is set up as a dual boot system with Windows on a separate partition.  I am going to switch over (ugh) and try that system out for a while to see if it does anything funky.  The problem there is that it is Windows 10 Home and it only sees half of my processors.  But I have to get some work done here.

As far as getting Linux to work, should I try downgrading to the LTS?  Any other debugging suggestions?

---

### Post by bvz on 2017-08-12
Windows seemed to be relatively stable, but I haven't run it very long.  I really want Ubuntu to work.

So I downloaded 16.04 to my Mac, made a bootable DVD, and installed that over the top (replacing) my 17.04 install.

During the install I got an error while copying files. It asked me to check my HD to see if all the cables were tight etc.

I restarted and re-installed and this time everything worked as expected.  When the install finished and the system restarted, it went to a text screen and just showed me the message:

[    *] A start job is running for Ubuntu live CD installer (1min 12s / no limit)_

I let it sit for a while but nothing happens.  Eventually I reboot the machine and it comes up just fine.

Could I actually be having a hardware issue? It is a brand new SSD that I bought specifically for this machine.  Is there a utility I can run to test the HW?

---

### Post by bvz on 2017-08-13
I did a complete re-re-re-install of 16.04.3 LTS Gnome.

It does not like to download updates and 3rd party files while installing (I have to leave both of those turned off in order for it to work).

I set up my machine and started using it.

Again it crashes, though this time it does so differently.  It drops me to a text only screen with errors just like I described above.

I ran a memtest overnight and it came up clean.  I ran the S.M.A.R.T tests (the full test from the GUI) and that came up clean.

Could it be that Ubuntu doesn't like my SSD?  I saw this: [https://askubuntu.com/questions/905710/ext4-fs-error-after-ubuntu-17-04-upgrade](https://askubuntu.com/questions/905710/ext4-fs-error-after-ubuntu-17-04-upgrade) which, from a behavior standpoint, looks exactly like the issue I am having.

That said, I do not have an nvme drive.  Mine is a Sata SSD (Sandisk Ultra II 500GB).  I'm not sure how to test whether it is the SSD causing the trouble.  

So I am giving it one last go before bailing. My latest attempt at staying away from Windows will be to pull the ssd drive and do (yet another) fresh install on a 1TB mechanical HD (without a windows partition).  I will report back on how that works, but in the mean time if anyone has any suggestions I would greatly appreciate it.  I am starting to get behind in my deadlines because I keep futzing with this machine instead of doing my work.  It is actually kind of stupid of me because if I just pony up $100 I can get upgraded to Windows 10 Pro and get on with my life.  I just prefer Linux that much that I seem to be willing to go through this hell to stay away from Windows :)

---

### Post by bvz on 2017-08-14
I'm kind of having a conversation with myself here :)

So, the latest is that the install on a mechanical drive seems to have really helped.  I did get one complete lock up since I did that, but I was also switching around my network cables (while already connected to a networked drive) and then tried to connect access this networked drive.  I'll chalk that one up to user error hopefully.

But outside of that I have been hammering my system pretty hard, copying files, making directories, kicking all 24 threads off rendering.  All good.  No more crashes.

And the weird thing is, the system seems to boot faster from the Mechanical Drive than from the SSD.

I wished I hadn't spent the money on the SSD now, but I don't think it is actually bad.  I just think that the combination of my system (Dell t5500 Dual hexacore Xeon x5675) and my SSD (Sandisk Ultra II 500 GB) just does not play nicely with either 16.04.3 or 17.04.

I have zero time left to devote to this, so as long as this works I am not going to spend any efforts trying to debug the SSD.  Once I meet my deadlines I will try to get it to work again with the SSD.  I am especially curious in that Windows would boot up in seconds off the SSD while Linux seemed to take for ages (and was at the very minimum no faster with the SSD than it is with the mechanical HD).  So maybe there is something deeply wrong with that combo.  Perhaps I have to upgrade the firmware on that drive.  I dunno.  At any rate, I seem to be going along ok now (hope I haven't just jinxed myself).

---

### Post by QIII on 2017-08-14
Hello.

You might try [clearing the memory cells]("https://wiki.archlinux.org/index.php/Solid_State_Drives/Memory_cell_clearing") on the SSD and trying again.

---

### Post by bvz on 2017-08-14
Thanks.  Once I am able to get back to it I will give that a shot.

---

