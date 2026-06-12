---
title: "Retain *all* archives of /var/log/apt/history.log"
date: 2015-01-10
forum: General Help
---

### Post by vasa1 on 2015-01-10
I want to retain all archived versions of */var/log/apt/history.log* because I would like to have a record of what I installed and uninstalled over time.

*/etc/logrotate.d/apt* has this:```
/var/log/apt/term.log {
  rotate 12
  monthly
  compress
  missingok
  notifempty
}

/var/log/apt/history.log {
  rotate 12
  monthly
  compress
  missingok
  notifempty
}


```I'm using Lubuntu 14.04 LTS which should be supported for three years. So would increasing **rotate 12** to **rotate 36** make sense?

And because */etc/logrotate.d/apt* is a system file, is there a chance that any change I make can be over-written if the logrotate package is updated?

---

### Post by Lars Noodén on 2015-01-10
That's probably the only way to do it currently.    If  "rotate" is set to zero, old versions are deleted rather than rotated.  If I could hack C, I would 
modify logrotate to allow "rotate" to be set to -1 to allow unlimited rotations.  Maybe one extra, 37, just to be sure.

---

### Post by vasa1 on 2015-01-10
> **Lars Noodén said:**
> That's probably the only way to do it currently.    If  "rotate" is set to zero, old versions are deleted rather than rotated.  If I could hack C, I would 
modify logrotate to allow "rotate" to be set to -1 to allow unlimited rotations.  Maybe one extra, 37, just to be sure.Thanks for replying!

But what are your thoughts about the possibility of */etc/logrotate.d/apt* being overwritten if logrotate is updated? Or will I just have to check what happens if logrorate is updated during the life of Lubuntu 14.04 LTS?

---

### Post by Lars Noodén on 2015-01-10
In 14.04 it looks like [logrotate](http://packages.ubuntu.com/trusty/logrotate) hasn't been updated yet so I can't guess based on it so far.   
I looked at 12.04, too, but it has not had a more recent version of logrotate backported, it seems to have been left with the old version.  So there's not a way to test.  But the package maintainer is listed as: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
So maybe that would be the place to find out for sure what the practice is, should the package get an update during the next 3 years.

---

### Post by vasa1 on 2015-01-10
I'm thinking that one admittedly weird way to track when logrotate is updated would be to put a "hold" on it.
```
echo "logrotate hold" | sudo dpkg --set-selections
```
Whenever an update to logrotate is available, the output of *apt-get dist-upgrade* will inform me that one package has been held back. Then I can "unhold" it with```
echo "logrotate install" | sudo dpkg --set-selections
```and check if */etc/logrotate.d/apt* has been modified as a result of the update.

---

### Post by Lars Noodén on 2015-01-10
That might do it.  But you might not need the second modification.  apt-get should allow  *--ignore-hold* to override any holds, but then that would steam roll over more than just logrotate if you have other holds.

---

### Post by vasa1 on 2015-01-10
> **Lars Noodén said:**
> That might do it.  But you might not need the second modification.  apt-get should allow  *--ignore-hold* to override any holds, but then that would steam roll over more than just logrotate if you have other holds.
Thanks, I didn't know about *--ignore-hold* but as you point out, it isn't selective. I don't plan on holding any other packages at this time but who knows.

I'll mark this [SOLVED] now.

---

