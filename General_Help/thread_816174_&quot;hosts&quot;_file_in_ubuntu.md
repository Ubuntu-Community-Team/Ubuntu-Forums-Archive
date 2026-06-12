---
title: "&quot;hosts&quot; file in ubuntu?"
date: 2008-06-02
forum: General Help
---

### Post by souldances on 2008-06-02
is there a "hosts" file in ubuntu like micros**t has, where domain names can be referenced to the localhost address?  i apologize if i'm using micros**t terminology here...  i was able to text edit a file named 'hosts' and add domain names of annoying banner and pop-up ad content providers and the like and basically 'trick' the computer into only looking on the computer itself, not the network or internet.  instead of dancing gorillas or some other annoying crap, the banner would display a 'server not found' message - much more palatable.  the file could also reference the actual numeric address of commonly accessed sites, speeding the access time considerably.  i'd like to utilize this with ubuntu, but don't know what to look for or where to look...  any help would be much appreciated.  thanks in advance - alan

---

### Post by babylon2233 on 2008-06-02
```
sudo gedit /etc/hosts
```

it located in /etc/ directory

---

### Post by souldances on 2008-06-02
yay!  thank you.  and even better for me, i discovered two firefox extensions that will likely eliminate most of my frustrations and allow me to only use the hosts file for speeding up access to commonly visited sites - noscript and noflash.  woohoo!  <dances off singing the 'happy, happy, joy, joy' song...>

---

### Post by Nesman on 2008-06-02
I'm pretty sure that the hosts file that Microsoft uses is just stolen from Unix anyway.  If you notice, it's in system32\drivers**\etc\hosts**.

I use my host file to map internal addresses for my LAN and use AdBlock in Firefox.
If slow DNS requests are an issue for you, you might want to try 4.2.2.2 and 4.2.2.3 for DNS servers, or [http://www.opendns.com/](http://www.opendns.com/) .  Your ISP must have crappy DNS service if it's something that you noticed.  I try not to use my hosts file for outside sites because of the confusion it causes if their ip address ever changes.  My wife never sees the humor in things like that when it keeps her offline for a few hours because I did something silly. ;)

Using your /etc/hosts for outside sites can be usefull, however, if you're doing webdesign.  It's an easy way to access the site via domain while actually viewing your test server.  Helps you to make sure your links all work correctly and you don't have any images that break before you go live.  Just remember to remove the entry when you're done.

---

### Post by kerry_s on 2008-06-02
> **Nesman said:**
> I'm pretty sure that the hosts file that Microsoft uses is just stolen from Unix anyway.  If you notice, it's in system32\drivers**\etc\hosts**.

I use my host file to map internal addresses for my LAN and use AdBlock in Firefox.
If slow DNS requests are an issue for you, you might want to try 4.2.2.2 and 4.2.2.3 for DNS servers, or [http://www.opendns.com/](http://www.opendns.com/) .  Your ISP must have crappy DNS service if it's something that you noticed.  I try not to use my hosts file for outside sites because of the confusion it causes if their ip address ever changes.  My wife never sees the humor in things like that when it keeps her offline for a few hours because I did something silly. ;)

Using your /etc/hosts for outside sites can be usefull, however, if you're doing webdesign.  It's an easy way to access the site via domain while actually viewing your test server.  Helps you to make sure your links all work correctly and you don't have any images that break before you go live.  Just remember to remove the entry when you're done.

hey, i thought i was the only one who used the 4.2.2.# over opendns. :lolflag:

---

### Post by x1a4 on 2008-06-02
> **Nesman said:**
> I'm pretty sure that the hosts file that Microsoft uses is just stolen from Unix anyway.  If you notice, it's in system32\drivers**\etc\hosts**.

Yup.  That's a remnant of microsmeg's feeble attempt to make DOS more like UNIX back in the day.  An attempt they abandoned after realising they actually had to know what the heck they're doing.

---

### Post by babylon2233 on 2008-06-02
It seems AdBlock Plus plugin can give you problem if you have java plugin installed.

---

