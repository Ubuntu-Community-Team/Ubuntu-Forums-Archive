---
title: "Choosing a distro"
date: 2008-07-03
forum: General Help
---

### Post by rogier.de.groot on 2008-07-03
Hi all,

I currently use Ubuntu on both my servers, my two desktop and my laptop, but some small things annoy me, and I was wondering if maybe I should change to (Ubuntu based) Mint or perhaps something else entirely.

Here's what I need my distro to do:
1) Regular stuff - I want YouTube to work, AVI's/DVD's to play, etc. I don't care if the codec is open source or not, get the regular things working without doing weird things on the command line.
2) For my laptop I need wireless to work - it's a Broadcom card, I currently use ndiswrapper because the regular driver (in hardy) won't work.
3) I develop using Java and NetBeans, I'd therefor like some up to date Java packages *that are kept up to date* and I mean real, Sun Java not that disfunctional GCJ or IcedTea stuff. That would include NetBeans 6.1 (instead of 6.0), GlassFish V2 UR2 (instead of UR1) and Tomcat 6.x (instead of 5.5).
4) I also develop in C# and therefor want up to date Mono/MonoDevelop packages. And a mod_mono that actually works (for ASP.NET 2.0) to go with apache on the server.
5) On the server side I'd also like to have subversion 1.5 with apache module to match.
6) On some machines, getting 3D accelerated NVidia drivers without the hassle.

And all of that using just apt-get (unless yum has gotten a lot better since fedora core 4) and no bloody 'build from source' nonsense.

Is there a distro for me or is Ubuntu with some adjustments as good as it gets? (and yes, I realize that getting all of this set up is even crappier on Windows, apt spoiled me and I like getting updates for everything on my whole system with one command).

---

### Post by phidia on 2008-07-03
One can search for the perfect distro forever.
I don't think there's an easy answer to your question-not an answer that anyone else can give you. To me it's like a friend/partner/spouse you find one you can live with and each one has their own unique imperfections, but you're asking the question so you're not happy-go shopping.
[Sabayon]("http://www.sabayonlinux.org/") just released it's latest version and it has many of the things you are wanting (video card automatically found and setup + other feature requests) but the package management style may be found lacking by some.:lolflag:

---

### Post by sujoy on 2008-07-03
i believe you should be happy with Debian Testing (lenny) with a carefull mix from the sid repos.

---

