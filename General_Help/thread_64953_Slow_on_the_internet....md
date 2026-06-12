---
title: "Slow on the internet..."
date: 2005-09-12
forum: General Help
---

### Post by TrailerTrash on 2005-09-12
One thing i can not figure out is how to speed up Ubuntu during web browsing. On my other distros i use PCLinuxOS, Xandros and sometimes Linspire  :roll: , my internet web browsing is very speedy...Ive noticed this slowness on other distros ive used like Ubuntu, Kubuntu, Mepis, BSDs, Kanotix and many others. I have a DSL 3meg connection and like i say, its blazing fast on PCLOS, Fedora, Blag, SuSE, Mandrake, Vector, Xandros, etc.......It takes forever to load a web page on Ubuntu..Even the repositorys are very slow to start, but once it starts then it is fast. I hope i make some sence here. Any ideas? Thanks
It make browsing the web not fun in Ubuntu until this gets fixed!

---

### Post by macgyver2 on 2005-09-12
[QUOTE=TrailerTrash]One thing i can not figure out is how to speed up Ubuntu during web browsing. On my other distros i use PCLinuxOS, Xandros and sometimes Linspire :roll: , my internet web browsing is very speedy...Ive noticed this slowness on other distros ive used like Ubuntu, Kubuntu, Mepis, BSDs, Kanotix and many others. I have a DSL 3meg connection and like i say, its blazing fast on PCLOS, Fedora, Blag, SuSE, Mandrake, Vector, Xandros, etc.......It takes forever to load a web page on Ubuntu..Even the repositorys are very slow to start, but once it starts then it is fast. I hope i make some sence here. Any ideas? Thanks
It make browsing the web not fun in Ubuntu until this gets fixed![/QUOTE]
Well...there's some Firefox-specific stuff you can do that can make web browsing feel snappier...look about a third of the way down [this page]("http://www.linuxjournal.com/article/8317").  Also, parts [one]("http://www.linuxjournal.com/article/8308") and [three]("http://www.linuxjournal.com/article/8322") are good reads.

---

### Post by arnieboy on 2005-09-13
[QUOTE=TrailerTrash]One thing i can not figure out is how to speed up Ubuntu during web browsing. On my other distros i use PCLinuxOS, Xandros and sometimes Linspire  :roll: , my internet web browsing is very speedy...Ive noticed this slowness on other distros ive used like Ubuntu, Kubuntu, Mepis, BSDs, Kanotix and many others. I have a DSL 3meg connection and like i say, its blazing fast on PCLOS, Fedora, Blag, SuSE, Mandrake, Vector, Xandros, etc.......It takes forever to load a web page on Ubuntu..Even the repositorys are very slow to start, but once it starts then it is fast. I hope i make some sence here. Any ideas? Thanks
It make browsing the web not fun in Ubuntu until this gets fixed![/QUOTE]
take a look at this post. it should solve ur woes:
[http://www.ubuntuforums.org/showthread.php?t=38646](http://www.ubuntuforums.org/showthread.php?t=38646)

---

### Post by TrailerTrash on 2005-09-13
Thanks, but its not a firefox issue......It dose this on all browsers....OK,,,When i click on something or even use Synaptic and even apt-get..there is at least a 10-15 second delay before anything starts loading and then the progress bar goes halfways (on the browser) and stalls for about 5 seconds and then the pages load. This did not happen in Warty, but it dose in Horay and Brezzy. If i cant figure this out then i will dump Ubuntu. Thanks! Please help!  ](*,)

---

### Post by palough on 2005-09-13
I am having the same problem. I also run Xandros and it is very fast.  I experiment with several Linux flavours, and find Knoppix especially fast on the web, almost instant.  I like Ubuntu and am planning a slow switch from Xandros to Ubuntu but unless I can solve this slow internet browsing thing I will have to stay with Xandros.

As a note, I did not have this problem with Ubuntu 5.04, only with the new installation of Breezy Badger.  I have the same problem in both wireless and direct cable, whereas before with Ubuntu V5.04 the cable was noticably faster than wireless.  With Breezy Badger both are unacceptably slow.  

I have used Gaelon before with Xandros and Mandrake and it is even faster than Firefox and Konquerer, so I installed it into Ubuntu, and it is exactly the same as Firefox, pitifully slow to the point where one could go and make a cup of coffe and the page will still not have loaded !.  

