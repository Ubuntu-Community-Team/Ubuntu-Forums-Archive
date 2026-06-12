---
title: "My Desktop Was Hacked!!!"
date: 2015-06-26
forum: General Help
---

### Post by coljohnhannibalsmith on 2015-06-26
Hello,

While running a TOR relay with Vidalia, I got this warning message: "The following computer: 185.56.82.6 is trying to view or control your Desktop." This happened repeatedly yesterday afternoon with the above and IP. It also, happened with tsnl09.201-154-163.dyn.nltelcom.net. I was offered a button to refuse or allow.  Of course I selected refuse.

What can I do?  Should I be worried about this? Can I report these people to their ISP's?  Should I contact my ISP?  Are there any settings I can select to further block these intruders? If it happens again, I'll be sure to take a picture.

Thanks, Hannibal

---

### Post by kerry_s on 2015-06-26
it's probably just 1 of those fake pop up js scripts. the kind that takes you to some unsavory site, you should close the window instead of selecting a button, remember they can put anything they want on a button, you think your clicking cancel & your actually clicking allow. i suggest avoiding the site your getting the popup.

---

### Post by steeldriver on 2015-06-26
Did you enable Desktop Sharing? is your VNC port (default 5900) open to the public network?

---

### Post by dragonfly41 on 2015-06-26
Check your ports with this service ...

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

### Post by grahammechanical on 2015-06-26
I did a web search on "computer IP address 185.56.82.6" and eventually came up with this

