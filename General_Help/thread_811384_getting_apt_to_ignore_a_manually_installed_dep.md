---
title: "getting apt to ignore a manually installed dep"
date: 2008-05-29
forum: General Help
---

### Post by orange on 2008-05-29
Hi all,

I manually installed two packages (want a custom kernel for a xen instance) from a different source.
Now, of course, apt sees these two deb as not being part of the framework and chokes:

The following packages have unmet dependencies.
  linux-headers-2.6.24-16-xen: Depends: linux-headers-2.6.24-16 but it is not installable
  linux-image-2.6.24-16-xen: Depends: module-init-tools (>= 3.3-pre11-4ubuntu3) but 3.3-pre4-2ubuntu4 is installed
E: Unmet dependencies. Try using -f.


of course apt-get -f install simply wants to remove them - how can I get apt to ignore these packages?

tia

-orange

---

### Post by sdennie on 2008-05-29
If you are **really** sure you want to do this, you could try using the --force-all argument to dpkg.

---

### Post by zvacet on 2008-05-29
I don´t think this is a reason but check system>admin>software sources>check all under Ubuntu software and update tab and reload.Just to be sure that you have all repos open.Do you have linux-image 2.6.24-17 installed?I think that can stop you to install packages you want,because system will not install lower version of package.Chech in synaptic that you have linux-image 2.6.24-16 and linux-image 2.6.24-17 installed and if you do remove linux-image 2.6.24-17.Thart way you will have just linux-image 2.6.24-16 and you should be able to install packages you want.

---

### Post by orange on 2008-05-29
> **vor said:**
> If you are **really** sure you want to do this, you could try using the --force-all argument to dpkg.

Yip - I'm **really** sure I want these two additional packages installed, so much so that I have already manually installed them using:

dpkg --ignore-depends=module-init-tools -i linux-image-2.6.24-16-xen_2.6.24-16.30zng1_i386.deb
dpkg --ignore-depends=linux-headers-2.6.24-16 -i linux-headers-2.6.24-16-xen_2.6.24-16.30zng1_i386.deb

now, however, I need to make sure that apt can continue, so, somehow i need to get apt to ignore the fact that they are there......

---

### Post by orange on 2008-05-29
> **zvacet said:**
> I don´t think this is a reason but check system>admin>software sources>check all under Ubuntu software and update tab and reload.Just to be sure that you have all repos open.Do you have linux-image 2.6.24-17 installed?I think that can stop you to install packages you want,because system will not install lower version of package.Chech in synaptic that you have linux-image 2.6.24-16 and linux-image 2.6.24-17 installed and if you do remove linux-image 2.6.24-17.Thart way you will have just linux-image 2.6.24-16 and you should be able to install packages you want.

K - this is a server - so no gui installed.

As mentioned in my reply to the previous poster, I have already installed the packages - just trying to get them ignored by the apt infrastructure.

So far I have tried:

creating /etc/apt/preferences
containing

Package: linux-image
Pin: version 2.6.24-16-xen
Pin-Priority: -1
Package: linux-headers
Pin: version 2.6.24-16
Pin-Priority: -1

no go

I then tried:

dpkg --set-selections <currentselections.txt
with currentselections.txt containing 

linux-headers-2.6.24-16-xen                     hold
linux-image                                     hold

still - apt thinks it needs to take care of these packages... and tries to do so - i want to tell it to ignore them.....

---

