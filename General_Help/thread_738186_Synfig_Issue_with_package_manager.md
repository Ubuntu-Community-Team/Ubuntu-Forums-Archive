---
title: "Synfig Issue with package manager"
date: 2008-03-28
forum: General Help
---

### Post by koresho on 2008-03-28
Hey everyone, I am trying to get Synfig installed on Hardy.
I first downloaded the source from their site and I tried to get it compiled but I wasn't doing something right, so I ended up trying to download it from the Add/Remove link on the main menu. 
I download and install it, and now when I try to launch it I get this message:
> This copy of Synfig Studio was compiled against a
different version of libsynfig than what is currently
installed. Synfig Studio will now abort. Try downloading
the latest version from the Synfig website at
[http://www.synfig.com/](http://www.synfig.com/) 

So far I have: 
[list][*]uninstalled and reinstalled Synfig using the Add/Remove and Synaptic
[*]deleted everything that had to do with Synfig from my /usr/bin
[*]used ```
sudo apt-get install libsynfig-dev
``` then downloaded synfig again and it still didn't work[/list]
I can't think of anything else, any help would be appreciated. Thanks!

---

### Post by Rocket2DMn on 2008-03-28
You can try forcing the correct version of lybsynfig from Synaptic by selecting the package then going to Package->Force Version.
You will have to figure out which version you need to force.

---

