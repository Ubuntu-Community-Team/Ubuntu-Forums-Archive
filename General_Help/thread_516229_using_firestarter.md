---
title: "using firestarter"
date: 2007-08-02
forum: General Help
---

### Post by HPCE_Larry on 2007-08-02
I have installed firestarter and i'm unsure as to how it works exactly. Does it block everything and you have to specify what to enable? Or what?

---

### Post by keyboardashtray on 2007-08-03
Sytem>Administration>Firestarter to access it and run the wizard the first time.

Basically, I haven't encountered an event it has blocked yet - whenever I run into a problem at a website, downloading something, or using a part of a program that uses the internet, I stop the firewall, and try again to see if it was blocking me. So far, it has always been something else.

I almost wish it did interfere with something so I knew it was working :)

Link to a tutorial at the website: [http://www.fs-security.com/docs/tutorial.php](http://www.fs-security.com/docs/tutorial.php)

---

### Post by eeried on 2007-08-03
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)
 On this web site you'll see what firestarter does: it blocks all your ports so nothing bad can come into your system.
Check on the ports page on that web site and you'll see.

---

### Post by mcduck on 2007-08-03
With default setting Firestarter blocks all incoming connections and allows all outgoing connections. Responses to connections you have opened yourself are also allowed. This is pretty much perfect setup for home users, only thing s to change are that if you use Bittorrent you may want to open ports for it for better performance. And of course if you install any servers you need to open ports for them as well.

remote machine --> your computer: blocked
your computer --> remote machnine: allowed
your computer --> remote machine --> your computer: allowed

Anyway, as long as you don't install any servers you don't really need any firewall with Ubuntu. While all ports are open by default, there is no program running that would respond to any incoming connections.. ;)

---

### Post by strabes on 2007-08-03
You don't even need to install firestarter unless you need a frontend to open specific ports because all non-necessary ports are closed by default in ubuntu.

---

### Post by eeried on 2007-08-06
According to the web site I noted earlier: [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2) before installing firestarter, all the ports are stealthed, and after installing it and running it all the ports are closed.

---

### Post by BigRon on 2008-02-09
Hello People! I am new to Ubuntu and Firestarter. When running Firestarter I have noticed it's counted 25 serious inbound events. 

I've only been online an hour or so, and there's a list of blocked connections as long as your arm, is this normal?

I am not a computer expert and have had 2 nightmarish experiences of trojans in the past (using windows of course) and was told that I wouldn't need a Firewall with Ubuntu because I have no interest in file sharing or anything.  However I've installed one anyway just to be on the safe side and it looks as if all hell is breaking loose despite everything running fine.

There have been blocked connections from the following services: Unknown, Samba(SMB), Traceroute and DCOM-scm.

Do any of the above sound familiar? Are they anything to worry about? 

I know I'm pretty clueless, but some advice would be much appreciated.

Cheers

---

### Post by eeried on 2008-02-10
You don't have to worry about anything at all, except if you notice that you can't get access to a service or a web page.

Firestarter protects your ports. you can check by clicking on one of the previous links that has a page which shows how well your computer is protected:
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

NB: if you don't need Samba -- only useful if you share a printer with a windows box for instance, you can even uninstall it through Synaptic.

---

