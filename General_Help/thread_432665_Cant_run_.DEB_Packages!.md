---
title: "Cant run .DEB Packages?!"
date: 2007-05-04
forum: General Help
---

### Post by GSF1200S on 2007-05-04
Um yeah.. what else can I say. It doesnt matter what debian package I try to run.. I go to install package and it usually gives me dependency errors saying I need libraries.

Yeah, I guess I could seek out the libraries, but doesnt this defeat the purpose of debian packages? Im using kubuntu and im on 7.04.

Any advice would be great!

---

### Post by yopnono on 2007-05-04
Have you enabled all the repos?

---

### Post by GSF1200S on 2007-05-04
> **yopnono said:**
> Have you enabled all the repos?

yes, all of the repositories are enabled..

---

### Post by WW on 2007-05-04
Where are you getting the .deb packages that are causing the problem?  Could you give an example?

If you are trying to install .deb packages from, say, debian, you could very well run into dependency problems, because the required version of a dependency might not be available in the version of ubuntu that you are using.

---

### Post by nikhilk on 2007-05-04
How are you trying to install this .DEB? dpkg/apt-get/aptitude/Synaptic/Adept???

Just noticed this
> **GSF1200S said:**
> Im using kubuntu and im on 7.04
Kindly make the change in your profile (it says "Ubuntu 7.04 Feisty Fawn User").

---

### Post by GSF1200S on 2007-05-04
> **nikhilk said:**
> How are you trying to install this .DEB? pkg/apt-get/aptitude/Synaptic/Adept???

Just noticed this

Kindly make the change in your profile (it says "Ubuntu Feisty Fawn User").

I just switched to KDE, so I hadnt changed it yet.

Let me give you an example: I downloaded the virtualbox debian package for ubuntu, and it gave me an error saying that I was missing dependencies. Using:

sudo dpkg install -f  (I know this is wrong but im at work and dont have the text doc with this command.)

it would install the dependencies and all the deb packages in my /home directory.

---

### Post by nikhilk on 2007-05-05
Any specific reason for downloading the package first and then installing it with dpkg instead of installing using Adept?
> **GSF1200S said:**
> it would install the dependencies and all the deb packages in my /home directory.
So you were able to install it?

---

### Post by WW on 2007-05-05
Just to be sure, did you get the **Ubuntu 7.04** package from the [VirtualBox Downloads page]("http://www.virtualbox.org/wiki/Downloads")?

---

