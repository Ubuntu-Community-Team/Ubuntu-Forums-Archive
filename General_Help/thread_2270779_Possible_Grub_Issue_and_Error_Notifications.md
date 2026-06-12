---
title: "Possible Grub Issue and Error Notifications"
date: 2015-03-25
forum: General Help
---

### Post by oaxacamatt1 on 2015-03-25
I am running Xubuntu 14.04.02 on a very standard Gateway (NV51B08u).  

I have a question that first needs investigation.  Let me explain.  I have recently been getting error notifications and requests from Xubuntu to send fault errors to the 'mothership'.  I have been sending these messages and at times even putting in root password to complete the error message process.  The need for a root password to send off grub error messages sounds strange to me...  I have looked at the error notification as much as I can to find out the problem but with little success.  

There fore I want to investigate the error messages more thoroughly and find out what the matter is but do not know where or how to start?  I hope this makes sense to someone... 

Any help would be appreciated.

---

### Post by dino99 on 2015-03-25
what do you mean ? is it a crash ? or some popup errors ? which ones ?

---

### Post by kc1di on 2015-03-25
Hello oaxacamatt1, 

Couple of things.  It asks for your root password because some of the files it needs to send to the developers come from your root file system. 

most crash reports are store in /var/crash folder you may also want to look in the /var/log folder if you know the specific program or function that's causing the crash there may be and indication in it's log file of what went wrong.  

In any event your bug reports should generate a bug on lunchpad and also send you a report via e-mail if your signed up for launchpad then you can track it there. 

good luck ;)

---

### Post by Dennis N on 2015-03-25
I have seen a number of those apport notifications (most recently yesterday), and usually if you continue and complete the process, you are sent to Launchpad to login (or create an new account) to view a bug page that was automatically created. You can add any details you wish to. All the supporting reports that were collected by apport are there as attachments. You also should get an email at the address you registered with your account on Launchpad. 

However, a few times, this whole process did not seem to complete for me - at least I was not sent to Launchpad page at all.

---

### Post by slickymaster on 2015-03-25
> **oaxacamatt1 said:**
> <---snip---> 

I have a question that first needs investigation.  Let me explain.  I have recently been getting error notifications and requests from Xubuntu to send fault errors to the 'mothership'.  I have been sending these messages and at times even putting in root password to complete the error message process.  The need for a root password to send off grub error messages sounds strange to me...  I have looked at the error notification as much as I can to find out the problem but with little success.  
<---snip---> 

Those are the apport notifications. Apport intercepts program crashes, collects debugging information about the crash and the operating system environment, and sends it to bug trackers in a standardized form. It also offers the user the ability to report a bug about a package, with again collecting as much information about it as possible.

---

### Post by pmi2 on 2015-03-25
> **Dennis N said:**
> ...not sent to Launchpad page at all.Same here, I've never even seen an automatic redirect to Launchpad, even once.
Until now I was just frustrated... now I feel neglected, too... :( (chuckle)

---

