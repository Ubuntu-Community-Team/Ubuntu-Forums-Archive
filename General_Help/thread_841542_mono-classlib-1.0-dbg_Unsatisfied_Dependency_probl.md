---
title: "mono-classlib-1.0-dbg Unsatisfied Dependency problem."
date: 2008-06-26
forum: General Help
---

### Post by tabithaboof on 2008-06-26
I am trying to install a game manager piece of software for Hardy, Specifically "xbgmsharp" which can be found here

[http://xbgm.sourceforge.net/files.php#Debian](http://xbgm.sourceforge.net/files.php#Debian)

When trying to install the .deb on the page (which is admittedly fairly old) I get a message saying 

"Error: Dependency is not satisfiable: mono-classlib-1.0"

I have looked in the repos for "mono-classlib-1.0 but havent had any luck finding it. Any idea where to go from here?

---

### Post by mdshaver on 2009-02-19
I am also having this same problem but with Intrepid. I need to install a Master Hearing Aid program designed for auditory research but I could not find the mono-classlib-1.0 dependency in Synaptic. When I Google it, it seems that I see hits referring to Dapper. Is there any way around this because I would really like to be able to use this program on Linux.

---

### Post by directhex on 2009-02-19
The mono-classlib packages haven't existed since Edgy.

Try using "equivs" to satisfy the dependency - or force it with --force-all

---

### Post by mdshaver on 2009-02-19
Thanks for the quick response but I'm a noob so I may not a little more hand holding on this. I looked for equivalents in synaptic but nothing seemed to work. Then I googled mono-classlib-1.0. I added a Debian apt to my Software Sources and installed Mono 1.0 Devel along with associated dependencies. This seemed to work but when I attempted to install the .deb package, it said that a variety of things (~45) would need to be uninstalled so that I could install my .deb file. The items in question included F-Spot, Banshee, gBrainy, and a variety of dependencies. I did not do this as I was unsure of the consequences on the system as a whole.

---

### Post by directhex on 2009-02-20
> **mdshaver said:**
> Thanks for the quick response but I'm a noob so I may not a little more hand holding on this. I looked for equivalents in synaptic but nothing seemed to work. Then I googled mono-classlib-1.0. I added a Debian apt to my Software Sources and installed Mono 1.0 Devel along with associated dependencies. This seemed to work but when I attempted to install the .deb package, it said that a variety of things (~45) would need to be uninstalled so that I could install my .deb file. The items in question included F-Spot, Banshee, gBrainy, and a variety of dependencies. I did not do this as I was unsure of the consequences on the system as a whole.

It told you it would need to remove all that stuff as it needed to massively downgrade your Mono in order to satisfy the dependency - depending on "mono-classlib" hasn't been right for a couple of years.

And by "equivs" i mean "install the equivs package" - or, as i said, install the .deb on the command line using --force-all

---

