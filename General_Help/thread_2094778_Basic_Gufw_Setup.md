---
title: "Basic Gufw Setup"
date: 2012-12-14
forum: General Help
---

### Post by Iggy64 on 2012-12-14
While there is a specialized forum here dealing with security issues, most of the discussion there goes right over this newbie's head.  I have read many, many articles across the web on how to configure the ufw firewall; but it's still not clear to me how to do a really basic setup.  I am hoping someone here can tell me what I need to do.

I use the internet to:
- browse for information 
- make occasional purchases (such as from Amazon)
-  send and received email through Yahoo! email and Gmail
- play YouTube videos
- occasionally Skype

I don't do any FTP or torrent transactions.   The only other traffic coming into my machine would be images dumped from my camera or music files from my music mixer.

I have installed Gufw.  Can someone please suggest the best Incoming and Outgoing settings to maximize security while allowing the activities I listed above?

Thanks!

---

### Post by haqking on 2012-12-14
> **Iggy64 said:**
> While there is a specialized forum here dealing with security issues, most of the discussion there goes right over this newbie's head.  I have read many, many articles across the web on how to configure the ufw firewall; but it's still not clear to me how to do a really basic setup.  I am hoping someone here can tell me what I need to do.

I use the internet to:
- browse for information 
- make occasional purchases (such as from Amazon)
-  send and received email through Yahoo! email and Gmail
- play YouTube videos
- occasionally Skype

I don't do any FTP or torrent transactions.   The only other traffic coming into my machine would be images dumped from my camera or music files from my music mixer.

I have installed Gufw.  Can someone please suggest the best Incoming and Outgoing settings to maximize security while allowing the activities I listed above?

Thanks!

[http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)

---

### Post by Iggy64 on 2012-12-14
Thank you for your kind reply.  

Sadly for me, that link is one of the threads I have already read and had it go over my head.  Yes, I don't even know what DHCP means, or whether I need it.  I don't know which email ports I need if I only use Yahoo! and Gmail.  And so on.  So even the nice, basic tutorial given there is beyond my complete understanding.  I hope to learn these things, but I would like to active the firewall now.

So I am fishing for specific advice on which incoming and outgoing ports I should allow, given the list of activities I wrote in my initial post.  In other words, given the activities I wrote in that post, what incoming and outgoing exceptions would you make?

Thanks for your patience and understanding.  I am just beginning to learn.

---

### Post by haqking on 2012-12-14
> **Iggy64 said:**
> Thank you for your kind reply.  

Sadly for me, that link is one of the threads I have already read and had it go over my head.  Yes, I don't even know what DHCP means, or whether I need it.  I don't know which email ports I need if I only use Yahoo! and Gmail.  And so on.  So even the nice, basic tutorial given there is beyond my complete understanding.  I hope to learn these things, but I would like to active the firewall now.

So I am fishing for specific advice on which incoming and outgoing ports I should allow, given the list of activities I wrote in my initial post.  In other words, given the activities I wrote in that post, what incoming and outgoing exceptions would you make?

Thanks for your patience and understanding.  I am just beginning to learn.

the steps in that thread suit most users, and suits you, you will need DHCP, DNS, Email, HTTp etc so the ports listed suit you, I dont know of top of head what Skype uses, youtube wont require open ports as it is web traffic through port 80.

So follow the thread using GUFW f that is the interface you want to use and do, it is step by step so follow the steps.

DHCP Access - Port 67 and 68 UDP

Web Access - Ports 80 and 443 Protocol TCP

Email Access - Ports 25 and 110 , 143 Protocol TCP

DNS Access - Port 53 Protocol TCP and UDP (This is absolutely required)

