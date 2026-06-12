---
title: "Web Sites Stall (UNSOLVABLE!)"
date: 2007-07-22
forum: General Help
---

### Post by CRuckis on 2007-07-22
Ok, I have seen many threads about this topic, and NONE seem to present a solution to this issue.

I created a post in the newbie section ([http://ubuntuforums.org/showthread.php?t=505591](http://ubuntuforums.org/showthread.php?t=505591)) and after trying several different things, some website will not load for me.

The Problem: After clicking the link or typing in the webpage, the site will *never* load. Status bar either remains at the half way point or stays empty. The window does not display any image, (I've waited up to 30 minutes). If I clicked a link, it will remain on the page that the link was located. Or if it was typed in the address bar, the page will remain white.

What I've tried: I have gone in terminal and pinged the sites, no packet loss. I have tried renaming the [/.mozilla/firefox] folder, no success. I tried switching browsers (from firefox to opera), also no success. All the computers connected to my network can access these sites with no problem.

Current known websites it is affecting:

[www.binghamton.edu](www.binghamton.edu)
busi.binghamton.edu
Go to citibank.com and click the "sign on" button in top right, that page won't load.
newegg.com
For those familiar with facebook, I can access, post etc, but for some reason cannot poke!


I'll post more that don't work as I find them.

ANY solutions or ideas are gladly accepted!!!

NOTE: I was experimenting and I WAS able to access these sites through foxyproxy.com, however, this is a major inconvenience as it is slower and I cannot login to these sites.

Thanks in advance!

---

### Post by zanglang on 2007-07-22
Have you tried accessing the sites from a newly created user profile and see if they work?
Might be useful if you try and test on alternative browsers. Try 'w3m www.bingmingham.edu' and see if the website text renders properly?

---

### Post by CRuckis on 2007-07-22
I punched that into terminal, got this :(

```
chris@sidewinder:~$ w3m www.bingmingham.edu
w3m: Can't load www.bingmingham.edu.
```

And do you mean create another user profile for Ubuntu?

---

### Post by zanglang on 2007-07-22
Ack, sorry, misread your url. :P Should be:
> w3m [www.binghamton.edu](www.binghamton.edu)

No, I meant a new Firefox profile. Type this
> firefox -ProfileManager
Create a new profile following instructions, and start Firefox with the new profile selected (you can switch back to your old profile with the same command). Now try the URLs you mentioned and see if they work?

---

### Post by CRuckis on 2007-07-22
Haha, you'd think I would have caught on to the URL mistake haha. Ok, with the corrected URL, it does the same thing that it would do in mozilla or opera. It says at the bottom of Terminal:

```
www.binghamton.edu contacted. Waiting for reply...
```

So bizarre. Since it doesn't work in opera either, I doubt creating a new mozilla profile will work but I'll try for the hell of it, anything to get this fixed.

Edit: Tried switching profiles, no dice :(

Also, terminal is still waiting for reply.

---

### Post by kvonb on 2007-07-22
that binhhamton worked on my Firefox!

There are some recent firefox updates, have you installed those?  I haven't yet, maybe I shouldn't :).

You could also try from the LiveCD, see if that works.

It could be an ISP problem too I expect!

Do you have Firefox set to go through a proxy?  Maybe turn it off, even if it isn't, make sure it's not set to auto, or just play with the proxy settings to see if it makes a difference.

Also have a look on your menu under System->Preferences->Network Proxy, try playing with those settings too.

---

### Post by CRuckis on 2007-07-22
When I installed I installed from the alternate, so i don't have a live CD... and as far as proxy settings, both are set to no porxy... I tried toying around with the settings on each but it didn't change anything. This is so weird.

I don't think it has to do with Mozilla at all, because the code I pasted above shows that terminal can't load it either. Neither can opera!!

---

### Post by zanglang on 2007-07-22
Hm. At least it doesn't seem to be your problem, but with your internet access... I think it's likely you're somehow getting blocked from accessing these sites by HTTP.
Are you accessing it from your own internet account, or through some transparent school/work proxy server?

---

### Post by CRuckis on 2007-07-22
Nope, simple home network. My computer is connected via lan to a Dell, that is wirelessly connected to a router. The dell computer is completely unprotected for the time being, no firewall or any anti-anything running. The dell can access these sites fine, however mine cannot. The dell has ICS on so that it can share the internet connection with me.

---

### Post by zanglang on 2007-07-22
I wonder if it's the Dell's problem... Is it possible for you to directly connect your computer to the router via LAN?

Also, can you access [http://bingwww.binghamton.edu?](http://bingwww.binghamton.edu?)

---

### Post by CRuckis on 2007-07-22
I tried it...still doesn't work :|

What could this be?! :confused: :mad:

EDIT: Nope, won't load that either.

---

### Post by kvonb on 2007-07-22
Can you access secure sites like logging into Hotmail etc'?

Do you use a pppoe connection to connect to the net?

It might be an MTU packet size problem (Maximum Transmission Unit).  I had the same thing when I started to use a pppoe connection!

Check your MTU with ifconfig, and also ring your ISP and ask them what it should be.

Mine is 1432, which is far less than the standard 1500, and I was having a similar problem.

---

### Post by CRuckis on 2007-07-22
How can I change my MTU?

Also, don't know if this helps...

```
chris@sidewinder:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:A5:BE:A2:ED  
          inet addr:192.168.0.250  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::202:a5ff:febe:a2ed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:49908 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32968 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25207707 (24.0 MiB)  TX bytes:4440221 (4.2 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)
```

---

### Post by kvonb on 2007-07-22
> **CRuckis said:**
> How can I change my MTU?

It depends on which device is actually connecting to your ISP, if you have a router/modem that connects, and you connect to that, changing the MTU on your computer might not make any difference.

But try this from a command prompt:

```
ifconfig ethX mtu 1432
```Obviously replacing the X with your network connection

You can save it by editing /etc/network/interfaces and adding the line mtu 1432 just after the device name like so:

```
auto eth0
iface eth0 inet dhcp mtu 1432
```I think that should do it, but I could be wrong, I'm no expert sorry :(

But if your main system is connecting via pppoe, then edit /etc/ppp/peers/dsl-provider (or whichever one you use, it will be in that folder).

This is an excerpt from mine:


```
hide-password
lcp-echo-interval 20
lcp-echo-failure 3
# Override any connect script that may have been set in /etc/ppp/options.
connect /bin/true
noauth
persist
mtu 1432

# RFC 2516, paragraph 7 mandates that the following options MUST NOT be
# requested and MUST be rejected if requested by the peer:
# Address-and-Control-Field-Compression (ACFC)
noaccomp
# Asynchronous-Control-Character-Map (ACCM)
default-asyncmap

plugin rp-pppoe.so eth1
user "notforyoutoknow"
```

Then disconnect/reconnect with the commands:

```
sudo poff
sudo pon dsl-provider
```

...or reboot!

Hope that helps :)

---

### Post by CRuckis on 2007-07-22
noobie question :D

how do I let root give me access to change that file?

put sudo in first in terminal right?

also I can't get permission to edit that file...

---

### Post by kvonb on 2007-07-22
> **CRuckis said:**
> noobie question :D

how do I let root give me access to change that file?

terminal won't let me edit and it won't let me replace the text file either

oh, sorry.  If you are using Gnome, then simply press alt-f2 and type:

gksu gedit /etc/network/interfaces

and press enter.

You can replace the editor with "kate" if you are using KDE, and of course any filename you want to.

But be careful, you could mess things up!

You might want to do it from a terminal, you can use the same command, but use simply "sudo", not "gksu".  Also you could make a copy of the file first, using this command:

sudo cp /etc/network/interfaces /etc/network/backup-of-interfaces

Then you will have a backup just in case :)

---

### Post by CRuckis on 2007-07-22
That was exciting, I managed to crash Ubuntu! It wouldn't boot cause I messed something up, but I'm happy because I was able to repair everything on my own, and that seems to be the only way I ever learn. Just look at Windows, I've crashed it hundreds of times and I'm a pro now, but i hate it, this is so much better! Now, I need some rest its almost 5 in the morning i'm exhausted. I'll be back on tomorrow to work on it and hopefully I won't be an idiot and crash Ubuntu again. Thanks for all your help so far! Even if it hasn't been solved yet I'm gaining equisite knowledge of Ubuntu and how it works. Thanks again! ;)

---

### Post by kvonb on 2007-07-22
You're welcome :)

It is very satisfying once you have learnt a few things and are able to fix things yourself.

Can you tell me how you connect to the net please, that might help me or someone else give you better info?

Regards, Kev :)

---

### Post by Absorbed on 2007-07-22
I had a similar problem in Firefox. All pages would load properly except slashdot. It would load somewhat, but seemed to stop before it was fully loaded. I fixed it by Tools... Clear Private Data.

---

### Post by CRuckis on 2007-07-22
> **kvonb said:**
> You're welcome :)

It is very satisfying once you have learnt a few things and are able to fix things yourself.

Can you tell me how you connect to the net please, that might help me or someone else give you better info?

Regards, Kev :)

OK, I am not sure how my connection really works, but here's how it's set up.

The router is connected to the modem in another room and has a wired connection to a dell laptop. In my room, I have a dell desktop that is connected to the router wirelessly. Now here's the part where I was amazed this worked - I connected an ethernet cable from the dell desktop to this laptop, and Ubuntu is able to connect to the net. I'm guessing that the Dell has ICS on and is sharing the connection with this computer, that's the only thing that makes sense.

---

### Post by CRuckis on 2007-07-22
> **Absorbed said:**
> I had a similar problem in Firefox. All pages would load properly except slashdot. It would load somewhat, but seemed to stop before it was fully loaded. I fixed it by Tools... Clear Private Data.

Not sure that this is the problem though, because it won't load in terminal or opera either :\

---

### Post by kvonb on 2007-07-22
OK, so if you put a cable from your Ubuntu computer into the router, can you get the net then, and do those pages now work?

If so, then It's starting to sound like a wireless problem to me, which I can't help you with unfortunately.

> **CRuckis said:**
> The router is connected to the modem in another room and has a wired connection to a dell laptop. In my room, I have a dell desktop that is connected to the router wirelessly. Now here's the part where I was amazed this worked - I connected an ethernet cable from the dell desktop to this laptop, and Ubuntu is able to connect to the net. I'm guessing that the Dell has ICS on and is sharing the connection with this computer, that's the only thing that makes sense.

---

### Post by CRuckis on 2007-07-24
Yup, it has something to do with the connection in between the dell and my laptop, plugging it into the router worked. Solution partially solved.

---

### Post by TAEAS on 2007-07-30
try sudo ifconfig eth1 mtu 1460

sorry did not see the previous post, but this worked for me.

---

