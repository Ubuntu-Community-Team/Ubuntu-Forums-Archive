---
title: "Elisa Issues..."
date: 2007-12-23
forum: General Help
---

### Post by lunarcloud on 2007-12-23
It used to be installable, but I uninstalled i, and now the whole elisa repo doesn't seem to work!

```
W: GPG error: http://elisa.fluendo.com gutsy Release: The following signatures were invalid: BADSIG 7096EDEA5B4E69BB Philippe Normand <philippe@fluendo.com>
W: You may want to run apt-get update to correct these problems

```I don't get it.

apt-key list shows this 
```

pub   1024D/5B4E69BB 2007-08-31
uid                  Philippe Normand <philippe@fluendo.com>
sub   2048g/5386A6DA 2007-08-31
```My source looks like this

```
##### Elisa #####
## sudo wget http://elisa.fluendo.com/packages/philn.asc -O - | sudo apt-key add -
deb http://elisa.fluendo.com/packages gutsy main
```
Please help? Any ideas?

---

### Post by Jazman on 2007-12-24
I can't offer any help now - because I've got the same problem.  It happened two days ago when I applied some new ubuntu gutsy updates that included elisa. 

Synaptic gives this error
An error occured The followingf details are provided:
W: GPG error: [http://elisa.fluendo.com](http://elisa.fluendo.com) gutsy Release: The following signatures were invalid: BADSIG 7096EDEA5B4E69BB Philippe Normand <philippe@fluendo.com>

Two versions are shown: elisa0.3.2.1-3ubuntu1 and elisa-extra0.3.2.1-3ubuntu1.
I've tried installing both - each fails.  From the Applications -> Sound and Video -> Elisa Media Center both die.  From the command line both fail after spitting out a string of python related errors.  If I knew if it would be helpful I would list those error messages.

When I try to revert to the elisa listed in the ubuntu gutsy repository elisa_0.3.2-0ubuntu1_all.deb that version too fails with a string of python errors.

I'm now inclined to think that maybe another ubuntu gutsy update is the culprit.  One of my network interfaces is showing an error: The interface does not exist.

I'm tempted to go to the fluendo elisa form and post this problem.  I want elisa back.

---

### Post by Jazman on 2007-12-25
I think I fixed it - at least it now works.  From the Synaptic updates I applied

elisa-extra (version 0.3.2.1-3ubuntu1) will be upgraded to version 0.3.2.1-4ubuntu1
libpigment0.3-1 (version 0.3.2.1-4ubuntu1) will be upgraded to version 0.3.2.1-5ubuntu1
python-pigment (version 0.3.2.1-4ubuntu1) will be upgraded to version 0.3.2.1-5ubuntu1

Also some self-education on my part about the elisa conf file as found in the source code under sample_config shows different configs - the raval.conf seems to be a good starting point.  AAMOF it may have been the conf file that was messed up in the first place that was the problem.

---

