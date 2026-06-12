---
title: "Configuring Postfix with clamSMTP"
date: 2005-05-05
forum: General Help
---

### Post by sgarman on 2005-05-05
I'm trying to configure Postfix to work with ClamAV on my Ubutnu Hoary mailserver. clamSMTP is a transparent SMTP proxy designed to scan mail using ClamAV and work with Postfix. The instructions for setting this up are fairly simple:

[http://memberwebs.com/nielsen/software/clamsmtp/postfix.html](http://memberwebs.com/nielsen/software/clamsmtp/postfix.html)

However, Ubuntu Hoary runs Postfix in a chroot (jail) environment, so this particular configuration note applies:

[http://memberwebs.com/nielsen/freebsd/jails/docs/jail_postfix.html](http://memberwebs.com/nielsen/freebsd/jails/docs/jail_postfix.html)

I need to know what "jail IP" postfix is using, but I am not too familiar with chrooted environments and I don't know how to determine this. Can someone enlighten me? Even some pointers to gentle documentation on the chrooted environments that Ubuntu uses would be welcome. 

Many thanks! Ubuntu is amazing.

Scott

---

### Post by blueplazma on 2005-05-05
When you say "jail" IP do you mean the IP address postfix is running on?  If that's all you mean, and assuming you only have one network connection, it's the IP address assigned to eth0.  You can check that with ```
ifconfig eth0
```  Good luck with your project.  I'm using postfix/Amavis right now and it was pretty easy to set up, but I hope yours works well too.

---

