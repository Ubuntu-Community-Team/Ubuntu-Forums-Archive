---
title: "firefox problem after updatingo tp 7.10"
date: 2007-10-20
forum: General Help
---

### Post by HoudiniWater on 2007-10-20
After update to 7.10 I can visit only ubuntu.com, and nothing more:(
Why? And how to solve this?

---

### Post by HoudiniWater on 2007-10-20
Pls help!

---

### Post by Luke_1_81 on 2007-10-20
I seem to have a similar problem. I can't seem to access any websites in Firefox. 
The synaptic packet manager can download packages fine and I seem to be able to ping any website I like.
I reinstalled Firefox but this made no difference.
I also installed Epiphany web browser but again cant seem to access the web.

I disabled the firewall on my router just in case but this didn't help and I also checked the DNS settings in the network properties. I even tried removing all entries but this made no difference.
 
:confused:

Can you ping other websites ok?

---

### Post by subvertigo on 2007-10-20
The problem is Tahoma.

I had the same problem. I don't understand why upgrading from Feisty to Gutsy, Tahoma font went broken.

For now delete Tahoma font from /usr/share/fonts/...

I'm searching for a solution .... i need Tahoma!

---

### Post by HoudiniWater on 2007-10-20
Ok, tried to do some more actions, without result, but...

1) Run firefox with root rights - no effect.
2) Run firefox with different accounts: firefor -AccountManager - no effect
3) I tried to use text browser - links. All was good:) but without graphics:)
4) Reinstall FF - no effect

Any ideas?

I think, that resume might be only that FF uses some packets broken ubuntu packets.

---

### Post by HoudiniWater on 2007-10-20
Wait you say that the TAHOMA is the problem why I can not visit any web site, except ubuntu.com

By the way all my localhost sites are ok. Wow! I can visit one of my old site in internet, sorry for advertising - bankconference.ru  , but may be it will help.

---

### Post by isaacj87 on 2007-10-20
Hey guys,

I've been having similar problems ever since I tried out the new kernel a couple months back. That's why I had to downgrade my kernel back to 2.6.20-16
Even now, with gutsy I have this "firefox lag" that really annoys me...I hope someone made a bug report and these issues get solved.

---

### Post by Luke_1_81 on 2007-10-20
Thanks for the info. I'm not sure Tahoma is the issue in my case. I don't have a tahoma listing in /usr/share/fonts/.
However I perhaps should have mentioned before that this was not an upgrade but a fresh install.

Has anyone else managed to get any other graphical browsers to work or are you finding that its just FF?

---

### Post by HoudiniWater on 2007-10-20
Opera also does not work :( only ubuntu.com
Damn it, what's wrong?

---

### Post by xyzt on 2007-10-20
As I have been posting elsewhere, my 7.10 can ping and ftp from console (two fresh installs from a verified CD), but Firefox and Evolution don't connect to servers. I haven't the slightest idea of what to do, since I'm new to this. And I haven't had a single answer to my posts, I've been basically talking to myself.

---

### Post by Luke_1_81 on 2007-10-20
I tried to telnet on port 80 which works so I guess the port is not blocked in any way.

I have a separate modem and router so I connected the modem directly to my machine to see if this made a difference. No change though.

Interestingly I did get a page to load once (mail.yahoo.com) but it took about 3 mins to load! I had tried this page before and have tried it again since with no joy though. Bizarre.

I'm fast running out of ideas.    :(

---

### Post by Grellin on 2007-10-21
Similar problem here. Updated from 7.04 to 7.10 and everything seems to work great except loading sites in Firefox. I can get to some sites with no issues but other sites like Hotmail and Yahoo seem to take forever to load. Both of them seem to "stick" when it is loading advertisement type links. Did 7.10 add some form of phishing protection or other spam guard??

---

### Post by Grellin on 2007-10-21
This message has the fix that worked for me. 

[http://ubuntuforums.org/showthread.php?t=580491](http://ubuntuforums.org/showthread.php?t=580491)

---

### Post by andreakk77 on 2007-10-22
I have the same problem, I can't go on on internet at all.
I can use the ftp client service, but if I try to download new packages using sudo apt-get install   nothing happen, I tryed to disable the firewall but nothing.
maybe I should wait before to upgrade the os to 7.10....

---

### Post by cattlecall on 2007-10-23
I've a similar problem accessing websites with FF.

First time install of Ubuntu (ever) today using v7.1.0, and upgraded FF to
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.8.1.8) Gecko/20071022 Ubuntu/7.10 (gutsy) Firefox/2.0.0.8
only just an hour ago but no joy in solving this issue.

I've restarted Ubuntu about 10 times to test this problem and FF simply behaves erratically. I can always access ubuntu.com, and usually the Ubuntu forums and other websites listed in the bookmarks that ship with the install. On any given attempt I can access other websites like google.com, yahoo.com, or sites linked to from google search results page. The 'Latest BBC Headline' feeds usually load after some time, but not always; rarely do the actual bbc.com pages load.

I've tried fix posted here [http://ubuntuforums.org/showthread.php?t=580491](http://ubuntuforums.org/showthread.php?t=580491) but no success (though the fix seems better suited to solving an issue with Flash).

More info:
I've installed the 64-bit Ubuntu distro on a HP Pavilion dv8000 AMD-Turion box and ran into inevitable broadcom wireless issues that were solved by a solution at: [http://ubuntuforums.org/showthread.php?t=197102&highlight=compwiz+broadcom](http://ubuntuforums.org/showthread.php?t=197102&highlight=compwiz+broadcom)
I also had a slow startup problem that was solved using the fix posted at:[http://ubuntuforums.org/showthread.php?t=581075&highlight=usplash.con](http://ubuntuforums.org/showthread.php?t=581075&highlight=usplash.con)

Beyond that, the install was straightforward. Connections to check updates and to package repositories work as expected, and otherwise the rest of the system seems to be working to spec.

I'm an absolute Linux beginner, so above is the only info I know to post. If anyone can steer me in the right direction I'll post any other data that can help solve this issue.

All the best!

---

### Post by cattlecall on 2007-11-01
This fix (from here: [http://ubuntuforums.org/showthread.php?t=87798](http://ubuntuforums.org/showthread.php?t=87798) ) solved my problem:

Try typing about:config in your Firefox address bar. Type ipv6 in the "Filter:" box, find the option that says "network.dns.disableIPv6". If it reads "False" right click and toggle it to True. Should give you a slight speedup in your browsing.

---

