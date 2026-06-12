---
title: "How To Check Whether Or Not My Ubuntu Computer Has Already Had Synaptics installed?"
date: 2015-03-13
forum: General Help
---

### Post by newbie14 on 2015-03-13
My ubuntu computer is not connected to the internet and will nevercan. My ubuntu computer is eternally offline.
I did these steps to check it:
1. There is an icon on the left side of the desktop screen named“ubuntu software center”.
2. I single-left-clicked the “ubuntu software center” icon.
3. The “Ubuntu software center” window appears.
4. I single-left-clicked the “installed” icon / tab at the top ofthe “ubuntu software center”.
5. The “ubuntu software center” shows a list of categories. Thecategories are:
    accessories
    Developer Tools
    Games
    Graphics
    Internet
    Office
    Sound & Video
    Themes & Tweaks
    Universal Access
    Uncategorized.
6. I  single-left-clicked the “accessories”
7. a list of programs appears below the “accesories”. But none ofthem are named “synaptics”.
8. I single-left-clicked the “Developer Tools”.
9. a list of programs appears below the “Developer Tools” tree.But none of the are named “synaptics”.
10. I single-left-clicked the “Games”.
11. a list of programs appears below the “Games” tree. But noneof the are named “synaptics”.
12. I single-left-clicked the “Graphics”.
13. a list of programs appears below the “Graphics” tree. Butnone of the are named “synaptics”.
14. I single-left-clicked the “Internet”.
15. a list of programs appears below the “Internet” tree. Butnone of the are named “synaptics”.
16. I single-left-clicked the “ Office”.
17. a list of programs appears below the “Office” tree. But noneof the are named “synaptics”.
18. I single-left-clicked the “Sound & Video”.
19. a list of programs appears below the “Sound & Video”tree. But none of the are named “synaptics”.
20. I single-left-clicked the “Themes & Tweaks”.
21. a list of programs appears below the “Themes & Tweaks”tree. But none of the are named “synaptics”.
22. I single-left-clicked the “Universal Access”.
23. a list of programs appears below the “Universal Access” tree.But none of the are named “synaptics”.
24. I single-left-clicked the “Uncategorized”.
25. a list of programs appears below the “Uncategorized” tree.But none of the are named “synaptics”.
26. From those steps, I concluded that “synaptics” is not yetinstalled in/on my Ubuntu computer.


My questions are:
1. Is there any step that I did wrong or miss?
2. Is there a more practical way to check whether or not “synaptics”had already been installed on/in my ubuntu computer?
3. Is there a specific code I can type in the “terminal” programto find out whether or not “synaptics” had been already installedin/on my Ubuntu computer?


Thank You.

---

### Post by dragonfly41 on 2015-03-13
Are you are looking for Synaptic Package Manager?

In launching Ubuntu Software Centre if you had used search Synaptic (not synaptic[COLOR=#ff0000]**s**[/COLOR]) 
you would see Synaptic Package Manager which you can then install. 

search Synaptics does show other synaptics packages. e.g. [http://apt.ubuntu.com/p/xserver-xorg-input-synaptics](http://apt.ubuntu.com/p/xserver-xorg-input-synaptics)

When Synaptic Package Manager is installed (I use Gnome Classic rather than Unity) you will see it here ..

Applications > System Tools > Administration > Synaptic Package Manager

If in command terminal I run "which synaptic" I see /usr/sbin/synaptic


[later edit]

After reading again I see that you have no Internet connection so you will not be able to install.

But you can use "which" or 

sudo updatedb
sudo locate synaptic

to hunt for it.

---

### Post by newbie14 on 2015-03-13
> **dragonfly41 said:**
> Are you are looking for Synaptic Package Manager?

In launching Ubuntu Software Centre if you had used search Synaptic (not synaptic[COLOR=#ff0000]**s**[/COLOR]) 
you would see Synaptic Package Manager which you can then install. 

search Synaptics does show other synaptics packages. e.g. [http://apt.ubuntu.com/p/xserver-xorg-input-synaptics](http://apt.ubuntu.com/p/xserver-xorg-input-synaptics)

When Synaptic Package Manager is installed (I use Gnome Classic rather than Unity) you will see it here ..

Applications > System Tools > Administration > Synaptic Package Manager

If in command terminal I run "which synaptic" I see /usr/sbin/synaptic


[later edit]

After reading again I see that you have no Internet connection so you will not be able to install.

But you can use "which" or 

sudo updatedb
sudo locate synaptic

to hunt for it.


I launched the "Ubuntu Software Center.
I searched "Synaptic"
and then I see two "Synaptic" like this:

[http://imgur.com/TD2O0hU](http://imgur.com/TD2O0hU)
[IMG]http://imgur.com/TD2O0hU[/IMG]
Does this mean I have already had the "synaptic" installed on/in my ubuntu computer?

---

### Post by v3.xx on 2015-03-13
> 3. Is there a specific code I can type in the “terminal” programto find out whether or not “synaptics” had been already installedin/on my Ubuntu computer?
```
apt-cache policy synaptic
```
Will tell you if its installed and ..
```
sudo apt-get install synaptic
```
will install it

[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

---

### Post by deadflowr on 2015-03-14
> **newbie14 said:**
> I launched the "Ubuntu Software Center.
I searched "Synaptic"
and then I see two "Synaptic" like this:

[http://imgur.com/TD2O0hU](http://imgur.com/TD2O0hU)
[IMG]http://imgur.com/TD2O0hU[/IMG]
Does this mean I have already had the "synaptic" installed on/in my ubuntu computer?

No.
An installed package in the software center would have a check on the package icon like so

---

### Post by newbie14 on 2015-03-14
> **v3.xx said:**
> ```
apt-cache policy synaptic
```
Will tell you if its installed 

Spot on, Sir. This code is the exact answer of my question.
I typed that code in to terminal.
The terminal replied with this:

yggdrasil@Fulani:~$ apt-cache policy synaptic 
synaptic: 
  Installed: (none) 
  Candidate: (none) 
  Version table: 
yggdrasil@Fulani:~$

The third line confirms that my ubuntu computer has no synaptic installed.


Thank You very much Mr. deadflowr

---

### Post by grahammechanical on 2015-03-14
If my memory is correct then Ubuntu 12.04 was the last version of Ubuntu to have Synaptic Package Manager installed as part of the default set of applications.

---

### Post by deadflowr on 2015-03-14
> **grahammechanical said:**
> If my memory is correct then Ubuntu 12.04 was the last version of Ubuntu to have Synaptic Package Manager installed as part of the default set of applications.

Your memory needs to go back even further.

---

### Post by v3.xx on 2015-03-14
Non the less, its still there and the op shows no candidate.  Whats with that?
Is this system updated?

And your welcome :)

Ok, my bad.  Your offline.

Edit: About being offline
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=offline+update+upgrade&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=offline+update+upgrade&sa=Search&cof=FORID:9)

[https://www.osdisc.com/products/linux/ubuntu/ubuntu-1404-lts-software-repository-32bit.html](https://www.osdisc.com/products/linux/ubuntu/ubuntu-1404-lts-software-repository-32bit.html)

---

