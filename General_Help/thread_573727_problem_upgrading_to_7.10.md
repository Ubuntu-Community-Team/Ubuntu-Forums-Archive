---
title: "problem upgrading to 7.10"
date: 2007-10-11
forum: General Help
---

### Post by perfect_circle on 2007-10-11
i get  an error when i try updating, it tells me....

Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_CA.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_CA.bz2) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz) Could not resolve 'wine.lowvoice.nl'


what should i do? any ideas.

---

### Post by dcstar on 2007-10-11
> **perfect_circle said:**
> i get  an error when i try updating, it tells me....

Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_CA.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_CA.bz2) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz) Could not resolve 'wine.lowvoice.nl'


what should i do? any ideas.
They are Feisty repositories, firstly you are no longer using that distribution (you should remove them), and secondly those errors are DNS errors - the site no longer exists (or resolves in DNS).

---

### Post by perfect_circle on 2007-10-11
how do i do that? remove them?

---

### Post by dcstar on 2007-10-12
> **perfect_circle said:**
> how do i do that? remove them?

Go into Synaptic and remove them from your list of Repositories.

---

### Post by nibbslang on 2007-10-18
I'm having the same problem.......

I have removed wine using the synaptic package manager and still the upgrade comes up with the same message as above.

Any ideas?

Anyone?

---

### Post by Archmage on 2007-10-18
> **nibbslang said:**
> I'm having the same problem.......

I have removed wine using the synaptic package manager and still the upgrade comes up with the same message as above.

Any ideas?

Anyone?

Ehm?

> Go into Synaptic and remove them from your list of Repositories.

---

### Post by steve.dhondt on 2007-10-18
> **nibbslang said:**
> I'm having the same problem.......

I have removed wine using the synaptic package manager and still the upgrade comes up with the same message as above.

Any ideas?

Anyone?
It's not the package that needs to be removed. 
Open synaptis package manager and click on "settings" on the top bar, then pick "repositories".
A new window will pop-up. In that window click the second tab: "third party software"
From that list select the one with "wine.lowvoice" in it's name and then click on remove. Close package manager and open update manager again, it should work like a charm.

---

### Post by cloudstrife87 on 2007-10-20
I've been facing the same respiratory problem mention above, and i've followed your method by disabling third parties respiratory in synaptic package manage, whoa....it finally upgrades... Thanks for your advice ;-)....

---

