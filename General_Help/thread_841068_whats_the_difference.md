---
title: "whats the difference?"
date: 2008-06-26
forum: General Help
---

### Post by pavel989 on 2008-06-26
how does the server edition differ from the norm? i haven't like had a server edition, and i was thinking about checking it out, but figured this could save me the time/cd.

so, what is the main difference?

---

### Post by DirtDawg on 2008-06-26
> **pavel989 said:**
> how does the server edition differ from the norm? i haven't like had a server edition, and i was thinking about checking it out, but figured this could save me the time/cd.

so, what is the main difference?

My understanding is the server edition has no GUI, so if you start it up, you'll just have a command line. It's used for people who run a server from a dedicated computer and don't need a GUI, etc that use resources. I think some people like to sort of customize their Ubuntu from the ground up using the server edition because it is bare bones and you can install only the packages you want.

Most people would probably suggest using the standard desktop edition (I do).

---

### Post by edd07 on 2008-06-26
The main difference is that the server doesn't have a graphical user interface installed by default. So you have to use the command line or control it remotely. Also, I think Apache, MySQL and PHP packages are in the CD, while in the desktop edition, you have to get them from the repos.

---

### Post by wdaniels on 2008-06-26
The main differences lie with the installation and the kernel. The installer will give you options to install typical server software (e.g. LAMP stack) rather than a desktop GUI. The kernel is tuned for acting as a sever rather than running an interactive desktop session, which amounts to using a different scheduler (Deadline I/O scheduler instead of CFQ), turning off pre-emption, lowering the timer interrupt, PAE support...etc.

Most of the configuration differences are for high-end/high-load servers, not really your average home server. Basically, if you want to use a graphical desktop, use the desktop edition, otherwise use the server edition. The only reason to use the server kernel on a desktop that I can think of is for PAE support, to address more than 4GB RAM under 32-bit.

---

### Post by pavel989 on 2008-06-26
thanks for the quick replies everyone. the reason i was asking is because i have an old desktop, which im pretty sure used to be a server back in its day, and i wanted to set it up as a home server sort of thing. So i guess im sticking with the standard ubuntu. thanks!

---

