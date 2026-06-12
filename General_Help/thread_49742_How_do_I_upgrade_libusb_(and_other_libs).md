---
title: "How do I upgrade libusb (and other libs)"
date: 2005-07-17
forum: General Help
---

### Post by Vetto on 2005-07-17
There are many applications that are listed in the Ubuntu Guide that look simple to install ("apt-get clamav" for example) but have unmet dependancies.  (I looked in the Library version list for Hoary 5.04 and I have the correct versions that came with the install).  The updated lib files are not in the ubuntu repositories (any of them) and I am unclear how to correctly update them myself.

The libs that I find from Debian's site are fine, I install them with dpkg and all is good.  It is the ones that I have to compile myself that are not working.

For example:

I have the libusb-0.1-4 package, version 1:0.1.8-17ubuntu2  and I require libusb-0.1-4 (>= 1:0.1.10).   I can complile the source and make install it, but it is not recognized by either synaptec or by the app that required this library.

There were no errors in the "make" or the "make install", but synaptic still only sees the old verison.

Is there a place to go to explain why this happens and how to correctly upgrade a library that is not in the repository?

---

### Post by Vetto on 2005-07-21
No one knows how to do this?  I have read the FAQs, Howtos, and googles the heck out of this and either no one has answered this online or I missed it...please someone smarter than me in this point me in the right direction.

---

### Post by Vetto on 2005-07-24
<bump>

---

### Post by Vetto on 2005-07-25
nevermind...I found the library I needed in a deb package finally.  That correctly updated the database and now all is well.

I still would like to know how to update a library from a "self complied" source without screwing up the debian database for synaptic, apt-get, or aptitude.

any thoughts?  (feeling lonely here...)

---

### Post by ewart_hodgson on 2005-10-17
Hi Vetto,

I've just hit the same problem. How exactly did you solve it, please? (I am not a computer professional, so I am delighted rather than offended by very detailed answers!).

---

### Post by Vetto on 2005-10-17
I didnt "fix" the problem where a self installed library is not recognized by apt, I found a *deb of the library that I needed and used that instead.  Not sure how or why or if it is always true, but it is my experience (albiet limited) that when you install using a DEB and dpkg that the database gets updated.

Hope that helps.

---

