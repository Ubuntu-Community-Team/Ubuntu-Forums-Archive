---
title: "Housekeeping"
date: 2006-07-07
forum: General Help
---

### Post by Sonofmoog on 2006-07-07
Two related problems about recovering some hard drive space.  My Ubuntu partition is 96% full, as the system reminds me every time I boot.  Using Synaptic to uninstall applications I don't want is hopeless, because:

1) there are thousands of installed packages; even finding likely candidates takes hours, and when I do
2) I'm stuck with dependency problems.  That file is required by ubuntu-common or ubuntu-desktop, or ubuntu-something.  IOW, it's a system file and I can't touch it.  
3) Everything I have on my system now I want to keep, and resizing the partition to increase space is not an option.  

So:

I'm left with canvassing the file system folder by folder for files I don't need.  The question is, what files?

I moved packages I had in /var/cache/apt/archives to another partition, but that's only a short term solution.  

Possibilities:

1) Install puts two kernels on my system.  Can I safely uninstall the older one, and if so, how?

2) Are there any files - fonts, multimedia files, icon sets, text documents, etc, that I can safely delete.  If so, where are they?

TIA for your help.

---

### Post by torfinn on 2006-07-07
Perhaps you have a local repository of downloaded packages that you no longer need. To clean these out, you may do a:
$  apt-get clean

However, since this must be done using 'sudo', I recommend that you convince yourselves that this is really what you want by checking the documentation, see:
$ info apt-get .

Since you have already moved alot of '/var/cache/apt/archives' I am not sure this will help much.

Torfinn

---

### Post by Sonofmoog on 2006-07-07
> **torfinn said:**
> Perhaps you have a local repository of downloaded packages that you no longer need. To clean these out, you may do a:
$  apt-get clean

[snip]

Since you have already moved alot of '/var/cache/apt/archives' I am not sure this will help much.



Actually, it did.  Thanks for the reply.  I moved the packages back to the ..archives folder, ran apt-get clean and it deleted them.  That helps my storage problem quite a bit.  I'm hoping that since apt-get didn't need them, I won't either.  

Can I delete some of those international fonts in /usr/share/fonts/truetype without hosing my system?

---

### Post by vem0m on 2006-07-07
also is there a command for dpkg like that as its used more by me anyways or is it the same thing?

---

