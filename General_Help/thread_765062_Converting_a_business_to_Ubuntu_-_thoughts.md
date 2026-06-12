---
title: "Converting a business to Ubuntu - thoughts?"
date: 2008-04-24
forum: General Help
---

### Post by reiki on 2008-04-24
ok so topic says it in a nutshell, but here's the details and I'm looking for some input, thoughts, criticisms, etc...

A good friend has a business and has 10 or 12 computers, a handful of employees, and a problem. He's using a mix of XP and Vista and he is forever calling me in a panic because he got this virus or that trojan and.... well he's a friend, but he's not a system admin if you know what I mean. He's not afraid to DO stuff, but people target him through email (sometimes competitors) and weirdness happens.

Now he needs email and internet access on all machines. The only real sticky bit in this whole thing is that he NEEDS Excel. His business depends on it. There is a special app written in Excel that does all his calculations. It does not work correctly in Open Office (I tried). Not sure all of the ins-and-outs of that excel app. I've seen it. The developer allowed me to try it in Open Office. I just don't know enough about it to know what failed, but it only partially worked. Not sure if there's VB in it or what.

So here's my thought:
Set him up with Ubuntu. He can do all of his email and internet and all of that stuff without worrying about all the stupid windows viruses and trojans and junk. 

For his Excel needs, EITHER run Excel under Wine.... assuming everything in the Excel app functions correctly... OR give him a WinXP virtual machine using VMWare or VirtualBox and have that VM only run Excel. The VM would have no internet access, but WOULD have internal LAN access. The files created as a result of the Excel app would be stored to a network storage drive. NOT on the virtual machine's virtual hard drive. VM gets "snapshotted" once it's set up. It should never GET a virus as it's not connected to the internet any more and if it DOES get something, revert to snapshot. All data files are unaffected and could be scanned by ClamAV if necessary.

Does this sound like I'm headed in the right direction? Suggestions for how to do something differently?
Please don't suggest rewriting the Excel app into something more standard. The guy that wrote this lives in Hawaii, I've spoken to him, he doesn't have the knowledge or time to port it and he's very unwilling to let just anyone touch it. Has some highly proprietary formulas and stuff in it.

thoughts and suggestions welcome.

---

### Post by upthelum on 2008-04-24
Sounds good to me. VMWare is a good option you could get it running no worries in Ubuntu, i use it regularly. Or you could set up a dual boot machine/machines, or set up 1 machine with windows and keep it off the lan if need be, for running excel.

---

### Post by dorkdork777 on 2008-04-24
[Here's the link]("http://appdb.winehq.org/appview.php?iAppId=11") for the Wine AppDB entry for Excel. Seems as though the 2003 version runs OK, but it's definately worth testing before you deploy Linux. If Ubuntu doesn't play well with it, consider testing Fedora, openSUSE, Debian, SimplyMEPIS, PCLinuxOS, or whatever else, until you find one that works, or until you decide that a VM is simply a better option.

The reason I say this is because a VM will always be worse than a compatibility layer (i.e. Wine) because, with a VM, you're running two complete OSs at the same time.

---

### Post by #Reistlehr- on 2008-04-24
If you want, a probable idea would be to leave one windows box with all required windows apps, and just use rdesktop (terminal services) into the box, to use the required apps.

---

### Post by a8ksh4 on 2008-04-24
I like the idea of just running excel over an rdesktop.  That'd make it really easy to lock down the one or two windows clients on your network.  There's also the advantage of being able to leave sessions active for a long time, even when rebooting the user's desktop.  This has been useful for me at work.  It'd be pretty secure if you tunneled rdesktop over ssh, too.  :guitar:

--Dan

---

### Post by reiki on 2008-04-24
> **dorkdork777 said:**
> [Here's the link]("http://appdb.winehq.org/appview.php?iAppId=11") for the Wine AppDB entry for Excel. Seems as though the 2003 version runs OK, but it's definately worth testing before you deploy Linux. If Ubuntu doesn't play well with it, consider testing Fedora, openSUSE, Debian, SimplyMEPIS, PCLinuxOS, or whatever else, until you find one that works, or until you decide that a VM is simply a better option.

The reason I say this is because a VM will always be worse than a compatibility layer (i.e. Wine) because, with a VM, you're running two complete OSs at the same time.

thank you. yes I looked at the AppDB entry for Excel before posting here. Looks like there is a *possibility* of issues, but it might run fine. This would be my first choice.

---

### Post by reiki on 2008-04-24
> **#Reistlehr- said:**
> If you want, a probable idea would be to leave one windows box with all required windows apps, and just use rdesktop (terminal services) into the box, to use the required apps.
thanks for the response. This is an interesting thought... using rdesktop... but I'll have to look into it a bit more as I have very limited exposure to it. Last I tried it, it could only be used by one person at a time. If more than one person wants to work with the excel app simultaneously, would this still work? I mean would the windows box handle it?

I am planning on installing Ubuntu onto one of his "spare" computers. I think it's an Alienware. If everything works out then the next great challenge for me would be installing Ubuntu on his existing laptops. THAT could get interesting. :)

First things first though... I want to have a plan that at least sounds good and then proceed to test it on just one (non-critical) machine to prove the concept. And THEN worry about how to fully implement it once we know it's all functioning as expected.

---

