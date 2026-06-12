---
title: "Performance issues"
date: 2004-11-08
forum: General Help
---

### Post by Klunk on 2004-11-08
I have just installed Ubuntu on my machine having used Red Hat 8.0 for a few years.

My machine spek is as follows:

AMD Athlon 1GHz
512MB RAM
80GB Hard Disk - bought especially for this to preserve my Red Hat installation.
40GB Hard Disk - old home directory
Generic CD Rom
Asus motherboard - can't remember exact spec.

Sounblaster 16 Bit motherboard (not currently working)
2x Linksys 10/100 Ethernet cards (One internal network and one connected to ADSL router)
Matrox Millennium II (G400) graphics card - 16Mb

I have a base Ubuntu install. I have reconfigured x to work at 1280x1024 and that all works fine. I have added a dhcp3 server (using my config file from my old machine) and done the same with Samba. I have installed XMail ([www.xmailserver.org](www.xmailserver.org)) which I used under Red Hat, actualy I again copied this from my old machine.

Finally I am running a firewall script (iptables) and using this to route internal traffic through to the ADSL router. Again this was copied from my previous install.

I basically have 2 problems, the machine generally seems to work quite fast, starting apps like eclipse and open office very quickly. However, the network seems to be slow. Firefox starts quickly, pointing to a file, but as soon as I try to go to a web site it seems to be painfully slow. Internal machine also seem to have slowed down when accessing the Internet through this router.

Has anyone got any network diagnostic applications that I can use or can you suggest anything I can do to speed this up ?

---

### Post by knappen on 2004-11-08
Have you tried to disable IPv6?

---

### Post by khc on 2004-11-09
Is it slow for name resolving or general network slowness? Say if you enter the IP address directly, is it significantly faster?

---

### Post by FLeiXiuS on 2004-11-09
Yes i would reccommend disabling Ipv6.  You will see a overwhelming increase of network performance.

The latest version of Mozilla includes support for "IPv6" a new form of addressing things on the Internet.

**To fix this issue follow these steps:**
```
sudo nano /etc/modutils/aliases
```
**Look for this line:**
```
# alias net-pf-10 off # IPv6
```

**Change the line to: (remove the #)**
```
alias net-pf-10 off # IPv6
```

```
sudo update-modules
```

---

### Post by knappen on 2004-11-09
I dont know if it makes any difference after you do the above, but if you run about:config in Firefox you can disable this line:

network.dns.disableIPv6

Set this line as "true"

---

### Post by Klunk on 2004-11-09
Thanks guys, I will take a look at IPv6, although I have a feeling it is the name resolution that is slow. 

I might have my router set for name resolution, I will chane it to my ISPs name servers and see if that helps.

---

### Post by mdr on 2004-11-09
hmmm, as usual with a debian distro behind my dsl router - it keeps forgetting the ISP server dns server addy that I manually add (when set to using DHCP from the router)

however - when manually added (again) and browser re-started network browsing is fine. (i.e. none of the "Host DNS is being resolved" for like an age).

will try the moz IPv6 fix.

---

### Post by Klunk on 2004-11-09
Wow that did the trick.

Lightning quick intenet access now I have done the IPv6 thing and changed my DNS settings.

Thanks for the help.

---

### Post by mdr on 2004-11-11
the moz ipv6 trick worked for me too btw...

no longer the slow dns resolution issue, whilst using DHCP too.

I guess the issue for us using basic routers is that the router generally acts as a DNS proxy and using IPv6 may cause some issues with that ?

---

### Post by CAPTAIN RON FL on 2004-11-15
Where do you go to type in the things to change?? I tried the Run application and it did not do anything.  I guess I am asking how to get to the command line [ I think that is what it  is called] .???? Thanks, Ron

---

### Post by jdong on 2004-11-15
[QUOTE=CAPTAIN RON FL]Where do you go to type in the things to change?? I tried the Run application and it did not do anything.  I guess I am asking how to get to the command line [ I think that is what it  is called] .???? Thanks, Ron[/QUOTE]

**Applications -> System Tools -> Terminal**.

The command line is a very powerful part of Linux -- unlike the Windows command prompt. I recommend dragging the Terminal menu to the "quick launch" bar, for easy access in the future.

---

### Post by FLeiXiuS on 2004-11-15
[QUOTE=jdong]**Applications -> System Tools -> Terminal**.

The command line is a very powerful part of Linux -- unlike the Windows command prompt. I recommend dragging the Terminal menu to the "quick launch" bar, for easy access in the future.[/QUOTE]


Right clicking on the desktop is a nifty feature also :-)

