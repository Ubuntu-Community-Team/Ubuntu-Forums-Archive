---
title: "Removing overlay-scrollbar"
date: 2013-03-13
forum: General Help
---

### Post by MrPCSmasher on 2013-03-13
I've seen many answers for how to remove the overlay scrollbar. 
```
sudo apt-get remove overlay-scrollbar
```
Here is a screenshot of running that command. It says overlay-scrollbar is not installed. 
But look at the right, there is the overlay-scrollbar. 

[ATTACH=CONFIG]240112[/ATTACH]
Any ideas?

---

### Post by vasa1 on 2013-03-13
Which OS is this?

---

### Post by MrPCSmasher on 2013-03-13
Ubuntu Studio 12.04

---

### Post by ajgreeny on 2013-03-13
There are a few **liboverlay-scrollbar** packages that you may need to remove as well.

I agree with you, I suspect, and feel that those things are almost unusable with the mouse on a big screen.  I can never find the flippin' things!

---

### Post by ibjsb4 on 2013-03-13
Wonder if the Classic solution would work in Studio.

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks#Disable_Overlay_Scrollbars](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks#Disable_Overlay_Scrollbars)

---

### Post by solarghost on 2013-03-13
I would recommend you install Ubuntu Tweak ([http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)), this makes some customization in Ubuntu some what easier.

---

### Post by MrPCSmasher on 2013-03-14
When i ran 
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get remove overlay-scrollbar[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]
the first time it showed some liboverlay-scrollbar items that were not in use and could be removed so I ran
```
sudo apt-get autoclean
```
which removed those things. So it indicated.
I just now ran 
```
sudo apt-get remove overlay*
```
and that removed some other stuff. So, don't know what I missed before now, but I got it now. I know it wasn't the suggestions in the post, however, ajgreeny's post made me think of it.
By the way, Ubuntu Tweak's website says it is for 11.10 and earlier.

Thanks to all who replied.[/FONT][/COLOR]

---

### Post by solarghost on 2013-03-16
> **MrPCSmasher said:**
> By the way, Ubuntu Tweak's website says it is for 11.10 and earlier.

I did not notice that :)

Well I still recommend you install Ubuntu Tweak, I use 12.10 and it works fine, it simplifies a ton of customizations.

If I remember correctly I used these instructions ([http://www.noobslab.com/2012/10/install-ubuntu-tweak-081-in-ubuntu.html](http://www.noobslab.com/2012/10/install-ubuntu-tweak-081-in-ubuntu.html))

Basically it's:

```

sudo add-apt-repository ppa:tualatrix/ppa 
sudo apt-get update
sudo apt-get install ubuntu-tweak

```

---