[http://myip.ms/info/whois/185.56.82.6](http://myip.ms/info/whois/185.56.82.6)

The IP address is owned by Shocksrv Internet Services Private Limited of India. So, if you do want to report an attempt to hack your system. It is most likely one of their users.

Regards.

---

### Post by QDR06VV9 on 2015-06-26
> **grahammechanical said:**
> I did a web search on "computer IP address 185.56.82.6" and eventually came up with this

[http://myip.ms/info/whois/185.56.82.6](http://myip.ms/info/whois/185.56.82.6)

The IP address is owned by Shocksrv Internet Services Private Limited of India. So, if you do want to report an attempt to hack your system. It is most likely one of their users.

Regards.
Thanks for confirmation grahammechanical!
My son a few months back knew I had tor and selektor installed so he thought he would try to outsmart me and was doing some Illegal downloading That lasted about 2 days before 
I cut him off my computer all together. And a Threat to turn his habits over to the appropriate authorities,  Long story short That IP address with similar warnings popped up . But A quick Email to them the problem has gone.
And OP you can switch exit nodes with selektor!
Regards

---

### Post by coljohnhannibalsmith on 2015-06-26
> **kerry_s said:**
> it's probably just 1 of those fake pop up js scripts. the kind that takes you to some unsavory site, you should close the window instead of selecting a button, remember they can put anything they want on a button, you think your clicking cancel & your actually clicking allow. i suggest avoiding the site your getting the popup.

I wasn't visiting a site. I was just running a relay, and Firefox was set to Bing, which I use for a homepage.  I'm using Exede for an ISP.

Thanks, Hannibal

---

### Post by coljohnhannibalsmith on 2015-06-28
Hacked Again!!!

Wow, I reported the abuse to the ISP's of the previous two hackers and they stopped hacking me.  Now, I've gotten a different hacker 61.240.144.64 entering the fray. This all happened last night.

Here's his ISP:
inetnum:        61.240.0.0 - 61.243.255.255
netname:        UNICOM
descr:          China United Network Communications Corporation Limited
descr:          No.21 Financial Street,Xicheng District, Beijing  100140 ,P.R.China

Since all these hackers have launched their attacks from foreign soil, I suspect the following:
Under FISA (US Foreign Intelligence Surveillance Act), the US may not spy on American Nationals on American soil, but may use foreign nationals operating from foreign soil to do so.  A real Catch 22.  This scenario seems to fit.  I also live in a border town with Mexico, so running a TOR relay may have caught the attention of the NSA. Any thoughts on this?

To add insult to injury, I tried to boot my system this morning and got the following message:

error: hd0 out of disk.
grub rescue> _

error: unknown command '['.
error: unknown command '['.
error: unknown command 'save_env'.
error: unknown command '['.
error: unknown command 'search'.
error: unknown command 'linux'.
error: unknown command 'initrd'.

Press any key to continue>

Failed to boot both primary and fallback entries.

I have GNU GRUB Version 1.99-21ubuntu3.17

Did the hacker erase my boot loader?  How do I recover?

Thanks, Hannibal

---

### Post by mastablasta on 2015-06-29
> **coljohnhannibalsmith said:**
>  Any thoughts on this?
yeah. you are being paranoid.

you yourself are using TOR, yet you htink that you are under attack and that the hackers are not using TOR to mask their IP?! Furthermore China has plenty of pirated windows XP which are relatively easy to crack for those that know how to do it (as the systems are unpatched). They can then be used as bots in hacking attempts.

2 options - use fail2ban or similar to create a blacklist (IPs not allowed to access your IP) or to create a white list (list of IP's that are allowed to attempt to and to access the PC).

as other mentioned by default ports on firewall are closed. so check you firewall settings as well. you can see if anything actually go in in your logs. you can install additional monitoring tools. if oyu do get hacked you probably won't know it. if you do get hacked by NSA you probably wont' know it and besides they do not need to hack you since they collected the data by other means.

> 
To add insult to injury, I tried to boot my system this morning and got the following message:

error: hd0 out of disk.
grub rescue> _

error: unknown command '['.
error: unknown command '['.
error: unknown command 'save_env'.
error: unknown command '['.
error: unknown command 'search'.
error: unknown command 'linux'.
error: unknown command 'initrd'.

Press any key to continue>

Failed to boot both primary and fallback entries.

I have GNU GRUB Version 1.99-21ubuntu3.17

Did the hacker erase my boot loader?  How do I recover?

Thanks, Hannibal


doesn't look related. but you can boot into live session and check if the disk is really out of space. and to check the disks SMART status. as well as logs for any successfulllogins from iP other than yours

---

### Post by Yellow Pasque on 2015-06-29
> And a threat to turn his habits over to the appropriate authorities
You threatened to narc on your own son for that? LOL.
EDIT: BTW, you should consult a lawyer before doing something foolish, because if your name's on the account/bill, then you are probably legally responsible. Better yet, stop expecting the government to solve a family disagreement over internet usage...

> Can I report these people to their ISP's?
You're wasting your time/effort doing that, especially for overseas ISP's. Most likely, the requests are coming from proxies and/or computers under the control of bots.

> Did the hacker erase my boot loader?
I really doubt you were hacked. You got a couple random VNC requests which you denied. Turn off VNC if you don't use it regularly: [https://help.ubuntu.com/community/VNC/Servers#vino](https://help.ubuntu.com/community/VNC/Servers#vino)
If you don't use VNC at all, purge the vino package.

---

### Post by QDR06VV9 on 2015-06-29
> You threatened to narc on your own son for that? LOL.
EDIT: BTW, you should consult a lawyer before doing something foolish,  because if your name's on the account/bill, then you are probably  legally responsible. Better yet, stop expecting the government to solve a  family disagreement over internet usage...

One should Tend to their own affairs!
I was not seeking help over  the matter, but it proved to be an effective ploy. Thanks for the unwanted Advise anyway.;)

---

### Post by Yellow Pasque on 2015-06-29
> **runrickus said:**
> Thanks for the unwanted Advise anyway.;)
As snide as you are being, you're still welcome. Note that you never said whether it was a serious threat or not... Also, I thought you were the OP because of the way you responded to gm (sorry to OP for any confusion).

---

### Post by dino99 on 2015-06-29
LOL
sometimes we meet really funny thread. OP said: 'i was only running a relay'/'i've been hacked'; someone else said 'i've identified the ip'

if people want to ride over the wild edge, at least they need to understand what kind of tool they are using, how it works; what an ip redirection means (identifying an ip, do you really beleive you got it when using onions ?)

Really 'hannibal' call the emergency agency right now  :lolflag:

---

