---
title: "$PATH problem in 12.04 &quot;WARNING: your PATH doesn't contain ...&quot;"
date: 2014-07-07
forum: General Help
---

### Post by ilker_Basaran on 2014-07-07
Hi, I'm new to Ubuntu, and couldn't find a way around my problem..

I'm using 12.04 LTS and trying to install a simulator (Omnet++)

When I try and configure, it gives the below warning:
----------------
WARNING: your PATH doesn't contain /home/ilker/omnetpp/bin!
Add the following line to your .profile or .bash_profile (provided you use bash):
  export PATH=$PATH:/home/ilker/omnetpp/bin
-------------------------------

and I can't continue to make.


BUT

I already added /home/ilker/omnetpp/bin to all 5 places:
~/.bashrc
~/.profile
/etc/profile
/etc/environment
/etc/bash.bashrc


Here is the echo of my $PATH
-------------------------
ilker@ccccccccc:~/omnetpp$ echo $PATH
/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/ilker/omnetpp/bin
-----------------------------

I also sourced above mentioned 5 files many times..I tried closing and re-opening terminal, logging out and back in and also tried rebooting...nothing worked..

I added the directory to PATH as it asked..the PATH variable has that directory..but configuration doesn't see it..

I'm trying to solve this more than 10 days now and very close to going mad..

I'll appreciate all the help that I can get..

Thanks a lot in advance..

---

