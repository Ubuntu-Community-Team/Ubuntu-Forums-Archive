---
title: "firestarter - cannot reach google"
date: 2005-09-02
forum: General Help
---

### Post by 5-HT on 2005-09-02
Hi, having a strange situation and was wondering if someone may be able to help me out.

For the past three days, I haven't been able to reach google.

I've narrowed it down to something to do with firestarter (even thought google may be down at first, but got there non-cached on another pc).

When it's disabled I can reach the site no problem, but once enabled Firefox just hangs trying to connect to the site.

It's funny because after I installed and setup firestarter, there was no problem reaching google, this problem's just a recent one.

I've made sure google isn't blacklisted within firestarter's configuration, and I don't seem to have a problem with any other site at all.

I also checked my hosts.deny file which is clean

I've tried purging firestarter and reinstalling (even deleting the .deb and downloading again) but still having the same issue.

I tried to ping the site but for some reason or another I can't ping out at all either from the GUI or CLI (I've noticed this right after the ubuntu install, but it shouldn't be affecting my current problem).

I have noticed one thing though (mostly likely not causing the problem, but it's the only other thing I can think of). After reinstalling the program, I still see the list of events firestarter has intercepted (thought it would have been deleted when firestarter was purged). Anyone know where that list is kept (I tried a search, but came up empty)?

Anyone have any ideas? 
Thanks for any help.

---

### Post by KingBahamut on 2005-09-02
Open port 80 for everyone in the ruleset. 

Firestarter isnt permissive by default, you have to add rules for everything.

---

### Post by 5-HT on 2005-09-02
Thanks for the reply.

I've tried both using the restrictive option with port 80 allowed for everyone as well as switching over to the permissive option, but still unable to get to google.

It's weird as other sites seem to be ok, and if there were something going on with firestarter and port 80 I'd expect all sites to be affected...but then again turning off firestarter solves the issue so it's causing some kind of conflict.

---

### Post by arnieboy on 2005-09-02
[QUOTE=5-HT]Hi, having a strange situation and was wondering if someone may be able to help me out.

For the past three days, I haven't been able to reach google.

I've narrowed it down to something to do with firestarter (even thought google may be down at first, but got there non-cached on another pc).

When it's disabled I can reach the site no problem, but once enabled Firefox just hangs trying to connect to the site.

It's funny because after I installed and setup firestarter, there was no problem reaching google, this problem's just a recent one.

I've made sure google isn't blacklisted within firestarter's configuration, and I don't seem to have a problem with any other site at all.

I also checked my hosts.deny file which is clean

I've tried purging firestarter and reinstalling (even deleting the .deb and downloading again) but still having the same issue.

I tried to ping the site but for some reason or another I can't ping out at all either from the GUI or CLI (I've noticed this right after the ubuntu install, but it shouldn't be affecting my current problem).

I have noticed one thing though (mostly likely not causing the problem, but it's the only other thing I can think of). After reinstalling the program, I still see the list of events firestarter has intercepted (thought it would have been deleted when firestarter was purged). Anyone know where that list is kept (I tried a search, but came up empty)?

Anyone have any ideas? 
Thanks for any help.[/QUOTE]

do a 
```
sudo gedit /etc/firestarter/events-filter-hosts
```
and make sure it does not include the following ip address:
> 216.239.39.99
if it does, delete that entry, save and exit and restart firestarter.

---

### Post by 5-HT on 2005-09-03
[QUOTE=arnieboy]do a 
```
sudo gedit /etc/firestarter/events-filter-hosts
```
and make sure it does not include the following ip address:  216.239.39.99

if it does, delete that entry, save and exit and restart firestarter.[/QUOTE]

Looked under the events-filter-hosts file, but that IP was not listed there, also looked around the other files in the /etc/firestarter directory (events-filter-ports, inbound, outbound, configuration, non-routables) and found that they were all blank.

I'll try doing a fresh install of ubuntu as I'm out of ideas, and see if that takes care of the problem as this seems really wierd in that nothing about firestarter seems to be blocking the site...but blocked it is.

Thanks for the help though.

---

### Post by arnieboy on 2005-09-03
[QUOTE=5-HT]Looked under the events-filter-hosts file, but that IP was not listed there, also looked around the other files in the /etc/firestarter directory (events-filter-ports, inbound, outbound, configuration, non-routables) and found that they were all blank.

I'll try doing a fresh install and see if that takes care of the problem as this seems really wierd in that nothing about firestarter seems to be blocking the site...but blocked it is.

Thanks for the help though.[/QUOTE]
dont do a fresh install.
just do the following:
```
sudo apt-get remove firestarter
sudo rm -rf /etc/firestarter
sudo apt-get install firestarter
```
see if this solves your problem or not.

---

### Post by 5-HT on 2005-09-03
Ha...that did it. Thanks a lot (saves me a reinstall of the os).

Previously I tried purging firestarter through aptitude, doing a reboot and reinstall, only ending up with the problem again.

I noticed that if I purge instead of uninstall that took care of /etc/firestarter.

This time following your advice, an uninstall through apt and removal of the directory seemed to do the trick.

---

### Post by 5-HT on 2005-09-04
Well I was a little premature in declaring the problem solved.
It's back again today.

After doing some investigation I did find out what was happening and how to fix it.

This may be an issue for a lot of people running firestarter (1.01) not being able to go to certain sites even though they're not blacklisted.

In /etc/firestarter there's a list of non-routable IP's in a file aptly called non-routables.

For some reason or another, this list encompasses more than the normal private IPblock range and extends into public IP's.

It seems as if the google servers I can connect to (google's funny in that no matter which server you try to connect to, it'll automatically bring you to the closest one) started recently using different IP's which were included in that non-routable list.

Firestarter 1.0.2 has the list disabled by default, but in 1.0.1 it's automatically enabled.

In order to get around the block, all you need to do is find out the IP address of the site you can no longer get to (nslookup or similar), and comment out that subnet in the non-routables list.


Hope this helps if anyone else has a problem like this.

---

### Post by bryan986 on 2005-10-07
ahhh! thanks for this....I could not get to google and all, it was wierding me out

I had to comment out the "72.0.0.0/8" line for it to work...

---

### Post by 5-HT on 2005-10-10
[QUOTE=bryan986]ahhh! thanks for this....I could not get to google and all, it was wierding me out

I had to comment out the "72.0.0.0/8" line for it to work...[/QUOTE]

Glad it was of help to someone.

The non-routables list is commented out in newer versions of firestarter, so hopefully this shouldn't be a problem in Breezy 
(then again, it's not hard by any means to fix, but took a little time to figure out- I'd never guess that firestarter would consider valid public ip's as being non-routable).

---

