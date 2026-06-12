---
title: "Aptitude list manually installed packages."
date: 2006-11-13
forum: General Help
---

### Post by ./mario on 2006-11-13
Does anyone knows how can I list manually installed packages with aptitude?

Or something like the 'world' file in Gentoo.


Thanks.

./mario

---

### Post by koenn on 2006-11-14
install equivs

-> [http://www.debian.org/doc/manuals/apt-howto/ch-helpers.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-helpers.en.html)

---

### Post by ./mario on 2006-11-14
What I mean is, when you install package A have deps package B and C, more later you install package D, E, F, that has deps G, H, etc.
And what I want is a way to see in a list, command line or whatever, what packages I INSTALLED,the packages A, D, E, and F. This packages where installed manually, by me.

Thanks.

./mario

---

### Post by emix on 2006-11-14
This feature should be implemented in Synaptic (in my opinion). It would be very useful.

---

### Post by ./mario on 2006-11-15
Should be a feature implemented in any package manager (or frontend), so the user have tracking of the packages he (or she) installed.

./mario

---

### Post by andmalc on 2007-06-03
This thread is old, but anyway, here's the command to list manually installed packages (excluding Essentials).

aptitude search '~i!~E' | grep -v "i A" | cut -d " " -f 4

See the following for more:

[http://www.debian-administration.org/articles/462](http://www.debian-administration.org/articles/462)

---

