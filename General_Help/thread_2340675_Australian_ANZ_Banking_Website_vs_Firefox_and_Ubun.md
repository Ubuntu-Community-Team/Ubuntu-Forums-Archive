---
title: "Australian ANZ Banking Website vs Firefox and Ubuntu"
date: 2016-10-20
forum: General Help
---

### Post by draxbear on 2016-10-20
I'm posting this up as I had a great deal of difficulty accessing the Australian ANZ Online Banking system from my Ubuntu 16.04 Desktop using Firefox. This was true when I stopped being their customer in 2013 and remains so here in 2016 when I had to jump on again to pull down some statements. Its likely you could try accessing via Chrome instead, but if you prefer not to, this fix works well for me.

Update your /etc/hosts file to redirect queries to yourself instead of some non-responsive server at ANZ called waf1x.anz.com.
Edit the hosts file with your preferred text edit, in my case vi:
```
sudo vi /etc/hosts
```
Add this entry under your localhost entry (match the IP addresses up if yours differs from mine)
```
127.0.0.1  waf1x.anz.com # Workaround for ANZ Banking Website
```

I suspect this is some kind of advertising server as it seems to have no impact at all on the operation of the site. Without this entry in place my entire firefox session would "grey out" for around 10 seconds every 10 seconds and was generally unresponsive even when not grey. The system eventually just kicked me out thinking I had timed out. Occasionally I'd see an error related to this server so figured it was worth a go "turning it off" in this manner.

I realize this is a banking system you're dealing with so use these steps with caution. To mitigate the risk significantly, you are redirecting to your localhost (127.0.0.1) IP address and not some other place so keep calm and carry on.

---

### Post by kurt18947 on 2016-10-21
Good job figuring that out. I'm pretty paranoid when it comes to sites that deal with personal information that identity thieves would love to get their hands on. Plain vanilla and boring - and well proven - is just fine. The bank I use sometimes wants to run flash ads. NoScript takes care of that.

---

### Post by &amp;KyT$0P# on 2016-10-21
draxbear, are you using NoScript?

(This is unrelated to kurt18947's post)

---

### Post by draxbear on 2016-10-22
Yes I'm using noscript and have whitelisted anz. I'm also using privacy badger and have deactivated it for them as well. Same issue with/without these whitelisted/disabled.

---

### Post by &amp;KyT$0P# on 2016-10-22
But you didn't try disabling NoScript entirely, did you?  (Don't.  Really, don't.)

It's an unfortunate pattern with NoScript and many banking sites.  They are using very unsafe practices for passing data around between domains, so unsafe that NoScript's XSS filter gets involved.  Search of the NoScript forum turns up [this]("https://forums.informaction.com/viewtopic.php?f=10&t=21325"), but some of those suggestions are, in my view, not really advisable for daily use.

**The OP of this thread here does the correct idea for a workaround.**  Just block the one domain and you're good.

You can also block it by marking [FONT=Courier New]waf1x.anz.com[/FONT] untrusted in NoScript.

---

