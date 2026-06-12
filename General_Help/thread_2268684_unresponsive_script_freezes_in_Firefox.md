---
title: "unresponsive script freezes in Firefox"
date: 2015-03-10
forum: General Help
---

### Post by pagnes on 2015-03-10
hello, I have continous unresponsive script messages woth Firefox on my older pc 
(AMD athlon 64 processor 3000+
cache 512 kb
memory 500 MB
Ubuntu 14.04.2 LTS)
i have tried all the advices on [https://support.mozilla.org/en-US/kb/warning-unresponsive-script](https://support.mozilla.org/en-US/kb/warning-unresponsive-script) and other pages, (letting it run longer, taking off all the extensions, using yescript, noscript, etc) - no way :(
it happens surely on facebook and Gmail, but on other pages too (video embed and other scripts)

It's very frustrating...

I have tried also Midori but instead of freezing it simply crashes.

---

### Post by yetimon_64 on 2015-03-10
Have a look at the minimum requirements to run ubuntu desktop, [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements).
Your system is just under/on the memory requirements, it may run, but it won't do so very well, add on the loading of firefox and then have it try to run a script ... is likely to be problematic to use at best.

I would recommend a lighter distro of Ubuntu like Xubuntu or Lubuntu, which use the lighter desktops XFCE and LXDE respectively. They may fare better on such older hardware. Regards, yeti.

Edit: just noted the tag on the thread title. Are you already using Lubuntu and still having a problem ?
> (AMD athlon 64 processor 3000+
cache 512 kb
memory 500 MB
**Ubuntu 14.04.2 LTS**)

---

### Post by pagnes on 2015-03-11
thank you, but I am actually already using  Lubuntu (Desktop Environment LXDE (Lubuntu)) for this reason

---

### Post by dragonfly41 on 2015-03-11
> hello, I have continous unresponsive script messages woth Firefox on my older pc 
...
i have tried .. (letting it run longer, taking off all the extensions, using yescript, noscript, etc) - no way :sad:
it happens surely on facebook and Gmail, but on other pages too (video embed and other scripts)

How many tabs do you keep open in Firefox?

At times I get this "unresponsive script" message on Ubuntu 14.04 and then I use All Tabs add-on .. list all tabs .. search mode .. to search through the tabs title | url | content for (typically) youtube or other video site which is often the culprit.  
This approach works also for video audio playing in background due to a tab being left running.

Firefox Session Manager is another useful add-on so that you can selectively disable tabs before Firefox is launched.

---

### Post by Holger_Gehrke on 2015-03-11
On a freshly booted machine with 1GB of RAM running Lubuntu 14.04 firefox takes 190M just after start. After going to just three websites (a webcomic, slashdot and ubuntuforum) it's at almost 250M resident size. Firefox should have been renamed to firememoryhog ages ago. I only see two options for you: get more ram or another browser. 

On another note, even having enough memory doesn't protect you from bad scripts: on a CMS I used to use, opening a page for editing involved selecting it from a tree of pages. This tree was transmitted completely expanded and then 'folded up' by a script. With several hundreds of pages in there, the page was about  2M and took something like 5 minutes from clicking on the link to the point where you could work with it.

---

### Post by nerdtron on 2015-03-11
And a more important question. Do you have add-ons installed on firefox?
Even with 4GB ram on my machine I experience that error fairly often that I noticed it. If you have adblock, flash block, no script, ghostery or other add-ons they may cause that browser behavior because some "heavy" websites are not functioning properly when you block something on their page.

---

### Post by pagnes on 2015-03-12
thank you all :)
- yes, I use some add-ons, actually noscript has been added for the reason of resolving this issue. However I have tested "clean" Firefox without any add-ons (either disabling them or restoring Firefox to initial state), without success.
- yes, I often use multiple tabs but it happens also when only one or two tabs are open
- I have measured memory use during Firefox and it was very intensive, but Midori was quite the same. I insist a bit on Firefox as I have hundred of passwords and bookmarks saved on it and syncronized with my other pcs.
- being an old pc it is not convenient to add more memory, another block of 500 MB of this type would cost about 50$, I prefer to do a total upgrade (changing mother board and everything) when neccessary, until then I'd like to use for non impegnative tasks this pc.

---

