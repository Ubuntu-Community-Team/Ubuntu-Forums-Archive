---
title: "How do I add a module to iptables after the fact?"
date: 2005-10-24
forum: General Help
---

### Post by frobroj on 2005-10-24
I need a particular module 'recent' built into iptables(I think). I had another thread going but it was about as popular as boys weekend at the vatican. Anyway.. What would all y'all suggest? Should I a) install iptables from scratch and compile it with the 'recent' module(pain in my fingers)?, b) rebuild the debian sources to include it(I have only built one rpm from src in a fedora dist and I was really lucky! This option = BAD I think..)? or c) Pray that one of the wonderful sage like ladies and gentlemen of the ubuntu forums knows of a package that includes the 'recent' module(This one is the house favorite!)?
Any imput would be most appreciated! THANKS EVERYONE!

---

### Post by Kyral on 2005-10-24
Isn't Iptables in the kernel? Yah it is. If you wanted to add a "module" to iptables you are looking at a kernel recompile

---

### Post by frobroj on 2005-10-24
Oh MAN! A lazier man than myself would say adios to the Big U and move on back to fedora... Well, I just might be that lazy..  Thanks for the reply Kyral! 
So does anyone know why or if the 'recent' package is not included in the kernel/iptalbes? And who do I need to bribe with booze to get it put in?  (Keep in mind, we make some ferocious beers here in Oregon!)

---

### Post by Kyral on 2005-10-24
What is the "recent" package? Can you show me a link?

(It actually sounds like the RELATED Iptables rule....)

---

### Post by frobroj on 2005-10-24
So here is what I really want to accomplish... I want the code below to work as it does in FC4... 
# ------- SSH Portknocking ------- #
iptables -A INPUT -m state --state NEW -m tcp -p tcp --dport 22 -m recent --rcheck --name S -j ACCEPT
iptables -A INPUT -m state --state NEW -m tcp -p tcp --dport 2091 -m recent --name S --remove -j DROP
iptables -A INPUT -m state --state NEW -m tcp -p tcp --dport 2092 -m recent --name S --set -j DROP
iptables -A INPUT -m state --state NEW -m tcp -p tcp --dport 2093 -m recent --name S --remove -j DROP
(Note: the port numbers have been changed to keep the innocent safe)

So it works great in FC but the big U gives me this error(shown below) when I try to imput a line of this...

iptables v1.3.1: Couldn't load match `recent':/lib/iptables/libipt_recent.so: cannot open shared object file: No such file or directory


Any Ideas?  THANKS!!

---

### Post by Kyral on 2005-10-24
Yah you have to enable it in the kernel. Which means a recompile. But its not to hard (Gets rather fun after a while :D)

[https://wiki.ubuntu.com/KernelHowto](https://wiki.ubuntu.com/KernelHowto)

---

### Post by frobroj on 2005-10-24
Gulp! Well I will try it on this server for fun... erh for practice... However, it makes the idea of moving the rest of the servers over a real bear of an Idea(guess they will stay FC for now).
 THANKS KYRAL!!!! I really appreciate getting a concrete answer! and The link is GREAT!!! 
Is there an avenue such as a suggestions site for us to try to get that module put into the Big U repo mix? I know that it wouldnt be too much work to keep the kernel up to date along with everything, however, once you start multiplying that by X amount of machines it gets that much more difficult.
Thanks again Kyral!

---

### Post by Kyral on 2005-10-24
I actually don't know why that IPTables option isn't in the current Ubuntu Kernels. The only thing I can think of is that it isn't in the 2.6.12 series that Breezy uses. I'm sure its in the 2.6.13 series

---

### Post by frobroj on 2005-10-24
Oh ok... I will give some other kernels a try. I will also play with the multitude of kernel patches there are, in hopes that one of them contains the module. 
Thanks!

---

### Post by Kyral on 2005-10-24
Try the vanilla kernel from Kernel.org first (Heck I'd only trust anything from Kernel.org)

---

### Post by frobroj on 2005-11-08
I am going to be lazy on this... I just found in some of my digging that the 'recent' module was accidentally left out of an unstable debian release and it has since returned to that released. The fine gentlemen at the ubuntu bug list said that if it was put back in the deb releases that it will also come back into ubuntu once they merge the new release.

So in short build the script and the 'recent' package will come!!!

Thanks all!
:smile:

---

### Post by frobroj on 2005-11-24
They just added the iptables with the recent package. An update of the iptables package makes it all better! [http://www.ubuntuforums.org/showthread.php?t=79467](http://www.ubuntuforums.org/showthread.php?t=79467)
jm


Can't figure out how to edit the title to say SOLVED or how to close the ticket. Help...

---

