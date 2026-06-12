---
title: "edgy still using firefox 1.5 when 2.0 is installed"
date: 2007-01-15
forum: General Help
---

### Post by ibjohnnyl on 2007-01-15
My Ubuntu 6.10 system is still using Firefox 1.5.0.1 when i open firefox.
Synaptic says that 2.0.0.1 is installed on my system.
If i open a terminal and type "firefox" it will open 1.5.0.1.  
If i type in "firefox.ubuntu"  it will open Firefox 2.0.0.1  

All the firefox icons open 1.5.0.1,  but if i click on a link in an e mail (or something) the system will open 2.0.0.1

How do I get my system to stick with firefox 2.0.0.1?

I started with Ubuntu 6.06 and followed the "official" upgrade instruction to get Edgy 6.10.  
The upgrade worked great  and i haven't installed anything outside of Ubuntus own upgrades or repositories so i don't know how i broke this.  
any suggestions?

---

### Post by bscbrit on 2007-01-15
Have you tried uninstalling 1.5?  If its not there, it cannot start....

---

### Post by ibjohnnyl on 2007-01-15
I have read that you can't uninstall 1.5 because it will cause problems for Gnome and a lot of other stuff.

I never learned how to fix this problem myself,
but i got it working by using the installation script from this page. [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

reinstalling through synaptic didn't help but reinstalling with this script did.

Well I didn't learn anything but it's working again.  
fun

---

### Post by NeoLithium on 2007-01-15
Instead of untar'ing it inside your own /home/USER directory, try to untar it in /usr/lib instead, it will overwrite Firefox 2.0 on top of your 1.5, but keep your personal settings.

---

