---
title: "Lost some apps and app functions"
date: 2013-04-19
forum: General Help
---

### Post by ineuw on 2013-04-19
Installed the associated PPA and Ironkey - by carefully selecting the Gnome installation. Accepted that the library was 380MB, and ended up with KDE and Akonadi which I really didn't want. So, after reading numerous posts with the same issue, I carefully uninstalled Akonadi and it's associate files using Synaptic.

This also meant the loss of Ironkey.
The loss of the date and time app in Accessories (not the plugin).
The loss of install/remove functionality of the Ubuntu Software Centre.
The loss of GUI menu access to Synaptic which only works through terminal activation.

Can anyone please help on how can I repair the above listed damage?

---

### Post by vasa1 on 2013-04-19
Your post is missing a lot of information. The start is a bit abrupt. Did you leave out a paragraph or more?

---

### Post by ineuw on 2013-04-19
All the info is here although I agree it's a bit abrupt. The initial info was to indicate that my installation was correct and I followed the correct procedure. It was surprising that a small app like Ironkey required a 380MB library so I mentioned it hoping to get some clarification, The problem was Akonadi (which is a very large app and very resource intensive),  the removal of which caused the loss of the other apps' functionality.

I was under the initial impression that if one installs the standard default Xubuntu and selects Gnome apps, KDE would not be needed. Ever since my original post, I've ben reading up on all the related topics and found that I assumed wrong. Now, all I want is to resore Synaptic and the Ubuntu Software Center to their original functionality and then find a way to install Ironkey without Akonadi. 

I hope this is clearer.

---

### Post by Elfy on 2013-04-19
From the information you've provided it's obvious you've had to install a bunch of kde dependencies for it, 380Mb sounds about right for adding an app with kde deps to xubuntu or ubuntu - removing them has caused it to break. You would have had a list of the packages being installed at the time.

Giving people the bare minimum information that you have means that anyone who might want to help has to then spend time searching for information you could have provided in the first place, why should they? 

Given what you have said - I'd try to remove the ppa and start again - ppa-purge might work for you.

---

### Post by ineuw on 2013-04-23
All above replies are appreciated. I broke too many packages and all repair options failed, so I installed from the beginning. Thanks again.

---

