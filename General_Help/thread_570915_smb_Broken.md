---
title: "smb Broken"
date: 2007-10-08
forum: General Help
---

### Post by nubie777 on 2007-10-08
I've got myself in a mess. :lolflag:

I use to be able to access a w2k disk drive via smb. Nautilus would ask for a password, i would enter it,  and a few seconds later I could access the w2k disk drive.  The following line was displayed in the Nautalus location bar: smb://Administrator@server01/Data1 where Administrator is the w2k  logon user id,  server01 is the name of the w2k machine and Data1 is the share name.  Now I get the error message: "The contents could not be displayed." It does not even ask for a password.  

I believe it is a smb problem, but it may also be intertwined with iptables.  When iptables is runing I cannot ping the w2k machine.  Error message is: "Operation not permitted."  On the w2k machine, i cannot ping ubuntu also.  When I turn iptables off, via Firestarter, I can successfully ping in both directions.

I have internet access on ubuntu.

I think I have two problems.  The first is iptables will not let me access the w2k machine because I can't ping the w2k box.  The second (maybe) is a problem with smb since it no longer requests a password.

Any suggestions would be most appreciated.

Cheers!

---

### Post by jimmywu013 on 2007-10-08
Did you install Firestarter recently?
I had a similar problem - being unable to access network shares and network printers, which I am relatively confident was related to installing Firestarter.  Of course, I did a lot of other installs/messing around with system configuration at the same time, so I can't be sure.  What I do know is that one day, I suddenly stopped being able to see the shares with Nautilus (same message as you).  What was strange was that if I typed in the local network ip of the other computer into nautilus (like smb://192.168.1.101/share_name), the share contents became visible.  Anyways, while fruitlessly searching forums for various possible explanations, I eventually screwed things up more by editing various network settings configuration files without knowing what I was doing.  Eventually, my whole network was completely borked, and I even lost DNS resolution for the internet, so I couldn't do anything.  Being rather busy and having spent all the time on the problem I could afford, I eventually gave up and completely reinstalled the system.

Sorry for such a long post about my smb woes.  I'll try to summarize what parts of any of this could possibly help you.

- Try using smb://Administrator@ip_of_server01/Data1 and see if that works.  Although, even if it does, something is still wrong with Nautilus

- About not being able to ping: perhaps you could take a look at your iptables filters and see what rules Firestarter has set.  (the command is iptables -L -v, you'll probably need sudo).  Not being able to ping could mean either only icmp packets are blocked, or all connections.  That's why you'd have to look at your rules to see.  

- Try uninstalling Firestarter altogether and restarting your network and see if that makes any difference.  
After reinstalling my system, my network shares came back.  This time, I've shied away from Firestarter and I configure manually iptables with my own set of rules, and things seem to be working fine.

HTH, and good luck,

Jimmy

---

### Post by nubie777 on 2007-10-09
Jimmy, 
Thank you very much for your reply.  I appreciate the all the detail and solutions you provided.  I was able to get access to my w2k share by substituting the hard ip address.  As for iptables, I installed arno-iptables-firewall. I found this while searching the web for a standard iptables script.  The url for arno is:[http://rocky.eld.leidenuniv.nl/](http://rocky.eld.leidenuniv.nl/)  if you are interested.

Thanks again.

Cheers.
:)

---

### Post by jimmywu013 on 2007-10-09
Glad I could help, and good to hear that you got it working.  
I'm actually relatively new to Ubuntu myself, and am usually on the asking end of things.  The Ubuntu community is really great.  

Jimmy

---

