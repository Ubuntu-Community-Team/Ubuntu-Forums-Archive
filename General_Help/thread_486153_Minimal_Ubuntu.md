---
title: "Minimal Ubuntu"
date: 2007-06-27
forum: General Help
---

### Post by ®©™ on 2007-06-27
Hello,

I just wondered if there is any "minimal" version of Ubuntu. (or another linux-distribution for that matter.)

I'm thinking about installing Linux for a couple of friends of mine, but as most people they don't really need a lot of applications. Basically, they'll need Skype, Firefox, Rhythmbox, Totem and Jabber. (some may also need F-Spot and OpenOffice.)

Of course, it is easy to just install Ubuntu and get rid of all the other programs. but when you get down to it, navigating through these few programs could be done so much easier and elegantly than the "standard" Ubuntu way. For long, I would have just told them to get a Mac, but OS X is starting to get really bloated.

So, have anyone else gone ahead and thought about this and made a "simple" distribution for "simple" people (:)), or am I the first one thinking about this? (the only half-decent distribution I've found is not free - it's the new midinux that's tied to certain hardware.)

Thanks in advance for all answers. :)

---

### Post by bodhi.zazen on 2007-06-27
There are several options.

I came across this one the other day :

[http://bea.cabarel.com/[BeaFanatIX (BFX)]()

It is a little dated, but it is awesome little ubuntu ;)

You can also look at 

You can also check out AUSTRUMI, Puppy, DSL, Zenwalk, Wolvix, Mint, PCLinuxOS

---

### Post by ®©™ on 2007-06-28
Thanks a lot for your reply. That was very helpful. From the ones you mentioned, Zenwalk seems to be the most appropriate. I like the addition of a dock (though I personally think it could have replaced the taskbar completely), and the whole OS seems modern and pretty.

I see it's based on the same desktop environment as Xubuntu, still they seem kind of different..?

Again, thanks. :)

---

### Post by mmtowns on 2007-11-21
> **®©™ said:**
> Hello,

I just wondered if there is any "minimal" version of Ubuntu. (or another linux-distribution for that matter.)

I'm thinking about installing Linux for a couple of friends of mine, but as most people they don't really need a lot of applications. Basically, they'll need Skype, Firefox, Rhythmbox, Totem and Jabber. (some may also need F-Spot and OpenOffice.)

Of course, it is easy to just install Ubuntu and get rid of all the other programs. but when you get down to it, navigating through these few programs could be done so much easier and elegantly than the "standard" Ubuntu way. For long, I would have just told them to get a Mac, but OS X is starting to get really bloated.

So, have anyone else gone ahead and thought about this and made a "simple" distribution for "simple" people (:)), or am I the first one thinking about this? (the only half-decent distribution I've found is not free - it's the new midinux that's tied to certain hardware.)

Thanks in advance for all answers. :)



Have you tried installing via the alternate cd?

1) Install a command line system via the Gutsy alternative CD.
2) To install a lighter window manager (I like Xfce)...
```
sudo aptitude install xorg xfce4
```
3) I like the thunar file manager, synaptic and firefox
```
 sudo aptitude install thunar synaptic firefox 
```

Install any other applications you'd like as well.  You might be interested in installing a graphical login manager so you don't have to use the command line to login and start X.  Try...
```
sudo aptitude install gdm
```

Good luck.

---

### Post by aysiu on 2007-11-21
mmtowns is on the right track, even though Xfce is a desktop environment and not a  window manager.

More details here:
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by mmtowns on 2007-11-21
aysiu,
Thanks for the terminology correction.  The link you provided is one that helped me as well.

---

### Post by Wiebelhaus on 2007-11-21
This is a [spectacular Doc]("https://help.ubuntu.com/community/Installation/LowMemorySystems") about precisely hwat you want to do.


Also try [Fluxbuntu ]("http://fluxbuntu.org/")first.

---