---

### Post by HungSquirrel on 2004-11-15
> Right clicking on the desktop is a nifty feature also
One of my very favorite features of Gnome!

---

### Post by CAPTAIN RON FL on 2004-11-15
OK I did that, but I can not seem to get the # to go away. I log in , did the sudo nano /etc/modutils/aliases. Got the page, found the code # alias net-pf-10 off # IPv6.  Tied to delete it with the delete button. pulledup a new terminal and ran the code sudo update-modules. Then closed the file for both. Then went back and checked and the # was still there.  What did I do wrong.?? I am trying to do this before I tackle my sound problem. I did check to see if there were any mutes, but were none. Also did the change password. So far so good. Just minor gliches with my know how.  ](*,)  Thanks, Ron

---

### Post by Rodney on 2004-11-15
Try -

sudo gedit /etc/modutils/aliases

then use the backspace and click save

---

### Post by FLeiXiuS on 2004-11-16
[QUOTE=CAPTAIN RON FL]OK I did that, but I can not seem to get the # to go away. I log in , did the sudo nano /etc/modutils/aliases. Got the page, found the code # alias net-pf-10 off # IPv6.  Tied to delete it with the delete button. pulledup a new terminal and ran the code sudo update-modules. Then closed the file for both. Then went back and checked and the # was still there.  What did I do wrong.?? I am trying to do this before I tackle my sound problem. I did check to see if there were any mutes, but were none. Also did the change password. So far so good. Just minor gliches with my know how.  ](*,)  Thanks, Ron[/QUOTE]


RTFM :-)  

```
man nano
```

---

### Post by CAPTAIN RON FL on 2004-11-16
OK, thanks for pointing out the how to bring up the nano manual. I still can not figure them out. I went to the web site. Read all the info and I do not see the connection. It is a writing tool for email???? What does that have to do with trying to get web pages to open faster??? 

Anyway I did what Rodney said to do [ sudo gedit /etc/modutils/aliases ] This worked but the speed of opening pages on ebay stayed the same. Running windows ME, they open twice as fast. I really need this feature as I am doing ebay to make money since I fractured my back , neck and shoulder and won't be able to run charter for awhile. Any sugestions as to how to make the web pages open quicker? Or maybe I did something wrong??? Thanks, Ron

---

### Post by knappen on 2004-11-17
Did you change the IPv6 settings in Firefox?

---

### Post by CAPTAIN RON FL on 2004-11-19
Yes I tried that. It did help somewhat. I finally gave up and switched to Mandrake 10.1 ce. I could not find anyone to help me get my cd player to work. I keep checking the forms to see if anyone has had the same problem.  I would like to go back to Ubuntu if I get it working. I have a couple of desktops and a couple of laptops I need to have working. I want to use the same distro for each. Thanks for all the help with everything else. Ron

---

### Post by Ozitraveller on 2004-11-20
[QUOTE=knappen]I dont know if it makes any difference after you do the above, but if you run about:config in Firefox you can disable this line:

network.dns.disableIPv6

Set this line as "true"[/QUOTE]



Could someone explain how I do this please :run about:config in Firefox.

I've done the bit before, but just don't understand this bit.

thanks

---

### Post by Ozitraveller on 2004-11-20
[QUOTE=Ozitraveller]Could someone explain how I do this please :run about:config in Firefox.

I've done the bit before, but just don't understand this bit.

thanks[/QUOTE]
 Found it!

---

