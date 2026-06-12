---
title: "Gutsy Pendrive what I know &amp; what I don't"
date: 2007-12-31
forum: General Help
---

### Post by charadeur on 2007-12-31
I have successfully installed Gutsy on a pen drive using the instructions from pendrivelinux.com about 6 times.  

What I have learned is that to save your network location you must make the path /root/.gnome2/network-admin-locations/<Locaton name file>  
You can then pick the filename from the network configuration tool in the GUI.  At that point it will save and can be recalled at next boot.  I was not able to figure out how to make it default every time.  

The big problem I have run into is when starting in persistent mode I get an error.  Sometimes it happens after the second reboot sometimes it waits to the 5th or 6th.  The main error I see is "unable to lock /home/ubuntu/ICEauthority Please report as a bug.  It may be caused by permissions to the directory."  

Booting into the normal non-persistent mode shows several files in the /media/casper-rw/home/ubuntu/ directory with question marks for owner, group, and permissions.  Deleting those files allow the boot into the GUI in persistent mode but the GUI does not respond after that.  

It seems like the routine to cleanup and save the persistent settings is not finishing as it should.  I have not been able to relate anything I am doing as the cause.  Sometimes the only change made was the background picture or similar non-invasive change.  

So has anyone else seen this issue or have any ideas?   Are you booting Gutsy from a pen drive in persistent mode with no issues?   I did search but did not find another post with the same problem.

---

### Post by dcstar on 2007-12-31
> **charadeur said:**
> I have successfully installed Gutsy on a pen drive using the instructions from pendrivelinux.com about 6 times.  
..........
So has anyone else seen this issue or have any ideas?   Are you booting Gutsy from a pen drive in persistent mode with no issues?   I did search but did not find another post with the same problem.

This works fine for me:

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by Zylar on 2008-01-02
I can also vouch for the wiki method, but I'm not sure about the PDL version.  Does the PDL one still have you download and run a .bat file?  I was always kind of wary of that.

Actually I am here looking for how the casper-rw stuff works, and just happened across your post and thought I'd chime in.

Good luck,

---

### Post by charadeur on 2008-01-07
Thanks for pointing me to the Wiki.  That method is solid.  The pendrivelinux.com site does have you upload their own cfg file where the Wiki one just has you adjust the file that is there.  The other difference is the way they copy the files and I think that might be what is wrong with the pendrivelinux.com instructions.  Anyway since using the Wiki I have had no drive corruption of the casper-rw drive.

Other things I have discovered is if you intend to install Wireshark do it from synaptic not from the deb utility.  I am still having some issues as I have to do a repair after a reboot or Wireshark will not run.  Any ideas on that one?

Nessus runs fine but don't start nessusd in Rc2.d because it just takes way too long to boot. 

Those are the two big utilities I wanted though I also installed putty and a few other small utilities.  

Any other security things you guys would install?  For wireless I have a notebook I use just for that with Backtrack installed.  I am mostly looking to do security audits at customers sites.

---

