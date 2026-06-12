---
title: "Whats the difference between Ubuntu's APT and Debian's?"
date: 2008-03-23
forum: General Help
---

### Post by Fixman on 2008-03-23
Does Debian have more packages?

---

### Post by talsemgeest on 2008-03-23
> **Fixman said:**
> Does Debian have more packages?
Ubuntu can have an infinite number of packages. You just need to add more sources

---

### Post by kerry_s on 2008-03-24
hmm, not sure who has more. ubuntu has meta packages for the different desktops and restricted items.

ubuntu's starts off as a snap shot of sid, then redone to the ubuntu way.
debian still has separate kernels for the different cpu's, ubuntu use's a generic kernel to cover all cpu's.

debian is faster
debian is more stable
debian supports older hardware better
ubuntu is suppose to be easier
ubuntu may support more newer hardware better

it's all just a matter of what you prefer.

other than that apt is done the same way on both, same commands, same programs.

---

### Post by accatagon on 2008-03-24
The entire APT system was designed by the Debian people. Ubuntu pretty much uses the exact same system, just with different packages, although, as kerry_s said, each version is based off of a snapshot of the entire Debian repository, and then stuff is changed to create Ubuntu.

Debian is one of those Linux distributions that was the progenitor for a lot of other distros. You'll hear a lot about "Debian-based" distributions, and Ubuntu is one of them. The main thing that actually ties these distros together is the use of APT and .deb package files. Essentially the technical aspects of how packages are handled are the same for both Debian and Ubuntu. Just keep in mind that a lot of what went into Ubuntu (and Knoppix and some others) came from the Debian people and that they deserve some thanks.

As far as differences in the packages themselves, Debian has far fewer features automatically built in. There is even the option of not installing a graphical user interface. It is far more customizable than Ubuntu, but at the expense of ease of use. Its release schedule is also a lot longer (3 years or so), yielding much more stable releases instead of much more up-to-date ones. They also have rolling releases in what is called the "testing" and "unstable" repositories, where you can get the newest packages, but without any guarantee that they necessarily work properly. If you wished to use a Debian desktop, I would STRONGLY advise that you use the testing version. otherwise, for servers, the stability of the official releases is nice.

---

