---
title: "Evince Acrobat-Reader Synaptic misery"
date: 2007-11-27
forum: General Help
---

### Post by itsjustarumour on 2007-11-27
OK, heres my tale of woe.

Yesterday morning, I found myself in a position where as a matter of some urgency I had to go to the website of the Finnish government, fill out one of those online pdf forms (the ones that one can only complete inside a browser window), print it out, and then jump on a train to take it in to the Finnish embassy in London.

A simple task, one would think. I had Evince set up as my default Firefox plugin.  However, it didn't display the document correctly, and when the document was printed out it also included various items such as "click here for next page" boxes which, well, shouldn't have been printed out all over the top of the document.  I tried fiddling with all the Evince settings, but to no avail.  This was the first time I've ever tried to use Evince, and I'm sad to say it proved "not fit for purpose".  Aka, well, "crap".  So I thought I'd uninstall it using Synaptic.  Except I can't - or not without uninstalling the Ubuntu Desktop, apparently.  BAH.

Well, I also had Acrobat Reader 8.1 ("Acroread") installed.  Not available from the official Ubuntu repos unfortunately, but from the Medibuntu ones.  I changed the Firefox settings to default to it, and this time the form displays perfectly and I'm able to fill it out fine.  And then I try and print it out - nothing.  Zip, zilch - absolutely nothing happens.  Spend a bit more time going through the settings, but to no avail.  I then try uninstalling Acroread and reinstalling it using Synaptic.  Some funny messages came up at some point which I didn't really clock, and my problem remains the same. BAH again.

OK, by this time I'm running over an hour late (I've been very persistent in trying to get this Ubuntu thing to work, see?)  So I have to do what I really hate to do.  Yes, I had to boot into my trusted, reliable Windows XP installaltion to do my task.  And this time everything works perfectly, and within a few minutes I'm clutching my completed form all printed out on "Gold standard" A4 and I'm ready to run for another train.

Of course, I could go on at this point about how this is an absolutely perfect example of why I can't ditch MS Windows and move to Ubuntu as my only OS, because its just too unreliable and how every time the pressure is on and there is urgent "productivity" to be done Ubuntu always seems to let me down.  But I won't.  And anyway, thats not the main point of this post.  

I've booted into Ubuntu again today, and there are updates to be installed.  Except I can't - clicking on the Update Applet gives me:

> Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

So, I run "sudo apt-get install -f" and I get:

> ian@COOLERMASTER:~$ sudo apt-get install -f
[sudo] password for ian:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following packages were automatically installed and are no longer required:
  xchat-common libschroedinger-0.1-0 tcl8.4
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  acroread
The following NEW packages will be installed
  acroread
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
2 not fully installed or removed.
Need to get 0B/29.5MB of archives.
After unpacking 73.8MB of additional disk space will be used.
Do you want to continue [Y/n]? 


I select "Y", and I get:

> Do you want to continue [Y/n]? Y
(Reading database ... 128522 files and directories currently installed.)
Unpacking acroread (from .../acroread_8.1.1-0medibuntu3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/acroread_8.1.1-0medibuntu3_i386.deb (--unpack):
 trying to overwrite `/usr/bin/acroread', which is also in package adobereader-enu
Errors were encountered while processing:
 /var/cache/apt/archives/acroread_8.1.1-0medibuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ian@COOLERMASTER:~$ 


So, I've tried using 'apt-get autoremove' to remove the relevant component, I've tried going into the relevant directories and deleting apps and files manually, I've tried deleting the broken package using the Filters with "Settings" in Synaptic, and I've tried uninstalling and installing Acroread using Synaptic again.  And whatever I do, I still get the same error message from Synaptic.

And thus ends my tale of woe!

Can anybody offer any wisdom on this?  How do I uninstall Evince?  How to I get Acrobat Reader to print?  And how do I repair my Software Index?

---

### Post by itsjustarumour on 2007-11-27
Bump

---

### Post by itsjustarumour on 2007-12-23
Well, if it helps anyone, it appears my printing problems are down to a known bug at:

[https://bugs.launchpad.net/ubuntu/+source/acroread/+bug/145772](https://bugs.launchpad.net/ubuntu/+source/acroread/+bug/145772)

The software index problem just cured itself, eventually.....

---

