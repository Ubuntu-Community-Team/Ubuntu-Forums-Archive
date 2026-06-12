---
title: "Grep a Range of IP's out of a text file AKA I Suck @ Grep"
date: 2008-02-27
forum: General Help
---

### Post by shimmyt on 2008-02-27
I was given the task of going through an http log file and I was asked to find all of the IP's that matched: 192.168.148 - 155.x. I could not find a simple way to do this in grep. From what I was reading adn what was outputing I would get anything that had a combination of those 6 numbers which I did not want. Any help would be appreciated.

---

### Post by Fire_Chief on 2008-02-27
> **shimmyt said:**
> I was given the task of going through an http log file and I was asked to find all of the IP's that matched: 192.168.148 - 155.x. I could not find a simple way to do this in grep. From what I was reading adn what was outputing I would get anything that had a combination of those 6 numbers which I did not want. Any help would be appreciated.

Well the good news is it can be done in a straightforward manner...the bad news is the only way I know to do it is to search for each subnet match one at a time. For example```
cat *logfile* | grep 192.168.148
cat *logfile* | grep 192.168.149
cat *logfile* | grep 192.168.150
etc
```
A little tedious but not a terrible way to do it for that few number of searches. Sorry I don't have a better method at the moment (though it may very well exist and I just don't know what it is).

Cheers,
Fire_Chief

---

### Post by astrotech226 on 2008-02-27
egrep is a little more suited for this type of thing:

egrep '192.168.1(48|49|50|51|52|53|54|55)' logfile

---

