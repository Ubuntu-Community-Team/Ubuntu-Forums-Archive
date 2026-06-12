---
title: "best firewall application for KUbuntu 15.04"
date: 2015-09-02
forum: General Help
---

### Post by alain.roger on 2015-09-02
Hi,

i would like to know what is the best firewall application under KUbuntu 15.04 ?
UFW has a nice GUI but nothing super and very userfriendly in Rule creation.

Any suggestion would be great.

thx.

---

### Post by TheFu on 2015-09-02
I like netfilter.  Anything over that is just a GUI. 

If you need lots of control, iptables is it. [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)  If you need simple, gufw.  There are entire books written about using netfilter with iptables with complex examples to handle almost any need you might have.  The user friendliness is slightly lacking, however.
> 
WARNING: Iptables and NetworkManager can conflict. Also if you are concerned enough about security to install a firewall you might not want to trust NetworkManager.  - from that link

Whatever you choose, pick 1 and only use that tool. Different tools are known to conflict. Bad things can happen.

In a few releases, the core Linux firewall will be changing for the first time in about 15 yrs.

---

### Post by Geoffrey_Arndt on 2015-09-02
I've always been happy with the default firewall settings.   Never had to adjust them, but I don't run any games that open/listen on ports etc.

Have you scanned your system for open ports?   [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

### Post by alain.roger on 2015-09-03
Hi Geoffrey,

in fact this is the result of grc.com test.[ATTACH=CONFIG]264204[/ATTACH]

---

### Post by TheFu on 2015-09-03
> **Geoffrey_Arndt said:**
> I've always been happy with the default firewall settings.   Never had to adjust them, but I don't run any games that open/listen on ports etc.

Have you scanned your system for open ports?   [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

By default, Ubuntu does NOT enable any firewall.  That may not be a good thing.

---

### Post by Geoffrey_Arndt on 2015-09-03
The way it's been explained to me is Linux distros in general don't pre-install the firewall front-ends, but IPtables is configured to only open the 3-4 most common ports in response to outgoing 8080, 443, smtp (whatever that port is, etc.).   

  I've done port forwarding in the past and setting rules via Suse Yast network tools, GuardDog, Shorewall, etc., but it was a pain to maintain over time.

To the Original Poster Alain . . . looks like your system is sound - - all ports closed and/or hidden.    May not need any firewall rules/tweaks beyond current settings.

---

### Post by TheFu on 2015-09-03
Other distros handle firewall rules differently. RHEL definitely enabled the firewall - whenever trying to make something work on RHEL - open the firewall, allow SELinux, setup the service. Those 3 things are needed.

Ubuntu doesn't have **any** firewall rules after install. If no service is installed, that is fine. If nothing is listening, can't break in.  If you run a server, you should know better and setup the firewall rules you want. That seems to be the idea with Ubuntu.

**sudo /sbin/iptables -L** to check.

---

### Post by QDR06VV9 on 2015-09-03
> **TheFu said:**
> Other distros handle firewall rules differently. RHEL definitely enabled the firewall - whenever trying to make something work on RHEL - open the firewall, allow SELinux, setup the service. Those 3 things are needed.

Ubuntu doesn't have **any** firewall rules after install. If no service is installed, that is fine. If nothing is listening, can't break in.  If you run a server, you should know better and setup the firewall rules you want. That seems to be the idea with Ubuntu.

**sudo /sbin/iptables -L** to check.
+1 TheFu is very wise(and skilled) in such matters. 
I just run a normal Desktop on 3 installs And 1 Server for backups and the such.
For my particular setups I install Privoxy, PGL, and enable ufw at startup, with only a couple of added rules.
For the past 8 years now nothing eventful has occurred outside the norm.
Just my 2cents
Regards

---

