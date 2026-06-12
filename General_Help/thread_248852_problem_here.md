---
title: "problem here"
date: 2006-09-01
forum: General Help
---

### Post by amirji on 2006-09-01
hi all

when im installing something using terminal i get a error message, was working before. started happening just now! i have a screen shot, its the bottom line btw. im a newbi so go easy on me!

---

### Post by ayoli on 2006-09-01
that's because you cant run apt-get while synaptic package manager is open behind.
close synaptics, then run again apt-get.

---

### Post by amirji on 2006-09-01
how do i close it?

---

### Post by ayoli on 2006-09-01
the window behind your terminal (synaptic) ? by clikin on the close button in title bar or choose quit in the menu.

---

### Post by kerry_s on 2006-09-01
Did you turn on all your repo's?  Why not just use synaptic so you can see the packages?

sudo gedit /etc/apt/sources.list  <uncomment(#) all the repos, maybe even add multiverse.

then apt-get update

or

synaptic > repositories click on the box next to the repo to turn it on(should have a check). You can click on the repo select edit click the multiverse box to add it to the list.

Edit: I didn't even notice he had synaptic open :(

---

### Post by amirji on 2006-09-01
sheesh! im sorry, u guys must thnk im stooopid! if its any consolation its quite late ova here in uk, i mus be tired! thnx a bunch evrythng is fine.

cheers

---