### Post by bob k on 2004-11-20
[QUOTE=CAPTAIN RON FL]Yes I tried that. It did help somewhat. I finally gave up and switched to Mandrake 10.1 ce. I could not find anyone to help me get my cd player to work. I keep checking the forms to see if anyone has had the same problem.  I would like to go back to Ubuntu if I get it working. I have a couple of desktops and a couple of laptops I need to have working. I want to use the same distro for each. Thanks for all the help with everything else. Ron[/QUOTE]
 Did you try xmms to get your cd audio working?

---

### Post by knappen on 2004-11-21
[QUOTE=Ozitraveller]Could someone explain how I do this please :run about:config in Firefox.

I've done the bit before, but just don't understand this bit.

thanks[/QUOTE]
 Just type

about:config

in Firefox. Scroll down until you find that line and change it to "true".

---

### Post by kamstrup on 2004-11-21
[QUOTE=Ozitraveller]Could someone explain how I do this please :run about:config in Firefox.

I've done the bit before, but just don't understand this bit.

thanks[/QUOTE]
 In the location bar just enter "about:config" and hit enter.

---

### Post by knappen on 2004-11-22
[QUOTE=kamstrup]In the location bar just enter "about:config" and hit enter.[/QUOTE]
 Exactly :-)

---

### Post by Ozitraveller on 2004-11-22
Thanks guys. It's changed.

---

### Post by Ozitraveller on 2004-11-22
Still can't get sound to work. It's doesn't work in debian either. But it does in red hat 9.

---

### Post by knappen on 2004-11-22
Sorry cant help you there.

Perhaps you can start a new thread with that problem.

---

### Post by jdong on 2004-11-22
[QUOTE=Ozitraveller]Still can't get sound to work. It's doesn't work in debian either. But it does in red hat 9.[/QUOTE]
 Start a new topic on your sound problems... come on, this ain't Microsoft Tech support... We don't ask for your credit card within 1 minute of your post... lol

---

### Post by jdodson on 2004-11-22
[QUOTE=Ozitraveller]Could someone explain how I do this please :run about:config in Firefox.

I've done the bit before, but just don't understand this bit.

thanks[/QUOTE]

yeah put the text "about:config" minues the quotes in the address bar in firefox.  it will bring up a config screen.  search for ipv6 and then click it to make it say "disable=true"  this turns off IPV6 which slows down firefox browsing.

i hope that helps:)

---

### Post by nuopus on 2004-12-07
[QUOTE=CAPTAIN RON FL]OK, thanks for pointing out the how to bring up the nano manual. I still can not figure them out. I went to the web site. Read all the info and I do not see the connection. It is a writing tool for email???? What does that have to do with trying to get web pages to open faster??? 

Anyway I did what Rodney said to do [ sudo gedit /etc/modutils/aliases ] This worked but the speed of opening pages on ebay stayed the same. Running windows ME, they open twice as fast. I really need this feature as I am doing ebay to make money since I fractured my back , neck and shoulder and won't be able to run charter for awhile. Any sugestions as to how to make the web pages open quicker? Or maybe I did something wrong??? Thanks, Ron[/QUOTE]
 Are you sure that it is REALLY disabled? Go to terminal and type sudo ifconfig and see if you have an ipv6 address.

I could NOT get ipv6 disabled in Ubuntu! Here is what I have done:

1. vi /etc/modutils/aliases and uncomment alias net-pf-10 off # IPv6 then ran update-modules.
2. vi /etc/modules.conf to make sure that those changes ACTUALLY took .. yep.
3. Remove the entire ipv6 directory from my kernel modules directory.

Now .... in most other distros step 3 should have done it .. but in the stock ubuntu kernel there is STILL ipv6! Is it cached? If it is not where is it getting the module information? NOTE: I sudo rm -rf /lib/modules/2.6.9-1-686/kernel/net/ipv6 and verified it was gone.

I did that about:config thing in the address bar and it worked ... even in epiphany with good inet access ... but not being able to disable ipv6 is still bugging me.

---

### Post by kamstrup on 2004-12-08
I am seeing the same thing... How do I get rid of the ipv6 module? For real this time ;)

---

### Post by spark9905018 on 2007-05-15
Spam.

---

