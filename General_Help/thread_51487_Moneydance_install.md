---
title: "Moneydance install"
date: 2005-07-24
forum: General Help
---

### Post by darby on 2005-07-24
I have Moneydance as a tar.gz file on my desktop. Some help please in installing.
There appears to be nothing in Snyaptic.

Thank you.

---

### Post by PeP on 2005-07-24
[QUOTE=darby]I have Moneydance as a tar.gz file on my desktop. Some help please in installing.
There appears to be nothing in Snyaptic.

Thank you.[/QUOTE]
well use=ually, when you have a tarball you

1. 
cd /path/to/the/directory/
2. tar -xvzf thing.tar.gz
3. cd thing
4  ./configure
5. make
6. sudo make install

If you do not have the dependances, it might not work properly (one of three last steps) that  why ubuntu provides you well packaged deb files.
 
If it doesn't appear in synaptic, it means ubuntu does not provide it so you either have to

1. If you are quite comfortable with linux because it can be tricky:  get it from another distribution ( just try to add debian servers on your /etc/apt/sources.list  or a .rpm  converted with alien  )

2. if more likely you are not, just do as i told above, and solve the dependancy hell manually ...

---

### Post by darby on 2005-07-24
Thank you for your prompt reply.


Whoops, I now have Moneydance in /home/my name/Moneydance and if I click on the shell script it opens.

Some help on tidying things up would be appreciated.

Thank you.

---