Edit: according to Skype they use 80 and 443 which you are opening anyways or whatever port you choose in skype configuration [https://support.skype.com/en/faq/FA148/which-ports-need-to-be-open-to-use-skype-for-windows-desktop](https://support.skype.com/en/faq/FA148/which-ports-need-to-be-open-to-use-skype-for-windows-desktop)

Peace

---

### Post by Ms. Daisy on 2012-12-15
You can set up a firewall as a new user, it just takes some patience if you set up outbound rules.  

If you find that something isn't working the way it should (network printer, skype, whatever) the best and quickest course of action is to look at the firewall logs to see what ports are being blocked that shouldn't be.  Here's a quick primer to reading ufw logs:

[http://ubuntuforums.org/showthread.php?t=2085110](http://ubuntuforums.org/showthread.php?t=2085110)

---

### Post by Rexilion on 2012-12-15
You are only listing client side transactions, so this would lock your firewall down the most:

> *filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [0:0]
:IN - [0:0]
:OUT-NEW - [0:0]
-A INPUT -i lo -j ACCEPT
-A INPUT -m state --state ESTABLISHED,UNTRACKED -j ACCEPT
-A INPUT -m state --state NEW -m limit --limit 100/sec --limit-burst 150 -m recent --set --name DEFAULT --rsource -j IN
-A INPUT -j LOG --log-prefix "bpkt filter in: " --log-level alert
-A OUTPUT -m connmark --mark 0x1 -j OUT-NEW
-A OUTPUT -p icmp -j DROP
-A IN -m connlimit --connlimit-above 10 --connlimit-mask 32 --connlimit-saddr -j RETURN
-A IN -m recent --rcheck --seconds 1 --hitcount 50 --name DEFAULT --rsource -j RETURN
-A IN -p tcp -j CONNMARK --set-xmark 0x1/0xffffffff
-A IN -j ACCEPT
-A OUT-NEW -j CONNMARK --set-xmark 0x0/0xffffffff
-A OUT-NEW -p tcp -m tcp --tcp-flags ALL SYN,ACK -j ACCEPT
-A OUT-NEW -j LOG --log-prefix "bpkt filter out: " --log-level alert
-A OUT-NEW -j DROP
COMMIT

You need to install 'iptables-persistent' for this and move the above file to /etc/iptables/rules.v4. Then do:

```
service iptables-persistent start
```

This is not exactly what you asked for since you wanted gufw advice. But this is native netfilter/iptables format which is widely documented and discussed.

```
man iptables
```

should give you a detailed explanation of each and every option and parameter.

An overview of the above snippets features is:

- rudimentary DDOS protection
- client side only (on your request)
- logging of blocked packets in dmesg (in case you run into trouble)
- tcp and udp blackhole emulation

---

### Post by jim_deadlock on 2012-12-15
Iggy64, first of all you should know that Ubuntu is already pretty secure, the ports are all closed by default and I would hazard a guess that most Ubuntu users don't even bother with a firewall.

With that said, the most hassle-free way of using gufw is to simply set the options to outgoing=ALLOW incoming=DENY, with this method you will have minimal tweaking to do while blocking all incoming nasties. If you set both to DENY then you will likely have more tweaking to do than you would otherwise.

Whichever method you choose above, at some point you will hit a problem where something stops working that was working before. When this happens, do this:

```
cat /var/log/syslog | grep 'UFW BLOCK'
```

Use this to track down whatever is being blocked (in most cases it'll be the last line), then you can find the IP, port number, protocol (UDP/TCP) and you can add these details as a new rule within gufw to allow it through. You can post here if/when you get to that point for further instructions on adding new rules.

Hope it helps.

PS. All of the items you listed, with the exception of skype, are browser-based and you will not have any trouble if you simply block all incoming as I described above. According to haqking's link, this is also the case for skype anyway.

---

### Post by Iggy64 on 2012-12-17
Many thanks to all who offered me help.  Your kind replies give me a lot better perspective on how I should handle my current situation.  Hopefully, as I get more comfortable with Linux, I'll be able to take full advantage of your advice.  Meanwhile, I can set up a basic firewall without getting bogged down in more detail than I need.

Again, thanks very much!

---

### Post by 3rdalbum on 2012-12-17
> **Iggy64 said:**
> While there is a specialized forum here dealing with security issues, most of the discussion there goes right over this newbie's head.  I have read many, many articles across the web on how to configure the ufw firewall; but it's still not clear to me how to do a really basic setup.  I am hoping someone here can tell me what I need to do.

I use the internet to:
- browse for information 
- make occasional purchases (such as from Amazon)
-  send and received email through Yahoo! email and Gmail
- play YouTube videos
- occasionally Skype

I don't do any FTP or torrent transactions.   The only other traffic coming into my machine would be images dumped from my camera or music files from my music mixer.

I have installed Gufw.  Can someone please suggest the best Incoming and Outgoing settings to maximize security while allowing the activities I listed above?

Thanks!

**ALLOW: All.**

I'm serious. You've got nothing listening to incoming connections, with the exception of Skype. As far as I know, Skype works better when it can grab incoming connections. Any malicious incoming connections would simply be refused by your computer as nothing would be listening.

You only need a firewall on Windows because Windows keeps listening to incoming ports when it doesn't need to. Attackers can open incoming connections to Windows in this way and plant their own malicious code. Ubuntu doesn't listen to incoming connections by default, so you're safe.

If you don't believe me and still think you need a firewall, then set gUFW to deny all incoming and allow all outgoing. This is the default configuration on all broadband modem/routers, and is safe, perfectly sensible and doesn't require whitelisting every time you install a new program. Incidentally, if your network is protected by a firewall in your modem/router, then you don't need any firewall on your computer.

Don't bother setting any rules to deny outgoing connections. You're just creating more work for yourself without increasing your level of security on Linux. For your Windows firewall, you probably need to deny outgoing connections because Windows gets infected with all sorts of malware; but for Linux where these things are almost unheard of, you don't need to worry.

**In short, someone who only uses their internet connection for the things you listed, does not need to bother with any sort of firewall on Linux.**

---

### Post by haqking on 2012-12-17
> **3rdalbum said:**
> **ALLOW: All.**

I'm serious. You've got nothing listening to incoming connections, with the exception of Skype. As far as I know, Skype works better when it can grab incoming connections. Any malicious incoming connections would simply be refused by your computer as nothing would be listening.

You only need a firewall on Windows because Windows keeps listening to incoming ports when it doesn't need to. Attackers can open incoming connections to Windows in this way and plant their own malicious code. Ubuntu doesn't listen to incoming connections by default, so you're safe.

If you don't believe me and still think you need a firewall, then set gUFW to deny all incoming and allow all outgoing. This is the default configuration on all broadband modem/routers, and is safe, perfectly sensible and doesn't require whitelisting every time you install a new program. Incidentally, if your network is protected by a firewall in your modem/router, then you don't need any firewall on your computer.

Don't bother setting any rules to deny outgoing connections. You're just creating more work for yourself without increasing your level of security on Linux. For your Windows firewall, you probably need to deny outgoing connections because Windows gets infected with all sorts of malware; but for Linux where these things are almost unheard of, you don't need to worry.

**In short, someone who only uses their internet connection for the things you listed, does not need to bother with any sort of firewall on Linux.**


Facepalm.

Reverse connections, UPNP etc etc.

but we are all welcome to our opinion for sure ;-)

To the OP my advice is follow the guide linked to and control your outgoing aswell as incoming. 

Im not doing this discussion yet again.

---

### Post by Ms. Daisy on 2012-12-17
haqking beat me to the facepalm.

Yeah, it's definitely an option to hack naked (no firewall). It's just not a _secure_ option. Full Stop.

---

### Post by Iggy64 on 2012-12-18
Despite the variety of opinions expressed here, they are ALL very helpful to me.  As a Windows user for decades, I have been through the wars with my PCs at home and at the job.  I seem to spend more time reacting to the geniuses who spend their time creating malware than I do on my actual work.

Of course, I am fed up with Windows for more reasons than that.  But as a total noob to Linux, I have read as much as time allows about security issues here.  Just as in this thread, there is a divergence of opinion.  I thought I would get some opinions on my own specific situation from people with more experience.  And you have responded with not just opinions, but explanations why you feel that way.  And that is perfect!  I understand the reasoning behind each of your opinions, even if you do not agree with one another.  And this will help me decide what to do now, as well as in the future - when I may set up other machines to do other things.

Thanks to all of you for taking the time to help this beginner understand the issues, so that he can make an informed decision.

Without this forum, it would take much longer to learn.  I hope that someday I will know enough to pitch in and help others.

---

### Post by haqking on 2012-12-18
> **Iggy64 said:**
> Despite the variety of opinions expressed here, they are ALL very helpful to me.  As a Windows user for decades, I have been through the wars with my PCs at home and at the job.  I seem to spend more time reacting to the geniuses who spend their time creating malware than I do on my actual work.

Of course, I am fed up with Windows for more reasons than that.  But as a total noob to Linux, I have read as much as time allows about security issues here.  Just as in this thread, there is a divergence of opinion.  I thought I would get some opinions on my own specific situation from people with more experience.  And you have responded with not just opinions, but explanations why you feel that way.  And that is perfect!  I understand the reasoning behind each of your opinions, even if you do not agree with one another.  And this will help me decide what to do now, as well as in the future - when I may set up other machines to do other things.

Thanks to all of you for taking the time to help this beginner understand the issues, so that he can make an informed decision.

Without this forum, it would take much longer to learn.  I hope that someday I will know enough to pitch in and help others.

you are welcome, it really comes down to you either leave your door open or you dont, even if you lock it someone can still get in.

but if you choose to leave it open, how much do you trust your neighbourhood.

Either way it is obvious that locking it offers more protection no matter how little or "needed"

Best of luck

Peace

---

### Post by Iggy64 on 2012-12-18
Thanks, again, haqking.

Yes, it seems to make sense to at least deny incoming.  It doesn't seem to cost me anything, so why not do it?

As far as denying outgoing, then setting up permissions --- perhaps I will begin working on that after I study up on the principles people have outlined in this and other threads.  I simply don't know enough yet to dive in now.  But I will try to learn from what has been suggested in this thread, an put it to use when I am able to understand it better.

By contributing your suggestions, you have all helped me see the things I should study and learn, and then put into practice.  Thanks to all of you.

---

