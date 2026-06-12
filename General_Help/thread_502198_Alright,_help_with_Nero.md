---
title: "Alright, help with Nero"
date: 2007-07-16
forum: General Help
---

### Post by Popolop on 2007-07-16
I'm having some problems installing Nero. I tried a couple of different things (sudo apt-get install nero, sudo apt-get install NERO, etc.), but I just can't get it to work. Any tips?

---

### Post by Popolop on 2007-07-16
Anyone?

---

### Post by bodhi.zazen on 2007-07-16
Best to go with a linux native application.

I like both K3b and Brasero (IMO k3b).

Neuro, Linux edition, is, IMO buggy at best.

---

### Post by davidjmayo on 2007-07-16
beaten by bodhi.zazen again!!
I was going to suggest you use k3b

---

### Post by Popolop on 2007-07-16
Alright, but one last thing. How do I convert .nrg to a .iso?

---

### Post by noynac on 2007-07-16
> **Popolop said:**
> I'm having some problems installing Nero. I tried a couple of different things (sudo apt-get install nero, sudo apt-get install NERO, etc.), but I just can't get it to work. Any tips?

I assume you are talking about Nero Linux. This software comes as a downloadable DEB file. I'm relatively new to Linux, but I think apt-get only works with programs in specified repositories, which I don't believe includes Nero Linux.

---

### Post by notwen on 2007-07-16
I personally use GnomeBaker and K3B for all fo my burning needs, but in case you're still after Nero for Linux here is a [link to their site]("http://www.nero.com/eng/NeroLINUX.html").  Scroll down and you should see both 32bit and 64bit deb packages for download.  Good luck. =]

---

### Post by Popolop on 2007-07-16
Well, nothing seems to be working for me. I tried burning the torrents on this page:
[http://www.mininova.org/tor/683777](http://www.mininova.org/tor/683777)

but it's not doing anything.

---

### Post by Popolop on 2007-07-16
Please help me :(

---

### Post by bodhi.zazen on 2007-07-16
> **Popolop said:**
> Alright, but one last thing. How do I convert .nrg to a .iso?

LOL

With nrg2iso. Install ngr2iso with Add/Remove programs or synaptic or as below :

```
sudo apt-get install nrg2iso
nrg2iso <file.nrg> <file.iso>
```

Where file.nrg is the file to convert and file.iso is the output file

* Note you will need to user the full path to the file or cd into the directory where the .nrg is stored.


================

Trouble shooting the torrent is sometimes more problematic. Sometimes not all those on miniova work :(

Try downloading a standard torrent first ...

Like say this one : [http://us.releases.ubuntu.com/releases/feisty/ubuntu-7.04-desktop-i386.iso.torrent](http://us.releases.ubuntu.com/releases/feisty/ubuntu-7.04-desktop-i386.iso.torrent)

---

### Post by davidjmayo on 2007-07-16
A search on synaptic (system==>administration==>synaptic package manager) for nero shows this package

nrg2iso (decription from synaptic: Extracts ISO9660 data from Nero ".nrg" files
This extracts the ISO9660 CD image data from Nero  ".nrg" files.)

Don't know if it will help or if it does what it says. Do your research before you try it.

EDIT: beaten again!!

---

### Post by michaelzap on 2007-07-16
Not sure what more help you need. Just download the .deb file from the link that notwen gave you above and double-click on it, or install nrg2iso and use it to convert your Nero images to iso images so you can burn them from any other application. If you're having a specific problem with one of those things, you should post exactly what's happening so that people have enough information to be helpful.

---

### Post by peebly on 2007-07-16
Strange, when I got Nero Linux 3, I just downloaded the deb file to the desktop and double clicked on it and then clicked install.

I did not have to type anything in to the terminal and it installed no problem.

To those who have recommended k3b or brasero, Sorry but these programs are nowhere near as good as Nero in my opinion.

Are you sure you don't like it simply because its not free.

---

### Post by stchman on 2007-07-16
> **Popolop said:**
> I'm having some problems installing Nero. I tried a couple of different things (sudo apt-get install nero, sudo apt-get install NERO, etc.), but I just can't get it to work. Any tips?

Nero is not part of the repositories to my knowledge.  I personally use K3B and it works very well.  It has everything I need.

---

### Post by michaelzap on 2007-07-16
K3B not as good as Nero?!? Are you kidding? K3B is really, really impressive...

Nero Linux is a very stripped-down version of Nero Burning ROM only. It doesn't have all the other crapola that the Nero Ultimate package for Windows has, so it's really not even in K3B's league in my opinion. It's an OK burning application, but other than handling .nrg image files I don't think there's anything that Nero Linux can do that K3B can't do better faster snazzier.

I used to use some of those other Nero applications that came with the Ultimate bundle on Windows (and they were mostly high-quality software), but in general I prefer not to have to uncheck 50 things to be installed when all I want is a burner/ripper.

---

### Post by notwen on 2007-07-16
> **peebly said:**
> Are you sure you don't like it simply because its not free.

Perhaps we've been w/o Nero for Linux for a couple of years and have grown fond of K3B or Gnome Baker.  Nero for Linux is still very new FYI.  We like our burning apps for the simple fact they do what we want, being free is just an added bonus.  This would be my opinion. =]  To each his/her own.

---

### Post by bodhi.zazen on 2007-07-16
> **peebly said:**
> Are you sure you don't like it simply because its not free.

Yea, I am sure :twisted:

K3b is clean, reliable, fast ...

But, hey if you like Neuro, hats off to you ...

That is the best thing about Linux, options ...

---

### Post by dxdemetriou on 2007-07-17
Well,

About K3b: It supports user permissions, links. It has very unstable speed, and the solution with disable KDED don't always work. It don't support fully UDF so no files greater than 4GB

About Nero: It doesn't support user permissions, I don't know for links. The speed is more stable, if I run the k3b first it inflected the speed of Nero too, if I am correct with the KDED thing. It fully supports UDF so bigger files can be written. When I tried to burn the Sabayon Linux DVD 3.3 it burnt it as a CD, but the K3b with the correct way.

About the Brasero, GnomeBaker, Graveman, etc: Brasero have maximum speed 6X for me, and both don't have a good verification. The Brasero I think it has, but only for Data disks, and creates a file with md5sum on disk

ps. If somebody knows how can I solve this issues let me know, so to can left from Nero.

---

### Post by stchman on 2007-07-17
I have never tried to burn a file larger than 4GB as the DVDs I use only hold 4.3GB.

Since we are on the subject of K3B I have a question.

I know Nero supports burning to multiple burners.  Can K3B do this?

Thanks

---

### Post by Alchera on 2007-07-19
> **Popolop said:**
> I'm having some problems installing Nero. I tried a couple of different things (sudo apt-get install nero, sudo apt-get install NERO, etc.), but I just can't get it to work. Any tips?
There's no way that would work as Nero is proprietary software and, as a result, will never find its way into any repositories.

---

