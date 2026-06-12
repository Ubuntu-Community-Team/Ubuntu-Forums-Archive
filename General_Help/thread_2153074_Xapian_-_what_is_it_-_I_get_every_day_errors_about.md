---
title: "Xapian - what is it? - I get every day errors about it"
date: 2013-06-10
forum: General Help
---

### Post by ELMIT on 2013-06-10
Every day my system pops up a message, that it got an internal error, ... 

The message is update-apt-xapian-index has stopped

what is it? what does it do?

How to fix it?

---

### Post by ELMIT on 2013-06-10
????

> sudo update-apt-xapian-index
[sudo] password for ronald: 
No handlers could be found for logger "softwarecenter.db.update"
Reading .desktop files from /usr/share/app-install/desktop/: done.  
Traceback (most recent call last):
  File "/usr/sbin/update-apt-xapian-index", line 101, in <module>
    if not indexer.setupIndexing(force=opts.force, system=opts.pkgfile is None):
  File "/usr/lib/python2.7/dist-packages/axi/indexer.py", line 518, in setupIndexing
    addon.obj.init(dict(values=self.values), self.progress)
  File "/usr/share/apt-xapian-index/plugins/cataloged_time.py", line 72, in init
    self._package_cataloged_time = cPickle.load(open(self._packages_cataloged_file))
cPickle.BadPickleGet: 84


---

### Post by dino99 on 2013-06-10
I am from the government, I am here to help you! Just ask!
And don't expect more to be happen than with any other government!

i feel its true  ):P

---

### Post by vasa1 on 2013-06-10
> **ELMIT said:**
> ????
I'm not sure that users are required to run "sudo update-apt-xapian-index". I think it's one of those automatic (cron?) things, which, unless one really knows what one is doing, is not to be fiddled with.

---

### Post by ELMIT on 2013-06-10
I run it so,because automatically it gives me each day an system error, ... so I wanted to know what causes that. More important how to stop it, ...

---

### Post by oldos2er on 2013-06-10
Threads merged. Please don't open more than one thread for the same or similar questions, it's confusing and it dilutes community effort, in addition to being contrary to the Code of Conduct: Do not cross post, or post the same thing in multiple locations.

---

