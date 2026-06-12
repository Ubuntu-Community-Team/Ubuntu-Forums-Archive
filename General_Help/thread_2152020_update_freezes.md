---
title: "update freezes"
date: 2013-06-06
forum: General Help
---

### Post by danielsender on 2013-06-06
Hi,

I have 13.04 running on a 32b Dell machine. On the last update it stops with the message:


```

...
Setting up rsyslog (5.8.11-2ubuntu2.2) ...
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd

```

So I purged/removed rsyslog and re-installed, but it keeps stopping at the same place.
Can some guru tell me what should I do to complete the update?

Thanks.

Daniel

---

### Post by dino99 on 2013-06-06
open a terminal, and run:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get -f install
sudo dpkg --configure -a

---

### Post by danielsender on 2013-06-06
> **dino99 said:**
> open a terminal, and run:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get -f install
sudo dpkg --configure -a

Is not working, when I do "sudo apt-get autoclean" or any of the following steps you wrote, it asks me first to run "dpkg --configure -a", so if type that then it freezes exactly at the place I mentioned in my first posting.

---

### Post by redmk2 on 2013-06-06
> **danielsender said:**
> Hi,

I have 13.04 running on a 32b Dell machine. On the last update it stops with the message:


```

...
Setting up rsyslog (5.8.11-2ubuntu2.2) ...
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd

```

So I purged/removed rsyslog and re-installed, but it keeps stopping at the same place.
Can some guru tell me what should I do to complete the update?

Thanks.

Daniel

My suspicion is that some of the permissions in /var have been changed.  The error is saying that it can't setup syslog and it is skipping the apparmor profile.  Did you modify the systems permissions in any way?

---

### Post by danielsender on 2013-06-06
> **redmk2 said:**
> My suspicion is that some of the permissions in /var have been changed.  The error is saying that it can't setup syslog and it is skipping the apparmor profile.  Did you modify the systems permissions in any way?

Not at all - If you tell me what permissions for relevant files/folders should be, I can compare them.

---

### Post by redmk2 on 2013-06-06
> **danielsender said:**
> Not at all - If you tell me what permissions for relevant files/folders should be, I can compare them.

The permissions are listed here: /etc/apparmor.d/usr.sbin.rsyslogd

But if you haven't touched the permissions then it's really not relevant.  i wonder if there is a bug then.  I'm using 12.04LTs and I've not had a problem with rsyslog from 8.04 onwards.

---

### Post by danielsender on 2013-06-06
> **redmk2 said:**
> The permissions are listed here: /etc/apparmor.d/usr.sbin.rsyslogd

But if you haven't touched the permissions then it's really not relevant.  i wonder if there is a bug then.  I'm using 12.04LTs and I've not had a problem with rsyslog from 8.04 onwards.

Before your reply I compared the permissions of /var on the system in question with another similar working system (on a different Dell machine) and they are the same. My question now is where is it getting stuck?

---

### Post by danielsender on 2013-06-06
> **danielsender said:**
> Before your reply I compared the permissions of /var on the system in question with another similar working system (on a different Dell machine) and they are the same. My question now is where is it getting stuck?

There was another posting with exactly the same issue: [http://ubuntuforums.org/showthread.php?t=2151632](http://ubuntuforums.org/showthread.php?t=2151632)

I followed the directions (kill the rsyslogd process manually) and it completed. Let's see if there is any other related issue later.

Thanks.

Daniel

---

