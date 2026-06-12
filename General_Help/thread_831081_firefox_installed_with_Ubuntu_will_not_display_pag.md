---
title: "firefox installed with Ubuntu will not display page properly"
date: 2008-06-16
forum: General Help
---

### Post by faz67 on 2008-06-16
Hello All
I recently installed ubuntu 8.4 and love the system. but the FireFox that was installed with it will not display my page properly.  All other browsers display correctly but this one will not display my sidebar text widgets at[ http://meandering-pen.com]("http://meandering-pen.com"). Does anyone out there using the Ubuntu default installation browser, see my text widgets?

Left  box titled Getaway

Right boxes titled Ads by google  and  Pet care costs.


All should look similar to bottom right titled Pet Care

PS this is a WordPress Blog
 
Gary:confused:

---

### Post by Het Irv on 2008-06-16
Do you have ad-block turned on? Nothing displayed in the aformentioned sections until I turned it off.

---

### Post by imneo on 2008-06-16
ubuntu 8.04 comes with firefox-3, this is not a stable version yet
you shuld remove it and install firefox-2

here is a full guide for how to do this correctly:

[http://scripts-net.com/viewtopic.php?f=22&t=82#p95](http://scripts-net.com/viewtopic.php?f=22&t=82#p95)

---

### Post by Het Irv on 2008-06-16
> **imneo said:**
> ubuntu 8.04 comes with firefox-3, this is not a stable version yet
you shuld remove it and install firefox-2

here is a full guide for how to do this correctly:

[http://scripts-net.com/viewtopic.php?f=22&t=82#p95](http://scripts-net.com/viewtopic.php?f=22&t=82#p95)

Why? I got it to display perfectly in Firefox 3, within the week Ubuntu will release the update that will bring Firefox up to the Release, which comes out tomorrow.  There is nothing wrong with FF3, I am willing to bet that the OP has Ad-block installed and it is doing its job blocking the Ads in those sections.

---

### Post by DJ_Peng on 2008-06-16
> **imneo said:**
> ubuntu 8.04 comes with firefox-3, this is not a stable version yet
you shuld remove it and install firefox-2
Actually Firefox 3 (please note, it's not FireFox) is out tomorrow, and the late beta that was included in Hardy wasn't that borked. I know, I'd been testing it in nightly builds since shortly after beta 4 came out. Suggesting someone roll back to Firefox 2 for an issue like this doesn't help him at all.

The text widgets are adverts that are hidden by plugins like AdBlock Plus. Try disabling any ad/Flash blocking extensions you may have installed and see if that does any good. Just looking at the code for those layers told me I wasn't seeing them because AdBlock Plus was doing it's job. Anyone using an advert blocking technology will also see empty sections as well.

---

### Post by faz67 on 2008-06-17
> **Het Irv said:**
> Do you have ad-block turned on? Nothing displayed in the aformentioned sections until I turned it off.

Thank you **Het Irv**

_This did indeed take care of the problem_. Or as Homer would say Doah.
What an incredibly active forum, I have never had so may responses to a post.:)
All within 24 hours.  The more I play with this distro the more I Like It!

_**BIG THANX TO ALL!**_

---

### Post by faz67 on 2008-06-17
> **imneo said:**
> ubuntu 8.04 comes with firefox-3, this is not a stable version yet
you shuld remove it and install firefox-2

here is a full guide for how to do this correctly:

[http://scripts-net.com/viewtopic.php?f=22&t=82#p95](http://scripts-net.com/viewtopic.php?f=22&t=82#p95)

Thanx for the reply but turning off ad block fixed the problem.
Don't forget to download Firefox tomorrow at the official release.

Thanx 
Gary

---

### Post by faz67 on 2008-06-17
> **DJ_Peng said:**
> Actually Firefox 3 (please note, it's not FireFox) is out tomorrow, and the late beta that was included in Hardy wasn't that borked. I know, I'd been testing it in nightly builds since shortly after beta 4 came out. Suggesting someone roll back to Firefox 2 for an issue like this doesn't help him at all.

The text widgets are adverts that are hidden by plugins like AdBlock Plus. Try disabling any ad/Flash blocking extensions you may have installed and see if that does any good. Just looking at the code for those layers told me I wasn't seeing them because AdBlock Plus was doing it's job. Anyone using an advert blocking technology will also see empty sections as well.

Thanks for the reply!
AdBlock was the problem!
All is right with the world now!
Gary

---

### Post by DJ_Peng on 2008-06-19
Glad I could help :)

---

