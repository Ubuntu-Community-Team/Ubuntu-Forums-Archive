---
title: "Evolution unable to compose email"
date: 2008-06-02
forum: General Help
---

### Post by HereInOz on 2008-06-02
Hi All,

I have a couple of machines running Hardy, set up to use Microsoft Exchange for email services.  Last week it was all working fine but today, when we try to compose an email, we get the composer window for a short while, and then the whole application goes grey, and we have to force quit.

We are able to connect to the Exchange server, read our mail, and all those things, but we are unable to compose an email.  Anyone got any thoughts on this?

---

### Post by cmnorton on 2008-06-02
Look in /var/log/messages, /var/log/syslog, and also post this as a bug in Ubuntu Launchpad [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

---

### Post by d2ortiz on 2008-06-02
I have the same problem. The problem start to occur after may 30 update

---

### Post by HereInOz on 2008-06-03
The real tragedy was that I needed to get this machine up and running by the following morning, so it was back to Gutsy for the moment, and all is well.  So I cannot post the log message now.  

Hopefully I will have the time and machine availability to re-install Hardy on a machine and test it on the domain.  Priorities always intervene, unfortunately :(

Thanks for your assistance.  I agree with d2ortiz, it worked one week, then didn't work the next week.  Probably update related.

---

### Post by rasto1968 on 2008-06-03
I'm also having the same problem, last week everything was fine and now I can't compose emails or view calendar entries without evolution locking up ! I even resorted to building my own from the source but still get the same problem. Evolution is now unusable for me :(

Edit: have just checked in /var/log/messages and /var/log/syslog and they show nothing unusual happening.

Rob

---

### Post by leemid on 2008-06-03
Hi HereInOz,
A friend of mine had exactly the same problem at the weekend. I was actually fixing something else for him, so I'm not sure if this will work for you, but when I booted the machine using the original 2.6.24-16 kernel, the problem went away and Evolution worked properly again.

I used startupmanager to change the default kernel and haven't noticed a problem since.
Hope that helps!

---

### Post by cmnorton on 2008-06-03
> **HereInOz said:**
> The real tragedy was that I needed to get this machine up and running by the following morning, so it was back to Gutsy for the moment, and all is well.  So I cannot post the log message now.  

Hopefully I will have the time and machine availability to re-install Hardy on a machine and test it on the domain.  Priorities always intervene, unfortunately :(

Thanks for your assistance.  I agree with d2ortiz, it worked one week, then didn't work the next week.  Probably update related.

If you've dropped back to the prior release, I suggest waiting for the early July 8.04.1 point release.

---

### Post by ephro on 2008-06-03
If you install the package apt source located here:

[https://launchpad.net/~zulcss/+archive](https://launchpad.net/~zulcss/+archive)

and run an update everything should work again. There is a bug in OpenLDAP that is causing all the problems.


ephro

---

### Post by HereInOz on 2008-06-03
Thanks ephro.  I have already gone back to Gutsy for the moment, so I think I will leave it at that.  It is a client's machine, so I will let them settle down a little before I have another go at it.

Thank you for the link.  I am guessing that by the time I get to re-install Hardy on the offending computer, the fix will have been integrated into the program, however, I shall keep the link - you never know what may happen.

---

### Post by rasto1968 on 2008-06-05
> **ephro said:**
> If you install the package apt source located here:

[https://launchpad.net/~zulcss/+archive](https://launchpad.net/~zulcss/+archive)

and run an update everything should work again. There is a bug in OpenLDAP that is causing all the problems.


ephro

I've just tried this and it doesn't fix the problem for me.

Rob

---

### Post by rasto1968 on 2008-06-05
> **leemid said:**
> Hi HereInOz,
A friend of mine had exactly the same problem at the weekend. I was actually fixing something else for him, so I'm not sure if this will work for you, but when I booted the machine using the original 2.6.24-16 kernel, the problem went away and Evolution worked properly again.

I used startupmanager to change the default kernel and haven't noticed a problem since.
Hope that helps!

Just tried switching to 2.6.24-16 and this didn't work for me.

Rob

---

### Post by rasto1968 on 2008-06-09
Just out of interest for the other people with this problem, which GFX cards are you using ? Mine is an ATI 1300.

I ask this as I think that one of the other items that changed recently was a new ATI driver - maybe this is the thing causing the problem ?

Rob

---

### Post by rasto1968 on 2008-06-09
I finally got it working, the problem was caused by the Global Catalogue Server Name entry being empty in the 'Receiving Options' tab for the mail accounts settings. Adding the name of the server stopped Evolution from locking up. I still find it pretty shocking that something as simple as this could cause a hard lockup.

Rob

---

### Post by varaonaid on 2008-06-25
OK, I've been having the exact same problem.  I can also confirm that it's the GAL issue.  Problem is for me, I don't have a GAL server or use one so that makes it more tricky.

To attempt to get around that, I changed my "Limit number of GAL queries" (or something similar) under the options for that exchange account to 1, which was the lowest that it allowed.  I also made sure that GAL was unchecked in the autocomplete section.

The result is, instead of graying out and locking up indefinitely, it grays out for about 15 seconds (presumably while it's trying to contact a GAL that isn't there).  Then, the composer window and evolution windows come back to life and I can continue on my merry way.

If anyone knows of a better solution, I'm all ears because it's wicked annoying to be stuck each time you write an email for 15-30 seconds while evolution freaks out.  I wish the developers would add an option to completely disable the GAL.  If there already is one, please tell me how to disable it.

Hope that helps someone out...

---

