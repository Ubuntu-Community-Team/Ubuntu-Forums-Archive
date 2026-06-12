---
title: "Firefox is SLLLOOOWWWW!"
date: 2005-05-31
forum: General Help
---

### Post by astronerd on 2005-05-31
Hi all, I have been having problems with firefox being very very slow at loading pages.  I have a fast wifi connection(at least I think so....)  and IE is very fast on my XP side, but firefox and downloads are really slow in ubuntu.  Is anyone experiencing this, and is there a way to speed things up?  I havent upgraded to the newest version of firefox, was waiting for it to get on the repos, but will that help?  Any ideas are appreciated.....  Thanks!
Charles

---

### Post by Txukie on 2005-05-31
It might be a poor signal to the router. Check what the signal strength is like on your wifi connection.

---

### Post by thrift on 2005-05-31
You need to test out and see what is making your connection slower.  I highly doubt it's firefox.

Try opening a terminal and 
dmesg > dmesg.txt 
and attach dmesg.txt in your home directory, that will let us know what's going on with your wifi card.  What wifi card do you have?

Try to open a terminal and
ping [www.google.com](www.google.com)
Does it start getting replys quickly?  How many ms between replys?

try to open a terminal and 
ping 192.204.202.126
Does it start getting replys quickly?  How many ms between replys?

If you attempt to open a terminal and

"wget http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.11.11.tar.bz2"
without the quotes, those are just to preserve the full url.
how is the speed on that?  Is at close to what you are getting on the XP side?

If you attempt to download "http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.11.11.tar.bz2" in firefox.  How is the speed on that?  Is it close to what you get on the XP side?

With this kind of information we can help you a lot more.

---

### Post by astronerd on 2005-05-31
Thanks for the suggestions.... Unfortunately I am still quite the noob at linux so I cant get the dmesg file as a text that this forum will use as an attachment.  It just says invalid format, even though it is just a text document....
 
Here is the google ping....
PING [www.l.google.com](www.l.google.com) (64.233.161.104) 56(84) bytes of data.
64 bytes from 64.233.161.104: icmp_seq=1 ttl=245 time=39.0 ms
64 bytes from 64.233.161.104: icmp_seq=2 ttl=245 time=35.8 ms
64 bytes from 64.233.161.104: icmp_seq=3 ttl=245 time=41.0 ms
64 bytes from 64.233.161.104: icmp_seq=4 ttl=245 time=40.0 ms
64 bytes from 64.233.161.104: icmp_seq=5 ttl=245 time=37.0 ms
64 bytes from 64.233.161.104: icmp_seq=6 ttl=245 time=36.1 ms
64 bytes from 64.233.161.104: icmp_seq=7 ttl=245 time=36.9 ms
64 bytes from 64.233.161.104: icmp_seq=8 ttl=245 time=35.8 ms
64 bytes from 64.233.161.104: icmp_seq=9 ttl=245 time=39.5 ms


The speed on the wget command is roughly 350 K/s give or take.  And this is roughly the speed I get in XP, little slower....

The firefox download is going at 15-20 Kb/s.....

Does this help?

---

### Post by astronerd on 2005-05-31
Got the dmesg... sorry!

---

### Post by shakin on 2005-05-31
When you ping does it take a long time to resolve the domain name? I've seen where some DNS servers like to be slow for Linux clients and mixing up the DNS server order tends to fix the problem (eg, put your last DNS server first).

---

### Post by astronerd on 2005-05-31
How do I check this, change the DNS order?

---

### Post by not_yet on 2005-05-31
it may be an ipv6 issue

changes below from the ubuntu starter guide

Address Bar -> about:config

Filter: ->
network.dns.disableIPv6 -> true
network.http.pipelining -> true
network.http.pipelining.maxrequests -> 8
network.http.proxy.pipelining -> true

cheers

---

### Post by astronerd on 2005-05-31
Those ipv6 changes helped a little.  When I tried to download the link provided in the earlier post my speed went from 15-20 to 50 or so.  Which is better, but still not the full speed of the connection..... Thanks for the help so far though!

---

### Post by beeldings on 2005-05-31
Set **browser.turbo.enabled** to **true** under the about:config page. I don't know how much of a performance increase you will notice, if any, but it couldn't hurt to enable this.

---

### Post by not_yet on 2005-05-31
not sure if you have seen this 

have a read

[http://ubuntuforums.org/showthread.php?t=171](http://ubuntuforums.org/showthread.php?t=171)

---

### Post by Martin Witte on 2005-05-31
More firefox performance tweaks are here: [http://www.tweakfactor.com/articles/tweaks/firefoxtweak/4.html](http://www.tweakfactor.com/articles/tweaks/firefoxtweak/4.html)

---

### Post by raven on 2005-06-02
I have the same problem as FF being slow
but it is not the surf or download
it is FF it self, ex: right click for context menu
changing tab, click on a link to open in a new tab,
scroll down page are slow motion,
so you can say that the app itself is slow as if in molases
BUT cpu% is ok, FF not hoging CPU time,
I have opera for now, and the speed and download are the max of
my connection, opera behave very normal,
what I did with FF
I did all the tweaks mentioned on this forums in (about:config), 
I deleted my profile and used a new one
with no added extensions, just default.
still very slow to manipulate
any Help ???

---

### Post by thrift on 2005-06-02
try to:

rm -fR .mozilla

that will reset your firefox config to the default one.

---

### Post by raven on 2005-06-02
Thanx for the reply,
I did this "rm -fR .mozilla", but same issue
ex: when you have couple of tabs "ex:4" just changing between them
would take a 1/2sec more than opera now, or FF on winxp,
surfing too is a bit slower than opera, 
all in all like I mentioned before, It seems FF in slow motion a 1/2 sec in everything
comparing to opera or FF on winxp, opening menus or right click on a link,

---

