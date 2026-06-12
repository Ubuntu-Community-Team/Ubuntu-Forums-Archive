---
title: "What in Ubuntu is Disconnecting Dialup Connection as soon as it logs on??"
date: 2007-09-06
forum: General Help
---

### Post by OzzyFrank on 2007-09-06
I recently posted a thread asking how to stop Wvdial from constantly trying to reconnect, as it had disconnected while I was out of the room and kept reconnecting as it kept disconnecting. I figured if the server was down for maintenance, why have Wvdial waste money constantly reconnecting?

Anyway, it isn't that simple, as Wvdial connects OK, but then I get disconnected as soon as logon is verified. I am in Windows now where this does not happen. In Ubuntu it is now constant for a couple of days since it first disconnected and kept redialling. In this time, Windows has had no problems. So I doubt it is at my ISP's end. Any ideas?

---

### Post by john.nicholls on 2007-09-06
Does "tail -f /var/log/syslog" offer any clues?

---

### Post by OzzyFrank on 2007-09-06
I'll see tonight when I get back into Ubuntu. Then I'll have to get back into Windows to post the results, hehe! Geez, it was all going great till a couple of days ago! Cheers

---

### Post by OzzyFrank on 2007-09-07
Unfortunately, it doesn't seem "tail" is installed by default, so I couldn't read any output. Is there any part of any system file that I can post here to shed more light on what is happening? I tried again before and without fail it disconnects a couple of seconds after logging in.

---

### Post by john.nicholls on 2007-09-07
```
cat /var/log/syslog
```

Look for the entries at the time you attempted the connection. There should be a lot of them related to the attempted connection.

---

### Post by OzzyFrank on 2007-09-09
Actually it told me NOTHING about it whatsoever, unfortunately. I tried this morning right on 9.25 straight after logging in. I'm posting the last bit, being a couple of lines at 9.24am, then it goes to 9:26am with no mention of anything for 9:25 (during that minute I had connected and got cut off, then I redialled and hung up before it could connect... no mention of any of that).

I'm assuming this is not the right file to be looking for serial modem activity? Any other suggestions? And I can paste the whole log file, but it tends to be quite large, hehe. I have no idea what could have done this. I installed Ubuntuzilla to update Mozilla products, and in the log file there is a lot of mention of it, but that wouldn't be disconnecting me would it? Even if it did want to disconnect after looking for updates, it isn't connected that long.

Anyway, here is the end of the log. Hope someone can help!

Sep  9 09:24:17 ozzman-desktop nmbd[5775]: [2007/09/09 09:24:17, 0] nmbd/nmbd_nameregister.c:register_name(482) 
Sep  9 09:24:17 ozzman-desktop nmbd[5775]:   register_name: NetBIOS name OZZMAN_SMB_SERVER is too long. Truncating to OZZMAN_SMB_SERV 
Sep  9 09:24:17 ozzman-desktop nmbd[5775]: [2007/09/09 09:24:17, 0] nmbd/nmbd_nameregister.c:register_name(482) 
Sep  9 09:24:17 ozzman-desktop nmbd[5775]:   register_name: NetBIOS name OZZMAN_SMB_SERVER is too long. Truncating to OZZMAN_SMB_SERV 
Sep  9 09:24:17 ozzman-desktop nmbd[5775]: [2007/09/09 09:24:17, 0] nmbd/nmbd_nameregister.c:register_name(482) 
Sep  9 09:24:17 ozzman-desktop nmbd[5775]:   register_name: NetBIOS name OZZMAN_SMB_SERVER is too long. Truncating to OZZMAN_SMB_SERV 
THIS IS WHERE I CONNECTED BUT THERE IS NO ENTRY FOR 9:25!!
Sep  9 09:26:59 ozzman-desktop anacron[6022]: Job `cron.daily' started
Sep  9 09:26:59 ozzman-desktop anacron[7344]: Updated timestamp for job `cron.daily' to 2007-09-09

---

### Post by OzzyFrank on 2007-09-10
There is only one reason why I _haven't_ been going FRANTIC here, since to me Ubuntu without a web connection is a big deal: I have been waiting for my ADSL broadband to get connected.

After a long hour trying with support to get it going, it now (FINALLY!) works, and in Ubuntu as well as Windows. Thanks god I don't have to nut through would could be disabling the broadband connection, hehe! But this STILL begs the question: What could have been disconnecting the PPP dialup as soon as successfully logging on? And in what file(s) would you find evidence of this?

Obviously, this isn't much of a concern for me now, and I couldn't test/troubleshoot now anyway since my dialup acct is no longer, but for the benefit of others in this forum, if someone knows AT LEAST what file records dialup modem activity (sorry guys, but contrary to popular opinion, it ISN'T /var/log/syslog), please let us know.

But I'm glad I finally went broadband, not just coz of speed but because I can boot in and out of Windows and Ubuntu and keep checking mail etc without the cost of phonecalls.

Thanks all (but if you feel unsatisfied with the lack of answers for this problem, please feel free to dig around and post the results here!). [I won't mark this as SOLVED coz it isn't]

---

