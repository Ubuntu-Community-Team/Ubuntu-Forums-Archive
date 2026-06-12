---
title: "Any luck connecting to Exchange Server?"
date: 2007-11-16
forum: General Help
---

### Post by SuperMike on 2007-11-16
Anyone have luck connecting Thunderbird (with Lightning plugin, of course) in Ubuntu to Exchange Server via a mail proxy or plugin? Many offices don't permit IMAP or POP/SMTP access to Exchange, only OWA, and so Evolution uses the OWA technique. However, I tried Evolution and actually find it buggy, problematic, and prefer Thunderbird with Lightning.

So essentially it would be a proxy that acts like POP and SMTP but interacts with OWA. Thunderbird would then connect with this mail proxy locally on a workstation.

---

### Post by jken146 on 2007-11-17
I have never successfully connected except to OWA through Evolution, which works perfectly for me.

---

### Post by SuperMike on 2007-11-17
> **jken146 said:**
> I have never successfully connected except to OWA through Evolution, which works perfectly for me.

Really? I had bad luck with it. I had double appointments on my calendar, and when I deleted one, the twin would disappear with it -- aggravating. Also, if I clicked Tasks, Evolution would hang. Other than that, it was usable.

Another thing that needs to be changed in Evolution is that they need a solution for when someone connects from home over VPN and wants to connect to their previously downloaded mail on their office workstation desktop PC. I mean, you could do ssh -X and load Evolution, but when I did I found all kinds of errors popped up on my screen, and talk about sloooooow.

---

### Post by crazy181 on 2008-01-09
I wasnt sure if it would be possible to connect to exchange with ubuntu thanks guys you saved me a lot of research.

---

### Post by mnk0 on 2008-01-14
Hi, Im not sure if theres somethign im doing wrong but .. out of the box install of 7.10 and updated packages, i can't connect to exchange says either cannot authenticate to server, or bad password, when i use the same login for IMAP i can connect fine, and also the OWA url works fine. Any Ideas??

---

### Post by SuperMike on 2008-01-14
What version of Exchange Server are you using? That kinda matters.

---

### Post by mnk0 on 2008-01-15
Microsoft Exchange Server 2003 POP3 server version 6.5.7638.1
Microsoft Exchange Server 2003 IMAP4rev1 server version 6.5.7638.1

Microsoft Exchange Server 2003 SP2

---

### Post by SuperMike on 2008-01-16
Hmm. That should work. My guess is the way you have your authentication settings in your Evolution profile and compare that to how your OWA login works because Evolution really just talks to OWA unless you setup the connection through IMAP. Most big companies are *mean* and don't enable IMAP for internal users for some stupid reason. This forces you to use OWA or a regular Outlook client, or use Evolution through OWA.

Check the FAQ on the Evolution site about those auth settings? In particular the URL path is important, and the way the username and domain is created in your Evolution profile is important.

Last, if you're running a local firewall, or have a firewall restriction to the OWA from the IP you're on, that could be another stumbling block. However, I doubt that's your particular case, based on the facts you've mentioned.

---

### Post by mnk0 on 2008-01-16
well yeah, thats what i was confused about.. I pasted the URL from what I got when I logged into the OWA site "https://myDomain/exchange" ive tried without the '/exchange' aswell, and my username was "DOMAIN\user" format,

When i click on the authenticate button while adding the exchange account, it appears to authenticate fine, however when it tries to access the server for mail and that the prompt came up for the Authentication the message says "Enter Password for DOMAIN\user@Server" which I find odd that it doesnt just say "DOMAIN\user"


--
Omar Samad

---

