---
title: "About imagezoom - firefox addon"
date: 2008-04-09
forum: General Help
---

### Post by satimis on 2008-04-09
Hi folks,


Ubuntu 7.04 server amd64
Firefox 2.0.0.13


After removing ~/.mozilla I have to reinstall all addon.


reinstalled imagezoom on;
[https://addons.mozilla.org/en-US/firefox/addon/139](https://addons.mozilla.org/en-US/firefox/addon/139)


Restarted Firefox
View --> can't find "zoom image" here.


Tools - -> Add-on
found it already installed.


Restart X/Reboot still can't take effect.  Please advise.  TIA


B.R.
satimis

---

### Post by ryanhaigh on 2008-04-10
Is the addon installed from the ubuntu repos rather than mozillas addon site?
Try uninstalling with ```
sudo apt-get remove mozilla-imagezoom
``` then using the addon site again (or reinstall the package)

---

### Post by satimis on 2008-04-10
> **ryanhaigh said:**
> Is the addon installed from the ubuntu repos rather than mozillas addon site?
Try uninstalling with ```
sudo apt-get remove mozilla-imagezoom
``` then using the addon site again (or reinstall the package)
I installed the package on the addon site;
[https://addons.mozilla.org/en-US/firefox/addon/139](https://addons.mozilla.org/en-US/firefox/addon/139)


NOT on repo

$ apt-cache policy mozilla-imagezoom```

mozilla-imagezoom:
  Installed: (none)
  Candidate: 0.2.7-8ubuntu2
  Version table:
     0.2.7-8ubuntu2 0
        500 http://us.archive.ubuntu.com feisty/universe Packages
```


Imagezoom is working.

Mouse
Pressing right button --> scroll mouse wheel

Enlarge/shrink the image.


Right click on image -->  Zoom image
is there.  But not on View drop menu


satimis

---

### Post by ryanhaigh on 2008-04-10
Go into tools>addons and click preferences make sure the show image zoom in view menu item is checked.

---

### Post by satimis on 2008-04-10
> **ryanhaigh said:**
> Go into tools>addons and click preferences make sure the show image zoom in view menu item is checked.
Sorry, there is no such an item.


satimis

---

### Post by ryanhaigh on 2008-04-10
Strange...as you can see I have the option to enable/disable the option you want to use. Perhaps I was not clear enough before? In firefox go to tools>addons>imagezoom>preferences and then check the box?

---

### Post by satimis on 2008-04-10
> **ryanhaigh said:**
> Strange...as you can see I have the option to enable/disable the option you want to use. Perhaps I was not clear enough before? In firefox go to tools>addons>imagezoom>preferences and then check the box?
Hi,


The Imagezoom version here is 0.31.  There is a minor difference on;```

[] Enable Global Zoom Functions

[] Show Autofit in Global Menu
[] Warn if Global Zoom is not set to default value

```


I check all of them then "Imagezoom" is on View drop menu.  Thanks


B.R.
satimis

---

### Post by satimis on 2008-04-12
Hi ryanhaigh and folks,


Something strange happened here.

"Enable Global Zoom Functions" can't be saved permanently.   On next boot this item is unchecked again resulting in;
View --> Image Zoom disappeared.


I tried to post on Imagezoom forum;

[http://imagezoom.yellowgorilla.net/forums/viewforum.php?id=4](http://imagezoom.yellowgorilla.net/forums/viewforum.php?id=4)


I can't submit my posting.  It complained'```

The following errors need to be corrected before the message can be posted:

    * To help prevent SPAM, you need to have javascript enabled to post to this forum. Enable javascript then reload the page to enter your message

```

On;

Edit --> Preferences --> Content 
Enable JavaScript
Enable Java

Already checked.


Please help.  TIA


B.R.
satimis

---

### Post by ryanhaigh on 2008-04-12
Sorry I can't offer a more helpful solution, the only thing I can recommend is to uninstall the extension from addons.mozilla.org and use the version in the repos as it is working perfectly for me. 

Alternately you could look at installing firefox 3beta5 which allows you to zoom the whole page (both text and images) with the ctrl+mousewheel. It is being included in the next version of ubuntu due out in a few days so it must be stable enough for daily use.

---

