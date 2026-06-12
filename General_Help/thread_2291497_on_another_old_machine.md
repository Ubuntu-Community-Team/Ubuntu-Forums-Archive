---
title: "on another old machine"
date: 2015-08-20
forum: General Help
---

### Post by WacoJohn on 2015-08-20
Old Windows ME desktop ... 512MB RAM, 10G HD.  Need more disk space so thought I could uninstall some things I will never need, . such as bluetooth support, CD burning,  etc.  In Synaptics pkg manager, I find such things, ... but it tells me some discerning things:

Example
BlueZ is the official Linux Bluetooth protocol stack.

Mark for complete removal gives blueman, bluez-alsa, and lubuntu-desktop to be removed.  Hmmm, don't want to remove the desktop .. I don't think  So, I go to lubuntu-desktop to see what it says about removing it, ... and it says:

> This metapackage package depends on all components of Lubuntu Desktop system.

It is also used to help ensure proper upgrades, [B]but it can be safely removed
if you want to remove some applications installed by default[/B].

Wondering if someone can explain the bold text.  To proceed with dumping the bluetoolh support, etc., how would I go about it .... if at all???  I get the feeling 'pruning' Lubuntu can/will be a very daunting task.  Thanks in advance for any and all comments etc.

---

### Post by tgalati4 on 2015-08-20
Since Lubuntu is already a "light" distibution, any system deletions can lead to system breakage.  Many packages are "meta" packages--a collection of packages--so when you try to remove the "meta" package, it will remove a lot of stuff that you don't want to remove.

Your main problem is a 10 GB hard disk.  Find a 30 GB hard disk.  Go to a PC fix-it shop and buy a used hard drive for a few dollars.  Otherwise, you need to run a super light desktop such as Tiny Core linux.  

Add more RAM if you can, but you really need a bigger disk, or put in a second disk for your /home partition so your personal data files won't crowd out the operating system.

On these older systems, you can use an IDE SSD--these are solid-state hard disks used in industrial computers--they are reasonably fast and come in decent sizes that work well with Linux.  Do a web search for them.

---

### Post by WacoJohn on 2015-08-20
Great answer.  Thank you.  Ram is maxed out.  Another hd is the best solution.  Thank you again.

---

### Post by mörgæs on 2015-08-20
> **tgalati4 said:**
> Since Lubuntu is already a "light" distibution,  any system deletions can lead to system breakage. 


No, a lot of apps can safely be removed. Gnumeric, Abiword... A [core install]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall") is an example of a well-functioning Lubuntu without unnecessary apps.


> **tgalati4 said:**
>  Many packages are "meta" packages--a collection of packages--


Right.


> **tgalati4 said:**
> so when you try to remove the  "meta" package, it will remove a lot of stuff that you don't want to  remove.


Wrong. Removing a meta package is safe but there is not much gained.


And, by the way, 10 GB is more than enough for a core Lubuntu.

---

### Post by WacoJohn on 2015-08-20
> **mörgæs said:**
> No, a lot of apps can safely be removed. Gnumeric, Abiword... A [core install]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall") is an example of a well-functioning Lubuntu without unnecessary apps.

Right.

Wrong. Removing a meta package is safe but there is not much gained.


And, by the way, 10 GB is more than enough for a core Lubuntu.

OK.  Don't mean to beat this to death ... but trying to learn.  If it is a meta package, ok to remove ... but not much gain.  What about when it says it is going to remove a DESKTOP???  That doesn't sound good to me.  It DOES say **but it can be safely removed if you want to remove some applications installed by default.  **Kinda what I thought I wanted to do ... but removing a desktop??  Heck, .. I need the desktop.  If someone could explain ......

---

### Post by kerry_s on 2015-08-20
512mb ram, go with something else, like puppy os or core os, there built for low ram.

any *buntu version will use like 200+mb ram just starting up, once you start a app you'll probably lockup up as it tries to swap for more memory.
your going to spend a lot of time waiting instead of using that computer.

---

### Post by WacoJohn on 2015-08-20
About to give tinycore a try and if fail, bigger drive. If I can't run Linux on it then will have to dumpster it. Been running Lubuntu with 512 for 5 years. Thanks everyone for all the help.

