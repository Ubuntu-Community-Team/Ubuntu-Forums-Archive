---
title: "mutt's postfix dependancy"
date: 2006-10-03
forum: General Help
---

### Post by vrajgh on 2006-10-03
Hello

I'm new to ubuntu and am going through the process of setting up my system "as I like it." Because I use email all the time, I am rather fussy about how it is set up and am looking for some help getting it just right.

On my previous system, I used a combination of mutt, procmail, fetchmail and nbsmtp. I've never really needed anything as powerful as postfix in order to manage my email. I want to replicate that setup because configuring mutt will then be as simple as copying my previous muttrc into my new home directory.

The ubuntu package list for mutt ([http://packages.ubuntulinux.org/dapper/mail/mutt](http://packages.ubuntulinux.org/dapper/mail/mutt)) lists postfix as a dependancy but also lists the "mail-transport-agent" virtual package as an alternative. Following this link gives a number of alternatives to postfix, including ssmtp which could do the same job that nbsmtp is doing on my current system. I've spent some time "googling" and reading man pages but have been unable to determine how to tell the package manager to install something like ssmtp instead of postfix. Is this level of control actually possible with the package management system? (I am assuming it is, otherwise there would seem little point listing alternatives on the website!)

Any hints in the right direction would be most appreciated.

---

### Post by andrew.46 on 2007-07-02
Hi,

 Hmmmmm.... that is a slightly old post but I have actually created just such a guide:

[http://people.aapt.net.au/~adjlstrong/mutt.html](http://people.aapt.net.au/~adjlstrong/mutt.html)

                                   Andrew

---

