---
title: "Only getting around half of my internet speed"
date: 2008-03-28
forum: General Help
---

### Post by ALIENDUDE5300 on 2008-03-28
Hello. I just recently installed Ubuntu and I am rather disappointed with how slow my internet speed is. Using speedtest.net, it says I have a speed of 7065kb/s download and 1205kb/s upload. I have an internet plan of 15Mb/s download and 2Mb/s upload. Under windows using the exact same test, I got 15743kb/s download and 1612kb/s upload. How can I fix this? For some reason it seems Ubuntu is capping my transfer rates. :(

---

### Post by zeronothing on 2008-03-28
the possible problem could be that ipv6 module is causing this problem. I have heard about issues with this before. for some reason by default ipv6 is enable during the installation. you could disable it because their is no use for ipv6 at this moment in time. to do so you could open up terminal and execute this on the commandline:

lsmod

this will show all of the modules loaded on your system. in the list loaded in terminal see if you can find one "ipv6" in the list. or you can execute this command:

ifconfig 

after you execute this command look to see if you find anything like "inet6 addr". if you do see anything like i mention aboved this means that the ipv6 is enabled.

to disable this open up the blacklist config file to disable the module from running:

sudo gedit /etc/modprobe.d/blacklist

add a new line to the file like this:

# this is to block the ipv6 module from loading
blacklist ipv6

add the two lines above to the blacklist then save it.

now restart your system to take the changes. when you system starts back up, open up terminal and execute lsmod and you shouldnt see the module "ipv6" anywhere in the list. if you do see it then something wasn't added to the blacklist config file right.

---

### Post by zeronothing on 2008-03-28
I should also mention if your using ubuntu 7.10 you should disable ivp6 lookup in firefox browser. to do this open up firefox. in the address bar type "about:config" hit enter. then in the "filter" textbox type in ipv6 (this will filter out the search). after you do that you will see something like "network.dns.disableIPv6", click on this to set the value to "true".

---

### Post by zeronothing on 2008-03-28
if you are using ubuntu 8.04 you can also disable the ipv6 feature in firefox 3. just use the same directions as I mentioned above for ubuntu 7.10.

---

### Post by wpshooter on 2008-03-28
My question is WHY do they/Ubuntu include this as enabled by default, if this service is not currently available ?

Why don't they set it up as disbled by default and then let the user that might need it (if there possibly are any) enable it when & if they need it ?

Or better yet, just leave it out of Ubuntu altogether until this protocol is needed.  Or is this protocol used in some parts of the world and not others ?

Thanks.

---

### Post by ALIENDUDE5300 on 2008-03-28
omg... disabling ipv6 worked like a charm... i'm now getting my full internet speed. =] Thanks!

---

### Post by zeronothing on 2008-03-28
I have no idea why they enable ipv6 by default. I do believe that ipv6 is being used in japan. I'm not totally sure on that, but some parts of the world are testing it out. I would also like to mention windows vista now also comes with ipv6 installed by default, so Ubuntu isn't the only OS to have it installed by default now. I glad I was able to help out.

---

### Post by dcstar on 2008-03-28
> **zeronothing said:**
> I have no idea why they enable ipv6 by default. I do believe that ipv6 is being used in japan. I'm not totally sure on that, but some parts of the world are testing it out. I would also like to mention windows vista now also comes with ipv6 installed by default, so Ubuntu isn't the only OS to have it installed by default now. I glad I was able to help out.

The problem isn't having IPv6 installed, the problem is when Ubuntu (and probably other Linuxes) incorrectly tries to use it rather than detecting that it is on a IPv4 only network and automatically disabling the protocol that cannot do anything but cause time-outs and other problems.

If the developers can sort out some code to correctly use v4 or v6 when appropriate then these issues would go away - and if a user was on an IPv6 connection they wouldn't have to do anything to fully utilise it.

---

