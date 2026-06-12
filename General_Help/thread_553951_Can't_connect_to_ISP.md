---
title: "Can't connect to ISP"
date: 2007-09-18
forum: General Help
---

### Post by labtek on 2007-09-18
Hello to the group. I'm using Kubuntu Feisty Fawn 7.04 from a dowload from the mirrors in a newly built system using a GeForce 6100SM-M mainboard with an AMD Sempron 3000 CPU. The mainboard chipset is Nvidia MCP61S.

I loaded the operating system on the computer's hard drive and all went well during the install. The only thing of note was that Feisty saw the 80 GB Western Digital SATA hard drive as SCSI. I downloaded Firefox, Thunderbird and a few other apps using Adept Manager without incident.

Firefox connected well to my ISP as did Thunderbird after I configured it to my Email account. I downloaded a few Emails (POP) but when I tried to send an Email to the ISP(SMTP) , I got a message that I was blacklisted due to excessive spamming and poor senderbase score. I called the ISP and was told that everything looked OK on their end and that I should not have gotten that message. I told the gentleman that I was using a Linux OS and he said that spamming should not be a problem.

I zero filled the drive, re-loaded the program and now the system refuses to connect at all to the Internet using either the live CD or the installed program. When using Adept Manager to download apps, I get the message that there was an error commiting packages- problem downloading some packages or the commit would break packages. Hence I can't download Firefox or Thunderbird (or anything else for that matter). I've tried another network card without any different results.

This is the first time I've ever seen this behavior in the 4 plus years I've been using Linux. I'm using the computer through a D-Link switch that works well with the 2 other computers hooked to it. I'm using a high speed connection to the ISP using a cable modem. I've tried re-setting the modem.

Perhaps the onboard LAN needs the driver installed from the setup CD.  Any other suggestions/comments would be welcomed and thanks in advance.

---

### Post by raijinsetsu on 2007-09-18
If you're using a cable modem, you must have a router, not a switch. I don't understand how your other computers could work with this configuration, as they shouldn't.

The way your LAN should be configured:

Cable Modem <-> Router/Gateway <-> Computers

As an aside, routers are usually also switches, but not vice versa. A switch makes sure that packets destined for Computer A only go out on the wire connected to Computer A. Computers B,C,D,E, etc. will not get packets destined for Computer A. This increases overall LAN throughput. :)

---

