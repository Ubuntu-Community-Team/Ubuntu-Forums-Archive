---
title: "Strange Happenings"
date: 2007-05-18
forum: General Help
---

### Post by BostonBrother on 2007-05-18
I was messing around with xgl trying to get beryl to work with my ati card and was following a tutorial that suggested installing the beryl-xgl binary, which I did.  When I started the script it flashed the screen a couple of times and proceeded to lock things up so I restarted my compter.  After the restart I found that I had lost my sound and networking abilities, both my ethernet and wireless cards are not working.  Does anybody know how messing with the graphics caused problems with by sound and network?  Also, more importantly what is the easiest way for me to get it back up and working?  I'm not sure if anything else is messed up.  Would re-installing the kde-desktop meta-package work?

---

### Post by mbradlcu on 2007-05-19
yep that's funky happenings alright... 
maybe create a test user account and see it's it specific to you're user configs.. 
it wouldn't be the first time I had to blow away my ~/.gnome* dir ; )

---

### Post by BostonBrother on 2007-05-19
Already thought of that.  I am having the same problem with all of my user accounts.  In fact, I went into the recovery mode and tried to ping [http://www.yahoo.com](http://www.yahoo.com) and couldn't even do that.  So I don't even have a network connection in recovery.

What did you mean by blowing away your home directory?  How would I do that?

---

### Post by mbradlcu on 2007-05-20
have you tried to enable your nic manually:
sudo ifconfig up
sudo dhclient eth0
I'm guessing your nic is eth0,, another test is see if the kernel actually detects the hardware;
lspci | grep -i ethernet

O and about deleting my home dir,, yea I've done that accidentally but I've intentionally deleted the .gnome* configuration directories for various reasons.. the command is 'rm -rvf /home' ,, beware it's unforgiving and dangerous.

---

### Post by BostonBrother on 2007-05-27
Well the kernel is detecting my ethernet card, but I didn't get anything for my wireless.  Also when I manually tried to enable my nic as you suggested I was unable to do it.  I'm starting to wonder if this is a glitch with the configuration of the kernel seeing as it is both my network and sound that was messed with at the same time.  Those two things don't have much to do with each other that I know of.  Is there a way to configure the kernel automatically like the install cd does or will I have to go into the kernel and make the adjustments.  Also, if I have to do this how would I do this.  I remember a bit from when I messed with installing gentoo, but I would need a refresher.

---

### Post by mbradlcu on 2007-05-29
yea, it's a little strange your other perferials are messed up too.. anyway here's a link I use to remind myself how to re/build the kernel:
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

---

