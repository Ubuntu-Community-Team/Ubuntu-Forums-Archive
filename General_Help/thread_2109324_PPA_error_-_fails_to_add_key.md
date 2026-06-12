---
title: "PPA error - fails to add key"
date: 2013-01-27
forum: General Help
---

### Post by heyup on 2013-01-27
I'm using Precise 12.04 classic no effects.

When I try to add a PPA e.g.
 
```
sudo add-apt-repository ppa:nilarimogard/webupd8
```

I get this error:

> Exception in thread Thread-1: 
Traceback (most recent call last): 
  File "/usr/lib/python2.7/threading.py", line 551, in __bootstrap_inner 
    self.run() 
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 99, in run 
    self.add_ppa_signing_key(self.ppa_path) 
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 132, in add_ppa_signing_key 
    tmp_keyring_dir = tempfile.mkdtemp() 
  File "/usr/lib/python2.7/tempfile.py", line 322, in mkdtemp 
    name = names.next() 
  File "/usr/lib/python2.7/tempfile.py", line 141, in next 
    letters = [choose(c) for dummy in "123456"] 
  File "/usr/lib/python2.7/random.py", line 274, in choice 
    return seq[int(self.random() * len(seq))]  # raises IndexError if seq is empty 
ValueError: cannot convert float NaN to integer 

Same thing happens if a try other launchpad.net PPAs. The PPA gets listed in Software Sources, but no key is added.

Any ideas what is causing this error, and how to stop it?

---

### Post by ibjsb4 on 2013-01-27
I too am running 12o4 classic no effects and install ppa:nilarimogard/webupd8 without issue.

Since your having issues with other ppa's I wonder if reinstalling python2.7 would help any.

And on a side note I expected to see changes after installing that ppa and I see nothing.  Whats with that?

---

### Post by heyup on 2013-01-27
> **ibjsb4 said:**
> 
Since your having issues with other ppa's I wonder if reinstalling python2.7 would help any.

Tried reinstalling both python2.7 and python-software-properties but this made no difference. I get the same error. 

What is odd is that I'm testing this on a fresh install of Precise 12.04 Classic No Effects.

A web search revealed same error here [http://blogs.bu.edu/mhirsch/2012/08/octave-3-6-on-ubuntu-12-04/]("http://blogs.bu.edu/mhirsch/2012/08/octave-3-6-on-ubuntu-12-04/")
but nowhere else.

---

### Post by ibjsb4 on 2013-01-27
Your link doesn't work, but I did find this

[http://bugs.python.org/issue13986](http://bugs.python.org/issue13986)

here

[https://www.google.com/search?client=ubuntu&channel=fs&q=ValueError%3A+cannot+convert+float+NaN+to+integer+&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=ValueError%3A+cannot+convert+float+NaN+to+integer+&ie=utf-8&oe=utf-8)

---

### Post by heyup on 2013-01-27
> **ibjsb4 said:**
> Your link doesn't work, but I did find this

[http://bugs.python.org/issue13986](http://bugs.python.org/issue13986)

here

[https://www.google.com/search?client=ubuntu&channel=fs&q=ValueError%3A+cannot+convert+float+NaN+to+integer+&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=ValueError%3A+cannot+convert+float+NaN+to+integer+&ie=utf-8&oe=utf-8)

I have edited the link, it should now work.

I did see those bug reports when I did a web search, but I don't think they are related to adding a PPA.

---

### Post by ibjsb4 on 2013-01-27
And your fully updated?

Might even try

```
sudo apt-get dist-upgrade
```

---

### Post by heyup on 2013-01-27
Sorry. 

Found the bug reports relating to adding PPAs:
[https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1063350]("https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1063350")

[https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1065868]("https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1065868")

---

### Post by ibjsb4 on 2013-01-27
> downgrading python-software-propertiesLooks like you have some hope.

Good luck

---

### Post by heyup on 2013-01-27
Downgrading python-software-properties to version 0.82.7 worked for me.

```
apt-get install python-software-properties=0.82.7
```

Thank you for your help.

---

