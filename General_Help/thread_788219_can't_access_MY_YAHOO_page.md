---
title: "can't access MY YAHOO page"
date: 2008-05-09
forum: General Help
---

### Post by Denny Johnson on 2008-05-09
Dell 1420n w preloaded 7.04.
All has been mostly well for several months.
All seems to be OK today except I can't access MY YAHOO page.
This is my homepage, lotsa stuff there.
I can't get there via HOME icon, address bar. google search results page, links on other YAHOO pages.
It's been like this for at least 6 hrs, don't see any ref to yahoo problem on the web.
All other web pages are fine.
After about 75 sec, I get this:

The connection was reset

     The connection to the server was reset while the page was loading.

    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.


Any suggestions greatly appreciated.

---

### Post by tech9 on 2008-05-09
are you behind a proxy?

---

### Post by didooofidooo on 2008-05-09
try other web browser first, if you still have the same problem then you should contact your network administrator.

---

### Post by Denny Johnson on 2008-05-09
Don't think I'm behind a proxy.......not sure what that means..........this is just my home computer running thru cable and a wireless router.

---

### Post by tech9 on 2008-05-09
> **Denny Johnson said:**
> Don't think I'm behind a proxy.......not sure what that means..........this is just my home computer running thru cable and a wireless router.


are you getting an IP address from your router?

post 

```
ifconfig
```

---

### Post by tech9 on 2008-05-09
> **didooofidooo said:**
> try other web browser first, if you still have the same problem then you should contact your network administrator.

and if he's @ /home - there is no network admin :-$

---

### Post by Denny Johnson on 2008-05-09
> **tech9 said:**
> are you getting an IP address from your router?

post 

```
ifconfig
```

denjohn@dell:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1A:A0:FE:F6:CE  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1B:77:A7:9F:1D  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:77ff:fea7:9f1d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39032 errors:3331 dropped:8419 overruns:0 frame:0
          TX packets:32986 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:39649331 (37.8 MiB)  TX bytes:5638867 (5.3 MiB)
          Interrupt:17 Base address:0x8000 Memory:fe8ff000-fe8fffff 

eth0:avah Link encap:Ethernet  HWaddr 00:1A:A0:FE:F6:CE  
          inet addr:169.254.12.51  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2698 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2698 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:83298 (81.3 KiB)  TX bytes:83298 (81.3 KiB)


FWIW.....thought it may have been a cookie thing, just went thru and unblocked anything Yahoo related.

---

### Post by Denny Johnson on 2008-05-09
FWIW.....I've rebooted, repowered, and even had a system check since the problem started this morn, no help.

---

### Post by tech9 on 2008-05-09
> **Denny Johnson said:**
> denjohn@dell:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1A:A0:FE:F6:CE  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1B:77:A7:9F:1D  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:77ff:fea7:9f1d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39032 errors:3331 dropped:8419 overruns:0 frame:0
          TX packets:32986 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:39649331 (37.8 MiB)  TX bytes:5638867 (5.3 MiB)
          Interrupt:17 Base address:0x8000 Memory:fe8ff000-fe8fffff 

eth0:avah Link encap:Ethernet  HWaddr 00:1A:A0:FE:F6:CE  
          inet addr:169.254.12.51  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2698 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2698 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:83298 (81.3 KiB)  TX bytes:83298 (81.3 KiB)


FWIW.....thought it may have been a cookie thing, just went thru and unblocked anything Yahoo related.


ok... just making sure you were getting an IP... looks good there,

Did you try deleting or clearing all private data in FireFox?

try "mail.yahoo.com"

can you get to this part of the site?

---

### Post by Denny Johnson on 2008-05-09
I just cleared private data.....no joy.
"mail.yahoo.com" took me to my acct.
Rebooted......no joy????????

---

### Post by tech9 on 2008-05-09
> **Denny Johnson said:**
> I just cleared private data.....no joy.
"mail.yahoo.com" took me to my acct.
Rebooted......no joy????????

not sure why you are not able to access the main yahoo page?

I would try to install another browser at this point and see if you can access the main page...

There are a lot of browsers out there... Opera, Konqueror, ect

let me know how it goes.

Hopefully, there will be joy :)

---

### Post by Denny Johnson on 2008-05-09
mmmmmm..........although "mail.yahoo.com" took me to my inbox, the mail won't open.
But.........I can open all folders, can't open mail within folders.
But......if I go to 'Yahoo.com', I'm already logged in, if I hold the cursor over the MAIL button, it shows my msgs and I can open them.
But..........on any Yahoo page, Mail, Yahoo, e mail msgs........the page 'looks like" it's fully loaded, yet the spinning circle thingy indicates that it is not fully loaded.
Nothing appears on screen when I try MY YAHOO.

---

### Post by Denny Johnson on 2008-05-09
> **tech9 said:**
> not sure why you are not able to access the main yahoo page?

I would try to install another browser at this point and see if you can access the main page...

There are a lot of browsers out there... Opera, Konqueror, ect

let me know how it goes.

Hopefully, there will be joy :)

Thanks for thr effort.

I've been happy [til now] w firefox, any recommendations for something similar.

---

### Post by sailor2001 on 2008-05-09
use 'seamonkey' instead of firefox.....

---

### Post by tech9 on 2008-05-09
> **Denny Johnson said:**
> Thanks for thr effort.

I've been happy [til now] w firefox, any recommendations for something similar.

no problem :) ...

seamonkey is a good browser too

---

### Post by Denny Johnson on 2008-05-10
Perhaps it's not a Browser issue.
I looked at Seamonkey, and installing it looked a bit over my head.
Went into the Synaptic Package Manager, searched Firefox, removed a bunch of Mozilla Firefox xxxxxx Language/Region packages. Then reinstalled Firefox and Firefox-gnome-support.........................no help.
Installed Epiphany Browser from Applications/Add Programs.................no help.
Created a new Yahoo acct.............no help, same things are happening w either Yahoo acct in either browser.
Perhaps one clue.......when I tried to open an e mail, after considerable time, appeared: "An unexpected problem has occurred. There was no XML in the response"........Does that ring any bells?????

---

### Post by Denny Johnson on 2008-05-10
MY YAHOO is now working in both Yahoo accounts.
All Yahoo pages are back to normal.
WTF......I didn't change anything since last post??????????
I guess I'm happy, but bewilderment seems to be the prominent mental state:confused:
Thanks to all who helped:)

---

### Post by tech9 on 2008-05-12
> **Denny Johnson said:**
> MY YAHOO is now working in both Yahoo accounts.
All Yahoo pages are back to normal.
WTF......I didn't change anything since last post??????????
I guess I'm happy, but bewilderment seems to be the prominent mental state:confused:
Thanks to all who helped:)

Hi Denny,

That is very strange that it's working now "out of the blue", but I am glad that you got it.

Take Care

T9:)

---

