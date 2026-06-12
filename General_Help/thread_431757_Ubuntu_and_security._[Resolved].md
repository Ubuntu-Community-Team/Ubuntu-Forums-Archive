---
title: "Ubuntu and security. [Resolved]"
date: 2007-05-03
forum: General Help
---

### Post by kikapu on 2007-05-03
Hi to all here,

i am new to ubuntu and trying to catch up.
So, i have installed Feisty and use heavily the net through and adsl modem-router. I read that Ubuntu does not need a firewall like Windows do and i am curious if this is indeed true and how we are protected from viruses/malware and all these.

I also do some internet banking with Feisty, do you think that i am already secure for this or do i have to use some firewall-like mechanism for protection ??

---

### Post by 3rdalbum on 2007-05-03
Ubuntu doesn't need a firewall, as there are no openable ports in the default Ubuntu install.

It does come with a firewall (built into the kernel), but since you're using an ADSL router you probably already have a fully-configured firewall in the router.

We are protected because malware and viruses are written to run on Windows and cannot run on Linux; and Linux developers have a policy of fixing security flaws and implementing good security features to begin with. Due to the systems of "permissions" and the fact that all the user's programs and most system services run as a normal user and not an all-powerful administrator user, malware is difficult to write for Linux and at the moment does not exist.

With internet banking, plug your computer into the router (don't use wireless). A firewall provides no additional protection for your banking data; firewalls only protect services running on your computer, not data that you are transmitting to another party through the internet.

---

### Post by apunc1 on 2007-05-03
by default on ubuntu all ports are closed and will remain closed unless you allow them manually (ssh server for instance). you do not need a firewall unless you want one. the firewall in the repositores (whose name escapes me, firestarter?) has a gui interface where you can edit the iptables. i don't have any experience with that, but you can search the forum for help with this. i personally don't have any port open and use a hardware router with a NAT firewall between my computer and cable modem , so i don't worry about a software firewall.

no OS is 100%  safe from viruses but yes Linux is much safer than windows because virus writers are not targeting linux in full force as of yet and because ubuntu closes ports by default. Just keep up with the feisty security updates and you should be fine. don't allow repositories or download files from unknown source and you should be fine.
if you're worried about suspicious javascripts, run the noscript extension in firefox.

---

### Post by Chappy7777 on 2007-05-03
From my limited understanding of Linux, there is little need to be concerned about sevurity. It is almost a non-issue. If you were using Windows, and learned how to keep your PC safe, then you'll be fine on Ubuntu. I never opened attachments using Windows, and I guess I won't here. But, I doubt a virus attached to a windows created attachment would be able to effect this Linux Box (as stated above). 

Anyhow, there is an Anti Virus program called Clam AV/Clam TK that you can get thru the Synaptic. If you feel the need, search for "clamtk" and Synaptic will download it plus any other necessary files. I am not using it, because I have never had a virus using Windows since 3.1, so I feel like I'm ok. 

I did download and install a file called libmagick9. Look in this forum for my post on that from yesterday if you want. The problem affects 5.10 and 6.06LTS (I'm using 6.06). I got no responses and lots of views, so I kinda assume the libmagick9 thing must be a non-issue.

God bless and fear not,
Chappy  :)

---

### Post by kikapu on 2007-05-03
Ok, i think i understood this. Thank you all for helping me! :popcorn:

---

### Post by aysiu on 2007-05-03
Read this:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by kikapu on 2007-05-03
> **aysiu said:**
> Read this:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

Xmm..ok, a good one, thanks!

---

