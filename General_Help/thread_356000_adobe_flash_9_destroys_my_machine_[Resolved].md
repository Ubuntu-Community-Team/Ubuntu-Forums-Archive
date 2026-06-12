---
title: "adobe flash 9 destroys my machine [Resolved]"
date: 2007-02-07
forum: General Help
---

### Post by tortus on 2007-02-07
I'm surprised to find no real posts on this in the forum, makes me fear I'm the only one.

Ever since I upgraded to Adobe Flash 9, my machine has been horrible to use.

I am using firefox 2.0.0.1 with the Flash 9.0.31.0.1ubuntu1~edgy plugin, and most flash applets seem to cause an infinite loop or something in the flash player. My CPU usage shoots to 100%, and I can just barely do anything. It takes a good 5-10 minutes to get a terminal open and type "sudo reboot". 

Recently my system update updated my flash to a newer version (not sure exactly what the older version was, my current version is the one stated above), and it seems to have helped. The flash player still eats a ton of the CPU and my machine still becomes very unresponsive. But now if I manage to quit Firefox I seem to recover ok, where as before I had no hope at all and had to reboot.

I am using edgy, an HP laptop with an intel single core processor. 512MB of RAM. Firefox 2.0.0.1 and Flash 9.0.31.0.1ubuntu1~edgy downloaded and installed using synaptic.


Seeing as I am currently developing a webapp that uses a flash applet, this has become a really serious problem for me. Definitely appreciate any help.

---

### Post by tortus on 2007-02-07
As an example, this flash applet causes the problem (many, many others do too)

[http://ziya.liquidrail.com/](http://ziya.liquidrail.com/)

I just reinstalled flash via synpatic and so far it seems ok, maybe that's all I needed to do.

---

### Post by Polygon on 2007-02-07
or you could just remove it via synaptic and just download the tar.gz from adobe's website. its just one file that goes in your .mozilla folder...

---

### Post by aysiu on 2007-02-07
> **Polygon said:**
> or you could just remove it via synaptic and just download the tar.gz from adobe's website. its just one file that goes in your .mozilla folder...
I agree--that's worth a shot. Full instructions here:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by tortus on 2007-02-08
I uninstalled from synaptic and got the tarball from Adobe's site. So far so good. Thanks for the help.

---

