---
title: "Editing the grub to allow a different default"
date: 2006-11-12
forum: General Help
---

### Post by karan733 on 2006-11-12
Hi guys

Im still struggling to get used to Ubuntu, and still need to use windows as a default (and go into ubuntu when im in learning mode!) - but the grub default is to go into ubuntu, with windows listed under other operating systems.

how can i edit grub so that either it takes away the 5-6 second timeout, or edit it so the default selection after timeout is windows, and the secondary options are ubuntu?

thank you, sorry if i posted this in the wrong thread!
karan

---

### Post by Herman on 2006-11-13
I can imagine it must be a real nuisance to people when they have to put up with a certain other operating system that seems to require rebooting for just about any excuse. (That is when you aren't scanning or updating all the scanning utilities). :D

Anyway, I think the easiest and probably best thing for you to do would be to just edit the line for default in your /boot/grub/menu.lst file by replacing the number 0 with the word 'saved'. To see what I mean, [click here.]("http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc")

Elsewhere on the same web page you will find a good number of other ways in which you can customize the way Grub boots up your computer, I hope you enjoy it, Grub is the greatest! :D

Edit: and for those of us who are really new I recommend scrolling to the top of the page and reading down, then you will have a more complete explanation of what you will need to know.

Regards, Herman :cool:

---

### Post by Tomosaur on 2006-11-13
Herman's page is very useful, although what you need to is very easily achieved like this:

Open up a terminal, and type:
```

gksudo gedit /boot/grub/menu.lst

```

Type in your password, then once gedit opens up, scroll all the way down to the bottom of the file. You'll see a few references to whichever operating systems you have installed. Ubuntu normally puts itself at the top of the list, so this will be menu item 0, since Grub counts from zero. All you need to do is count (from zero), to your windows reference. The 'Other Operating Systems' line should be included in your count. So let's say your menu file looks like this at the bottom:
```

title Ubuntu
...

title Ubuntu Recovery
...

title Other Operating Systems
...

title Windows XP

```

then your windows installation is menu item 3. Scroll back to the top of the file and look for the line which says 'Default 0'. Change the 0 to whichever number you just counted, save the file, and exit.

If you don't feel comfortable editing the file by hand, then there are other options available to you. Check the link in my sig for a GUI script which will let you edit the grub menu, or there is another GUI grub editor which was released just recently. It is also in the HOWTO section, although I can't remember the exact name of it. Either will do what you want to do, it's just a matter of preference. You may want to do a tag search on grub to find other examples before you go changing anything you're unsure about.

---