I installed Ubuntu on two friends notebooks, one installation is the same as mine, slow, while on the other notebook it is quite acceptable, still not Linux fast but acceptable. It has to be a tweak inside Ubuntu somewhere.

Anyone else having this problem?

Cheers   ](*,)

---

### Post by TrailerTrash on 2005-09-14
LOL palough! Maybe you and I are the only ones having this problem. Using Ubuntu feels like im on dial up....I had cable modem and its working at the same speed as DSL..No diffrence.

It takes about 45sec just to load this forum on Ubuntu. It takes 3 to 5 sec at the most to load this forum on PCLOS.  ](*,) Thats from click to full page load.

---

### Post by bob_c_b on 2005-09-14
I ran in to this behavior on my last Mandriva install, turned out the DHCP daemon was autofilling my first DNS entry with my router/gateway (192.168.4.1). I would type in a URL, it was search local DNS/host table, then my router and then finally forward the request to my ISPs DNS server. Every request was taking 5-12 seconds instead of my usual near instant acknowledgement. I editted the router's DHCP settings to exclude itself and pass my ISPs DNS servers first and that really sped things up. I have seen this behavior on Linksys and D-Link routers with 2 flavors of Linux. Might be worth a look.

---

### Post by guivega on 2005-09-15
Hi guys!

I'm comming from this forum:
[http://ubuntuforums.org/showthread.php?t=65170&highlight=dns](http://ubuntuforums.org/showthread.php?t=65170&highlight=dns)

I doesn't look the same but it is probably the same reason, Ubuntu is not able to discover dns by itself in some instalations and working with some routers. Mine is a dlink DSL-G604T.

Anyway, here is what it worked for me (copy paste from the oder forum)


1) I logged in as root in gnome, (do a search in ubuntuforums to know howto)

2) Then I opened System>Administration>Networking

3) Make sure you select or add a location, I selected ubuntu (it was already there but for some reason it is not selected by default)

3) Add a host: Ip=127.0.0.1 and my computer name (ubuntu)

4) add dns: (check your isp dns servers) mine are 202.188.0.133 and 202.188.1.5

5) Then apply. ok, logout and login as my normal user

and everything was working

Now, the weired thing is that If I do System>Administration>Networking again it takes a while to start and all the settings are gone, so, i don't dare to go there again! (if anyone has a solution for that... shout it!)

I'm not saying this is the solution, but it is something to try.

I also use DMZ for the ip of the ubuntu computer, and to make sure that the router uses always the same ip for my ubuntu computer I enter the MAC address for the ethernet card and the IP that I want for it in the HOME>DHCP>STATIC DHCP SERVER of the dlink router web configuration manager.

try it and let me know if it makes any difference in you machine

Guillermo

---

### Post by TrailerTrash on 2005-09-15
Thanks, but it did not work..It is still very slow.  :mad:

---

### Post by ricesteam on 2005-09-17
I installed breezy on both my desktop and laptop to test it out.

On the desktop, everything worked perfectly.  Internet was fast.  Fast DNS lookup.  I didn't have to go configure any networking configs.

On the laptop however, even manually entering my DNS from my ISP into the network settings, internet is still slow.  (Although it did quicken the lookup of URLs)

I use a D-link router at home.

I'm just confused why the desktop install was flawless, but the laptop install was buggy.

Other problems with the laptop install, was that there is no boot splash screen, but on the desktop there was....im installing Breezy from the same ISO on the same CD.

Wierd.

---

### Post by fakie_flip on 2005-11-08
Normally a dial up user can get 5/6kb/s most, but 1kb/s at most on Ubuntu. Besides this, Ubuntu is a great distro. The problem causing Ubuntu to load webpages slowly might be different for a DSL user and a dial up user. I do not have this problem with DSL on Ubuntu, but my friend does who is new to Linux with dial up. It is making him want to go back to XP where he had the many virus problems before. Also getting Opera has been difficult for him. It required libraries that were not showing up with the exact names in Synaptic. Some names to packages in Synaptic were similar but not the same. I looked up these packages on Debians deb search and found that the packages he needs requires a lot of other packages. Those packages might require more packages. I wish I could remember what I did to get Opera working, so I could tell him. What would be a distro for loading webpages fast for a dial up user?

---

