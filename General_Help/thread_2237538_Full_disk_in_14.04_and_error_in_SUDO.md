---
title: "Full disk in 14.04 and error in SUDO"
date: 2014-08-02
forum: General Help
---

### Post by WB0HYQ on 2014-08-02
I keep a very close eye on disk usage so when I turned on my monitor this morning I was greeted by a message telling me my disk was very near full.  According to which application I ask (Properties of main drive, or the 'Disks' application) I have a drive of 233.4Gb/44.5Mb free OR 250G/13G free.

In either case, I have NO idea how it got filled up that rapidly as I just checked two days ago and was only useing around 80Gb on my 258G drive.  Trying to run almost anything gave me the error that "I can't run because of low disk space", I tried clearing out a few things:

bill@bill-UBU:~$ sudo apt-get clean
[sudo] password for bill: 
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
bill@bill-UBU:~$ 

I have always gotten this error from sudo, but the commands I issue normally get executed.  In this case, nothing happened.

I am now running "Disk Usage Analyzer" and get the error attached.

Where do I go from here?  Do I have to trash the disk and start over?

Bill

---

### Post by steeldriver on 2014-08-02
It looks like the majority of the usage is inside your /home directory - so apt-get clean isn't going to help much

If you are the only user of this computer, then it will really just be a matter of going through your own files and freeing up some space there - if there are other users, have them do the same. In either case 'sudo' should not be required. If the usage has suddenly gone up for no apparent reason, then check for large log files such as ~/.xsession-errors

Once you have some headroom, you can set about the other issues and try to fix the sudo error

---

### Post by ajgreeny on 2014-08-02
Run the DUA again but scan your /home this time to get a lot more detail of what is using all that space that you think you still have.

---

### Post by WB0HYQ on 2014-08-02
I have since run a number of 'cleanup' suggestions from various Ubuntu posts and have now managed to release a bit of space.  It isn't a lot, though.

The "properties" check responded as in the attached.  I now have an (undetermined) amount of space that is 'unreadable'.  I have no idea what that might be a result of as I used only some generally safe commands such as 'clean', 'autoclean', and 'autoremove'.  I alsu installed and ran Ubuntu Tweak, which found a large amount of items that I really don't need so I removed them.

I do agree that my /home appears to be the biggest offender size-wise and will work on paring it down.  I am the sole user of this computer so at least I dont' have to worry about others on it.

Bill

---

### Post by WB0HYQ on 2014-08-02
Holy catfish!  /home/Bill/.cache/upstart contains a load of files (225)!  Most of them are files of around a few KB to maybe 3Mb.  There is one file though that is "gnome-session-Unity.log.1" which is the ENTIRE 215.6Gb!

Can that one be deleted?  if so, then my problem is definitely solved.

How do I keep that from happening again?

Bill

---

### Post by WB0HYQ on 2014-08-02
I have poked around the log file and found that it is completely filled up with loggings from 'HTTrack'.  I used that application once, didn't like it, and uninstalled it after using it on my own web site.  I checked 'ps' and saw that there was some remnant still running that was making additions to the file as I watched.  Whne I killed that process, the file stabilized at 215.6Gb.  I think that an apt-get uninstall may in order to completely remove this app.  Before, I used only the GUI uninstaller.

Bill

---

### Post by WB0HYQ on 2014-08-02
I am now back to normal (8.3Gb in use on my drive).  I ran 'sudo apt-get purge httrack' and it removed three files (which I thought I'd already removed using Software Center).  Then I logged out and logged back in.  The HUGE gnome-session file was GONE and I had my drive back again.

The Properties display still how 'some contents unreadable' though.  I am not sure if that is a permissions thing, or that some directories/files are damaged.  A reboot seemed to work well (but still give me the "Malformed file - Press Enter to continue" thing) but boots up properly.

I am still plagued with my home display opening up with all the hidden files being displayed.  I can make them go away, but the default seems to be "display each and every file in the directory no matter what".  Is that changeable other than continually having to use the menu item and de-click 'show hidden files' or toggle Ctrl-H?

EDIT: Nevermind.  I changed Preferences and unchecked the box.  My bad.

Bill

---

### Post by ajgreeny on 2014-08-02
Interesting!!

What complete website did you download using httrack?  That was, no doubt, what was using all that space, and presumably continuing to do so after you had (you thought) stopped using it.

---

### Post by WB0HYQ on 2014-08-02
I agree that HTTrack kept running after I killed it (supposedly) by closing the GUI.  Since my computers run 24/7/365, in the evening, I just turned off the monitor.  Next morning, I got the "disk nearly full" message and asked for help.  The web site is my own co-shared with my wife at intellisigsys.net.  It's pretty new and I have a load of work to do on it, but I really just wanted to see how well HTTrack downloaded it back to my working computer.  As it turned out, when I shifted from Firefox to pale Moon, somehow that broke the link between HTTrack and the browser so it wouldn't run any more anyway.  HTTrack didn't do very well downloading the site at all.  Lots of missing links, pictures, and the like.

Anyway, gnome-session-Unity.log.1 went away when I logged out/in and the disk cleared.  That's what was important.  I'm going to mark this one Solved, I think.

Bil

---

