---
title: "Running multiple copies of a program that doesn't want to."
date: 2013-02-17
forum: General Help
---

### Post by Cyhawk on 2013-02-17
I'm stumped. In my years of using Linux I've never before needed to do this before and I'm wondering if anyone has an elegant solution for this problem. I haven't been able to find a proper solution googling the issue.

Short question: I need a sandboxing utility that has persistent environments. On windows the solution is to use Sandboxie. Is there something similar in Linux?

Long answer: I have a specific need to run multiple copies of Steam in a persistent environment. (reason being, idle accounts)

Arkose is great, however it doesn't allow persistent environments. LXC uses too much overhead, and won't connect to the x server. VMware/virtualization has massive overhead and I can't automate it.

chroot is an option but its not only annoying to setup but will end up eating a lot more disk space than I want to.

Any suggestions?

---

### Post by TheFu on 2013-02-17
Connecting to X will be an issue unless you can use a virtual X driver to trick each environment. That will work.  **xvfb** is probably what you want. [https://en.wikipedia.org/wiki/Xvfb](https://en.wikipedia.org/wiki/Xvfb) explains.  I've used it for Oracle installations - when an X/Server was needed on a real, huge, UNIX server - absolutely makes no sense whatsoever for that to be required for a "server" software to run that doesn't have any GUI, but whatever.

LXC doesn't really have any overhead - unless you mean complexity. Only 1 kernel is loaded. Just different data segments are used. The overhead isn't much more than a chroot.

Chroot doesn't need to use very much more disk storage. Just use hard-links for the files that can be identical.  cp -rl

Most programs - and I know absolutely nothing about **steam** - most programs support passing in a config file that can point to different directories, use different ports and can specify different temporary files.  Something like JAVA_HOME or WINEPREFIX are examples, so that completely different environments can be run under the same account.  
If that doesn't work, why not just create different user accounts? That should work, provided the software does not use hard-coded system resources like a specific named-pipe file in /tmp/ or a listener for a very specific inbound port that cannot be changed via a config file.

The** lsof** command should help you determine which system resources are used by a program to help figure out if the steam program devs were multi-user friendly or not.  I could easily understand that those devs would believe only 1 person would be using a computer at a time - that is how Windows desktops are designed and have been for 25+ yrs. 

I thought that abusing idle accounts was enough reason to be band.

---

