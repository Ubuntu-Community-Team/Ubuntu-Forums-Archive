---
title: "Installation Dependencies"
date: 2008-07-02
forum: General Help
---

### Post by solarghost on 2008-07-02
Hi

I couldn't find a appropriate place to post this so I'm posting it here.

I have recently installed Ubuntu (Hardy), everything when smoothly. Then I had to install the Vodafone software and that was a bit of a nightmare (not difficult just a lot of work) to get my internet connection up and running. My biggest problem was installing all the packages and their dependencies. I used the excellent [http://packages.ubuntu.com/]("http://packages.ubuntu.com/") which is great however what would have really helped me in the list of "Other Packages Related to" that you get when you search for a packages is an indicator of whether or not the dependency is provided in a standard install of that particular release (Hardy, Gusty, Feisty etc). Otherwise well done to the Ubuntu team for an easy to install, free Operating system and a Excellent Package search website.

---

### Post by dcstar on 2008-07-02
> **solarghost said:**
> Hi

I couldn't find a appropriate place to post this so I'm posting it here.

I have recently installed Ubuntu (Hardy), everything when smoothly. Then I had to install the Vodafone software and that was a bit of a nightmare (not difficult just a lot of work) to get my internet connection up and running. My biggest problem was installing all the packages and their dependencies. I used the excellent [http://packages.ubuntu.com/]("http://packages.ubuntu.com/") which is great however what would have really helped me in the list of "Other Packages Related to" that you get when you search for a packages is an indicator of whether or not the dependency is provided in a standard install of that particular release (Hardy, Gusty, Feisty etc). Otherwise well done to the Ubuntu team for an easy to install, free Operating system and a Excellent Package search website.

All packages installed by the inbuilt utilities - like Synaptic - will install dependencies automatically.

If you do not use the provided tools then you are on your own.

---

### Post by sdennie on 2008-07-02
Normally if you install a package with "dpkg -i", and it fails because of dependency problems you can then type:

```

sudo apt-get install -f

```

And it will download the missing dependencies.  I've done this while installing VirtualBox from their website many times.

---

### Post by solarghost on 2008-07-02
I think you have misunderstood me. 

"All packages installed by the inbuilt utilities - like Synaptic - will install dependencies automatically.

If you do not use the provided tools then you are on your own."

The vodafone driver does not come standard with a "stock" Ubuntu install (rightly so) and I needed that to get an internet connection. So that I could use inbuilt utilities to download packages because I could not download anything because I did not have internet.

That however is besides the point. The point of my thread is that I think that the package website ([http://packages.ubuntu.com/]("http://packages.ubuntu.com/")) should indicate if a package comes installed as part of a "stock" install of a paticular Ubuntu version.

Hope this is clearer.

---

