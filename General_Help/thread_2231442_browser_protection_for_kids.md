---
title: "browser protection for kids?"
date: 2014-06-25
forum: General Help
---

### Post by garyed on 2014-06-25
I'm setting up an Ubuntu desktop for a 9 year old. My only concern is how to protect them from or block certain internet sites and try to keep things G rated. Any advice?

---

### Post by papibe on 2014-06-25
Hi garyed.

I would create an account with OpenDNS, then activate their parental control features, and finally I'd point the machine to use their DNS service.

Just a thought.
Regards.

---

### Post by Quarkrad on 2014-06-25
+1  I too use OpenDNS.

---

### Post by QIII on 2014-06-25
... which will buy you about 90 minutes before a 9 year old figures out how to get around it ...  :)

What papibe says, plus something like DansGuardian, PLUS intrusive physical monitoring when the kid is on line.

If they don't like you looking over their shoulder every few minutes, it's time to gets them a stick and a rock to play with.

;)

---

### Post by garyed on 2014-06-25
Thanks for the ideas,

I'll look into it

---

### Post by jaimerosario on 2014-07-09
I'm reworking a script I did long ago (at the moment, I'm unemployed) that installs and configures Squid3/Dansguardian with OpenDNS.
I added a customized dictionary of both english/spanish words for filtering.
If you are interested, send me a private message.
The script I'm working on automatically installs and configures:

1. Squid3
2. Dansguardian with a default of four filter groups, plus added a custom dictionary of words to filter and urlbigblacklists as the main blacklist.
3. Webmin with DG Webmin module.
4. DHCP Server for up to four subnets.

If you want to check, send me a message to bring you the pastebin url so you can see the code.

---

