---
title: "DeVeDe problem in Gutsy"
date: 2007-10-19
forum: General Help
---

### Post by enstardavid on 2007-10-19
Hi, 
I had DeVeDe 3.2 workingjust fine in Feisty.

I upgraded to Gutsy today - generally smoothly - but DeVeDe won't load. It show in the Applications menu.I have tried deselecting and reselecting from Add and Remove - Gutsy seems to think it is there but it won't start. No error message - just click and nothing.

I am wondering if there is a Python change and that is causing it? Any suggestions as to how to move forward?

Anyone else with the same problem?

Thanks,

David

---

### Post by lordkalkin on 2007-10-19
I'm having exactly the same problem.  I tried just downloading it from the site and installing it again, but no go on that.  Any ideas?

---

### Post by gazzar on 2007-10-19
try running it from the terminal, see if it gives any errors.

I had the same/similar problem. It run in feisty fine, but after upgrading to gutsy, it no longer worked. my problem was down to the fact that i had manually upgraded devede to v3.2 on feisty, so when i upgraded to gutsy, things got messy. Using the error messages from the terminal I tracked down the manual installed files and removed them, then did a reinstall on the gutsy version of devede and all started working again.

hope this helps

---

### Post by lordkalkin on 2007-10-19
On your advice, I started by removing Devede in Add/Remove Programs.  Then, I decided to put 'devede' into a terminal and see if the program was really gone.  I got a dialogue box telling me that I needed to install mplayer and mencoer (which Add/Remove Programs removed with Devede).  I installed those from the command line, then ran the command again.  Everything worked fine.

thanks.

---

### Post by enstardavid on 2007-10-20
Hi, 

I also had manually upgraded to 3.2 (by 'blindly' following a forum guide, I am sorry to say. But it worked fine.

I am afraid I am a Ubuntu newbie - what are the commands that you need to run?

I guess I open a Terminal  - but what do I type there?

---

### Post by enstardavid on 2007-10-22
Hi - 

gazzar was correct (and I was trying too hard).

Simply uninstalling, removing the files 'manually' and then reinstalling got it working.

Thanks.

David

---

