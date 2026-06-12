---
title: "Ubuntu Software Center stuck in a search"
date: 2015-04-27
forum: General Help
---

### Post by hoosemon61 on 2015-04-27
HI,

I recently installed drop box using Ubuntu Software Center, and it appeared to hang during install, when the install progress bar showed about 90% complete.

After leaving it alone for about an hour, I finally rebooted the computer.

Drop Box actually installed correctly, but USC is now stuck with some kind of search in progress and I can't delete it.

I clicked on the red X to the right of the progress bar,and the search icon now says cancelling under it, but it never progresses - by never, I mean I left it overnight.

I can try and install or remove other software, but they queue up behind this stalled search, so they never start.

I tried using sudo apt-get to install Synaptic, to remove USC, and to remove dropbox, but I get the same error each time:

[INDENT][I]E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/I][/INDENT]

Everything else seems to run fine, I can open and close USC and reboot the computer, but when I reopen USC it goes straight into the stuck search.

I'm running 12.04 LTS - 32 bit.


Any ideas?

Thanks,

Hoosemon

---

### Post by Skaperen on 2015-04-28
since you have rebooted, nothing should be running, go ahead, start a terminal and **[FONT=courier new]sudo rm /var/lib/dpkg/lock[/FONT]**. i would remove drop box and install it again to be sure it really is complete.

---

### Post by hoosemon61 on 2015-04-28
Ok,I did that and the command executed without any errors.

I then tried *'sudo apt-get remove dropbox' *and got this error:

*E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem*

So I ran that - it comes back with *'Setting up nautilus-dropbox'*

Then a new line, downloading dropbox, displaying % and there's a little one line advert for dropbox. 

When it reaches 100%, just sits there, no new prompt.

If I try to close Terminal, it says a process is still running.

It does exactly the same thing when I start over and try running* 'sudo apt-get install synaptic' * 

Seems like the command line version of what it does when I run USC.  

It's like the dropbox install never finished and it refuses to do anything else with package management until it's done.

Where to from here?


Hoosemon

---

