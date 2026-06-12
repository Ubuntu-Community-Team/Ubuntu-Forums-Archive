---
title: "Mono 1.1.6 on Hoary?"
date: 2005-05-02
forum: General Help
---

### Post by sebgate20 on 2005-05-02
I've heard that the Mono 1.1.6 Packages are in Breezy Badger but I feel that I don't want to upgrade my system to something that must be very unstable (well hey, it's only been development for a month or so!).

I'm using Mono 1.1.4 from manno.name but I'd really like 1.1.6. Any idea where I can get them from? How? Could I download them from the Breezy Universe Respoitory manualling?

Thanks

Seb

---

### Post by jayded on 2005-05-02
Why do you need 1.1.6, is there something specific you require ?

[QUOTE=sebgate20]I've heard that the Mono 1.1.6 Packages are in Breezy Badger but I feel that I don't want to upgrade my system to something that must be very unstable (well hey, it's only been development for a month or so!).

I'm using Mono 1.1.4 from manno.name but I'd really like 1.1.6. Any idea where I can get them from? How? Could I download them from the Breezy Universe Respoitory manualling?

Thanks

Seb[/QUOTE]

---

### Post by shakin on 2005-05-02
You could add the Breezy repository and mark Mono for installation, then see if it wants to install any dependencies. If not, I think it would be pretty safe to install since a broken package would only break Mono. I plan on doing this at home sometime this week.

What you don't want to do is update critical libraries or apps from Breezy.

Don't forget to remove the Breezy repository once Mono is installed.

---

### Post by sebgate20 on 2005-05-02
[QUOTE=shakin]You could add the Breezy repository and mark Mono for installation, then see if it wants to install any dependencies. If not, I think it would be pretty safe to install since a broken package would only break Mono. I plan on doing this at home sometime this week.[/QUOTE]

Never mind. I found it in the Backports Repository. I added this line to my sources.list:

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports-staging main universe multiverse restricted

and Synaptic found it! What does the backports-staging bit mean? I know what backports are but the staging puzzels me.

Seb

---

### Post by Bob D. on 2005-05-02
Backports packages go through a period where they are available for download and testing to see if any issues surface. Once past the staging test period, the packages will be promoted.

From the Backports homepage:

[i]But, **BIG FAT WARNING**: The staging area should be treated like Debian experimental -- it's NOT tested, NOT guaranteed in any way, shape or form to be stable!

[/i]Bob

---

### Post by sebgate20 on 2005-05-03
I like to live on the edge......But the Backports stuff works fine for me!

Seb

---

