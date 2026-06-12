---
title: "Cool Iptables feature bombs in Ubuntu 5.10"
date: 2005-10-20
forum: General Help
---

### Post by frobroj on 2005-10-20
Let me preface this with the fact that I am a total noob with iptables. However I am a noob that is dying to learn more.
OK down to the problem. I just installed a few ubuntu machines and am trying to get a really cool iptables piece working. It is a tagging piece that works in lieu of port knocking scripts. Personally, I think its the greatest thing since sliced meatloaf. It works great in all my fedora machines FC3, FC4, & RHEL4.
Anyway below is the snippet I am having problems with and an example of the error I am getting. Is there a module I am missing or something? 

Example code:

#iptables -A INPUT -m state --state NEW -m tcp -p tcp --dport 22 -m recent --rcheck --name SSH -j ACCEPT
#iptables -A INPUT -m state --state NEW -m tcp -p tcp --dport 4062 -m recent --name SSH --remove -j DROP
#iptables -A INPUT -m state --state NEW -m tcp -p tcp --dport 4063 -m recent --name SSH --set -j DROP
#iptables -A INPUT -m state --state NEW -m tcp -p tcp --dport 4064 -m recent --name SSH --remove -j DROP

Example error:

$ sudo iptables -A INPUT -m state --state NEW -m tcp -p tcp --dport 22 -m recent --rcheck --name SSH -j ACCEPT
iptables v1.3.1: Couldn't load match `recent':/lib/iptables/libipt_recent.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.


Any help is much appreciated. Thanks in advance!

My guess is that the iptables is compiled without the 'recent' module... Please tell me I dont have to recomplile iptables... Please...

---

### Post by frobroj on 2005-10-20
Is this in the wrong forum? Should I have entered it into the Networking?
Thanks!

Oh and for those who are curious what exactly this does.. It opens a port(ssh in the example) for a specific IP address after that source ip telnets to a specified port(4063 in the example). It is portknocking at its simplist level but it adds a huge layer of security.  If you get it working just remember what your mom said "Were you born in a barn?". Remember to telnet to either of the close ports(4062 or 4064 in the example) when your done. 

Thanks..

---

### Post by frobroj on 2005-10-20
Can a fella get some love???

---

### Post by psychic on 2005-10-20
[quote=frobroj]Can a fella get some love???[/quote]
Yeah, do what i do. get a girlfriend...

no seriously, be patient.
There are people that have an answer for your problem. 
Just give them time to reply.

---

### Post by xombie on 2005-10-20
"$ sudo iptables -A INPUT -m state --state NEW -m tcp -p tcp --dport 22 -m recent --rcheck --name **S** -j ACCEPT"

---

### Post by frobroj on 2005-10-20
Yeah the **S** is the name convetion I am using to test with on one of my work machines. I am doing this at home and at work. I think the 'recent' module is not installed. I will look around to see how I can determine that it is or is not installed.

Thanks..

---

### Post by frobroj on 2005-10-21
Pardon my Laziness and or Ignorance... 
Found this file "/usr/include/linux/netfilter_ipv4/ipt_recent.h" living in my Fedora box which works great. And it is nowhere to be found in the Ubuntu box. 

So I guess my question is... Is there any packages of IPTABLES that I can use from the repositories that have the 'recent' module compiled in them??? 

Thanks!

---

### Post by frobroj on 2005-11-08
FYI ---- I just found in some of my digging that the 'recent' module was accidentally left out of an unstable debian release and it has since returned to that released. The fine gentlemen at the ubuntu bug list said that if it was put back in the deb releases that it will also come back into ubuntu once they merge the new release.
[COLOR="Red"][B]
So in short build the script and the 'recent' package will come!!!
[/B][/COLOR]
Thanks all!

---

### Post by Arvin on 2005-11-24
Now,I think it's [ok]("http://forum.ubuntu-fr.org/viewtopic.php?pid=132610#p132610").

---

### Post by frobroj on 2005-11-24
YUP! Just got the latest IPTABLES update and Bingo! Problem solved!

jm

---