---

### Post by Yellow Pasque on 2015-08-20
> **WacoJohn said:**
> What about when it says it is going to remove a DESKTOP???  That doesn't sound good to me.  It DOES say **but it can be safely removed if you want to remove some applications installed by default.  **Kinda what I thought I wanted to do ... but removing a desktop??  Heck, .. I need the desktop.  If someone could explain ......

As already explained, it's not literally removing the desktop. It's just a very confusing name (this forum is littered with similar, "OMG! Not my desktop!" comments).

---

### Post by WacoJohn on 2015-08-20
> **Temüjin said:**
> As already explained, it's not literally removing the desktop. It's just a very confusing name (this forum is littered with similar, "OMG! Not my desktop!" comments).

Explained where?  You are the first to mention "it's not literally removing the desktop".  It never occurred to me to search for the litter.  I certainly do sincerely thank you though for a direct answer to the question.

---

### Post by tgalati4 on 2015-08-21
And an equal number of posts with broken desktops because something got removed that wasn't supposed to.

I'm running MATE, if I remove the desktop meta-package, bad things happen:

> tgalati4@Mint17 ~ $ sudo apt-get remove mate-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libaudiofile1 libesd0 libsvga1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  caja mate-applets mate-control-center mate-desktop mate-indicator-applet
  mate-media mate-media-pulse mate-panel mint-meta-mate
0 upgraded, 0 newly installed, 9 to remove and 18 not upgraded.
After this operation, 18.1 MB disk space will be freed.
Do you want to continue? [Y/n] 

So, yes, technically you can remove a meta-package and then reinstall the individual packages to get back to where you were, but if you remove a bunch of stuff trying to save some space, you quickly get in trouble.

---

### Post by WacoJohn on 2015-08-21
> [COLOR=#000000]So, yes, technically you can remove a meta-package and then reinstall the individual packages to get back to where you were, but if you remove a bunch of stuff trying to save some space, you quickly get in trouble.[/COLOR]

I am certainly being educated.  Thank you for this bit of wisdom.  I could use a few more MB of space .. but for now .. will stick with an installation of Tiny ... and if not .. then a bigger drive.  Thank you again.

---

### Post by Yellow Pasque on 2015-08-21
> I'm running MATE, if I remove the desktop meta-package, bad things happen
That's because mate-desktop is not a metapackage like the other ubuntu-desktop packages we're talking about here. As if it wasn't confusing enough, Ubuntu MATE had to name their metapackage mate-desktop-environment. Sigh...

> So, yes, technically you can remove a meta-package and then reinstall the individual packages to get back to where you were
Removing the metapackage does not remove the packages that it depends on.  It is safe to remove the "-desktop" metapackages, though Ubuntu recommends that you install it before upgrading to the next version of Ubuntu.

---

### Post by Bucky Ball on 2015-08-21
> **WacoJohn said:**
> I am certainly being educated.  Thank you for this bit of wisdom.  I could use a few more MB of space .. but for now .. will stick with an installation of Tiny ... and if not .. then a bigger drive.  Thank you again.

If you are satisfied with the support and outcome please mark the thread as solved. See the first link in my signature for how. Good luck. :)

---

### Post by mörgæs on 2015-08-21
A meta package is sometimes called a shopping list for packages. After the shopping cart is full there is no need for the list, which can be deleted. 
Moreover, deleting the list is a logical step if one or more items (applications) are removed from the cart afterwards. Hence Lubuntu does this automatically.

Lubuntu-core is simply a shorter shopping list.

If you want to save hard disk space there is some advice in the link in my signature.

---

### Post by howefield on 2015-08-21
> **WacoJohn said:**
> ... could use a few more MB of space .. 

Depending on how long you have had the install (updating and installing packages) you'll probably get something back by cleaning out the apt cache.  

```
sudo apt-get clean
```
```
sudo apt-get autoclean
```
```
sudo apt-get remove
```

Not that it really matters, using a 10g hard disk with 512 of memory probably isn't a hugely pleasant experience.

---

