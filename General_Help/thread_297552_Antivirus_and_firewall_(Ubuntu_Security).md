---
title: "Antivirus and firewall (Ubuntu Security)"
date: 2006-11-11
forum: General Help
---

### Post by xenoalien on 2006-11-11
Are anti-virus and firewall applications needed for Ubuntu to insure security? I heard there are only 3 known viruses for linux. Do I need to install antivirus and/or a firewall or will I be okay without it?

---

### Post by taurus on 2006-11-11
More likely you would be okay without them but you can install an antivirus, AVG, if you wish and for firewall, use firestarter...  Just don't run services that you don't need on your machine and you should be fine.

---

### Post by kvonb on 2006-11-11
It's funny, looking back at coming cold turkey from Windows.  You get so used to virus checkers and spyware that you feel naked and paranoid when you first come to Linux.

But don't worry too much about virus etc', I haven't got anything loaded on my system, not even a firewall (it is silent and built in as default).

Ubuntu and Linux in general don't suffer from virus attacks and malware, Canonical even go so far as to say that Ubuntu is immune to these things, although I would be wary of saying that :).

Relax and enjoy the freedom :)

Regards,  Kev :)

---

### Post by xenoalien on 2006-11-11
Man Linux rocks! I don't think I'll ever go back to windows :). Ubuntu runs just about everything windows can anyways. Thanks guys. I wont have to be so paranoid now lol.

---

### Post by taurus on 2006-11-11
Nope.  You can go to sleep at night and don't have to worry about your Ubuntu box anymore...  :mrgreen:

---

### Post by kvonb on 2006-11-11
...plus you don't have to waste 20 to 50% of your processor power on background virus scanning!

---

### Post by juantovarm on 2006-11-11
I have been using Ubuntu for the last month or so, it's total freedom, no more viruses, adware, spyware...No more paranoia :) I have some friends who run windows and they are all worried about *the new virus* and upgrading virus definitions, etc, etc... Now all my resources are going to apps i am running and not to keep my pc clean and safe

Juan

[IMG]http://ubuntucounter.org/img/ubuntu-user2.php?user=8952[/IMG]

---

### Post by Oki on 2006-11-11
I am using Firestater, but I have to start it every time I start the pc. Is it possible to get it to start automatic? Can I add it to the Session manager? 

And I use ClamTK antivirus(I have read that there is about 600 virus for Linux, and I am thinking; "one is enough"). And my question; why cant I scan the entire pc, only folders?

Thanks

---

### Post by kvonb on 2006-11-11
```
I am using Firestater, but I have to start it every time I start the pc. Is it possible to get it to start automatic? Can I add it to the Session manager?
```



The "Firestarter" that you see is just a "frontend", the firewall is running in the background, the interface is just there so that you can adjust stuff, it is also annoying and feeds the Windows paranoia because you can see all the hits.

```
And I use ClamTK antivirus(I have read that there is about 600 virus for Linux, and I am thinking; "one is enough"). And my question; why cant I scan the entire pc, only folders?
```

That's why Ubuntu is resilient to virii, nothing can get access to the important stuff!  Honestly, you really don't need a virus scanner, take the plunge and feel the freedom and tranquility :D

---

### Post by Oki on 2006-11-11
Thanks kvonb for the good answer!

---

### Post by aysiu on 2006-11-11
Read this:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by Uncle_John on 2006-11-12
hey 
maybe not the right place, but you've been talking about firewalls:p 

kvonb, said that there is a deafult firewall in ubuntu. how can I acces to that firewall? I need to open some ports, so my bittorrent will run faster?

I am new to Ubuntu so any help is very welcome=)

---

### Post by kvonb on 2006-11-12
Uncle_John:

Install Firestarter (I think you will have to install Automatix first though and do it through there).

:)

EDIT: no, just go to add/remove, it is in there.

---

### Post by Uncle_John on 2006-11-12
Hey 

I didn't find Firestarter in Add/Remove so I installed automatix2
It works fine but I can't find Firestarter in it.

What should I do?

---

### Post by kvonb on 2006-11-12
Sounds like you have to add universe and multiverse repos to Synaptic first then do an update (it is in the menus of synaptic).

When you have done that, run the add/remove thing and click on "show unsupported apps" and "show commercial apps".

It will show up then.

If you get stuck, let me know :)

Regards Kev :)

---

### Post by Uncle_John on 2006-11-12
I have it and it works:p 

But there's another problem. I am noob I know](*,) 
I can't find port settings in Firestarter. 

Well basicaly the problem is that my bittorrent is very slow, so I wanted to adjust settings in firewall, so the bittorent could run faster. But now I am wondering if I did the right thing? I know it's a mess:-?

---

### Post by kvonb on 2006-11-12
Hey uncle John,

In Firestarter, go to the OPTIONS page, make sure it is set to INBOUND TRAFFIC POLICY on the drop down box and (from memory), right click in the middle window (Allow Service) and add a new rule/policy.

For bittorrent, type in the port number (usually 6881), in the IP address field put the IP address of the computer you are running bittorrent on.

It's probably Chinese to you, but this is the link to the firestarter help page:

[http://www.fs-security.com/docs/policy-page.php](http://www.fs-security.com/docs/policy-page.php)

The thing with bittorrent is that it depends on people sharing the files and they don't usually give much outgoing speed to it, meaning that your downloads will be slow.  I've had one running for nearly 2 months (although it's 29gigs!).

Experience comes with use and trial and error, you'll get the hang of it eventually :).

I use Azureus which is a little harder to setup, I believe it is actually slower as it tends to eat a lot of CPU time.  However it is very tweakable and gives a lot of control.

If you are going to try it, don't use the one in the repos or from Automatix, download it straight from their site ([http://azureus.sourceforge.net/download.php)](http://azureus.sourceforge.net/download.php)), install jre (through Automatix)
 and you're good to go.

To be any use though you need to run it 24/7 which is a bit of a pain, I run a dedicated server so it's no big deal.

I'll finish rambling now, I hope some of this is helpful to you.

Regards,  Kev :)

---

