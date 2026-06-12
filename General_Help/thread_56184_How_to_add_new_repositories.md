---
title: "How to add new repositories?"
date: 2005-08-11
forum: General Help
---

### Post by clehel on 2005-08-11
Hi,
I need your help. I am new to Linux, but was so far lucky to set up Kubuntu (Ubuntu 5.0.4), and added all repositories as described in the official Ubuntu guide. I was also able to add the Skype repository, as described in a recent post on this forum. However, I am stuck hear. I thought I would add the Debian repository, and maybe freshmeat, etc., but I could not. I tried both by directly editing the /etc/apt/sources.list file, or by adding them through the "Repositories" window of Synaptic, which writes to the same file. I was able to add some repositories, but I always get the same error message when I afterward start Synaptic, like: 

"Couldn't stat source package list [ftp://ftp.debian.org](ftp://ftp.debian.org) etch/main Packages (/var/lib/apt/lists/ftp.debian.org_debian_dists_etch_main_binary-i386_Packages) - stat (2 No such file or directory)"

I tried many things, to follow the set-up of already added repositories, but with no success. Can you please help me by telling what is the trick? :confused:

Thanks a lot in advance,
Csaba

---

### Post by Juergen on 2005-08-11
> I thought I would add the Debian repository, and maybe freshmeat, etc.IMHO you are on you way to make your system unstable/unusable.

Many of those packages not specifically built for your (K)Ubuntu probably need different versions of libraries than are installed. 
Install those, and the rest of your system won't work properly anymore...

Stay with the official (K)Ubuntu repositories until you are able to repair strange behaviour of your system! (will probably take several months - at least)

If you **really** need something that isn't available from the official repositories (like skype), you might make an exception - but don't blame Linux, Ubuntu or someone else, if you have problems afterwards ;-)

So, now to your problem.
For me, the 'etch/'-part seems wrong. Look where this comes from.
Best in such a situation is just to post your sources.lst here (strip the comments for brevity)

---

### Post by clehel on 2005-08-11
Dear Juergen,
Thanks. I actually would need just a few pieces of software, so it is not so serious, and thanks for your advice to be patient. The line in /etc/apt/sources.list looks like this:

deb [ftp://ftp.debian.org/debian/](ftp://ftp.debian.org/debian/) etch main non-free 

I added it this way, because the "main" and "non-free" directories are within this directory on the debian server:

ftp.debian.org/debian/dists/etch/

What should I change?
Csaba

---

### Post by Juergen on 2005-08-11
Just remove the space before 'etch', I think. 
It seems to be built like a seperate release

(And again: if it wants to (re-)install 100eds of dependencies, shy away ;-))

---

