---
title: "Lubuntu Software center - Cannot find any softwares"
date: 2012-10-23
forum: General Help
---

### Post by davidafranklin on 2012-10-23
Hello,

When I look for a program (let;s say Firefox, skype, teamviewer..) through the Lubuntu Software center, nothing ever shows up. It only finds softwares installed.

I do not remember this happening with 12.04.

Any suggestions?
Thanks

---

### Post by Ace..... on 2012-10-23
I'm running 12.04 and I can confirm that software centre displays all software :)

---

### Post by jerrrys on 2012-10-23
Have you updated?

sudo apt-get update

---

### Post by Rex Bouwense on 2012-10-23
Also make sure that you are not on the Installed Software Tab.

---

### Post by davidafranklin on 2012-10-23
sudo apt-get update did not do anything.

I am entering what I am looking for in the "Search a package" field and nothing comes up.

---

### Post by Rex Bouwense on 2012-10-23
What packages are you wanting to install?

---

### Post by davidafranklin on 2012-10-23
Anything.
If i even type just one letter like "e" in the search box, it onlyt gives me installed software, nothing additional.
My "Instaled Software" list is the same as my "``Get software"

---

### Post by vasa1 on 2012-10-23
Was this an upgrade from 12.04 or a clean install of 12.10? (I did a clean install and have no difficulty. If you did do an upgrade it's possible something got corrupted in the process?)

---

### Post by davidafranklin on 2012-10-24
> **vasa1 said:**
> Was this an upgrade from 12.04 or a clean install of 12.10? (I did a clean install and have no difficulty. If you did do an upgrade it's possible something got corrupted in the process?)

This is a clean install

---

### Post by vasa1 on 2012-10-24
> **davidafranklin said:**
> This is a clean install

Can you open it from a terminal and then tab back and forth between *get* and *installed*?
And watch what happens in the terminal. You may get some feedback.

---

### Post by davidafranklin on 2012-10-24
Not sure how to do that... I can open the terminl but from there, what do i need to type?

I could take several print screens to show you but cannot paste them into the forum.

---

### Post by davidafranklin on 2012-10-26
Hi All,

I found the solution, see this post:

[http://askubuntu.com/questions/151415/why-does-my-lubuntu-software-centre-only-show-installed-apps](http://askubuntu.com/questions/151415/why-does-my-lubuntu-software-centre-only-show-installed-apps)

Basically you have to reinstall LSC under the Synaptic PAckage Manager, then everything works fine.

Thanks

---

