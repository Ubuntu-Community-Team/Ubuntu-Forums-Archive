---
title: "Open remote terminal"
date: 2014-04-20
forum: General Help
---

### Post by chris137 on 2014-04-20
Hi,
Right now I am trying to use my notebook mostly remotely.
Starting the notebook, starting all needed programs and shutting it down does work.
There is only one thing I don't even know how to start with even if it might be easy.
Very important for alle the above is that my external drive is mounted.
Sometimes it is not recognized by linux and I have to unplug the power of the drive and put it back in.
Everything will work after that.
Since I think that it is not an linux-side issue I do not want to investigate it any further.
What I want to do is the following:

Write a script which reminds me to do just this.
Would look something like this:
if /dev/sdc1 present
be happy
else popup at remote@host

So in the last line I'd like to have a command which - maybe via ssh - opens a terminal on the remote pc from which I control my notebook with echo 'mount the drive, retard' or similar
I have no idea how to approach this, maybe you can help

Thanks

---

