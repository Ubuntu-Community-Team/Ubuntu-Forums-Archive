---
title: "How to install all the application manually by packages."
date: 2015-02-16
forum: General Help
---

### Post by krishfrz on 2015-02-16
Hello,i want to install VLC,Google chrome,amd radeon driver,music player and all the needed application i want,can i do this.if i so how can i install them and from where i can download them.sorry i am a noob here.
samsung np350v5cs02in:-
i5 ivybridge processor
amd HD 7670m(dedicated)
intel HD 4000(integrated)
1 TB HDD
4 GB RAM
thanx in advanced.

---

### Post by Bucky Ball on 2015-02-16
More information, please. If you have Ubuntu installed, or one of its flavours, you can install them from either Synaptics or the Software Centre.

If you want to start from scratch and just install the apps you want to use and nothing else (including your desktop environment of choice) you could try the [minimal install.]("https://help.ubuntu.com/community/Installation/MinimalCD") It installs the base kernel only. At first boot, you have a cursor where you can 'apt-get install' the what you want.

---

### Post by deadflowr on 2015-02-16
+1 to using the software center to start.

Most of what you want to install can be found in there.
However you need to go to google to get chrome

(You need to know what system of ubuntu you are using (64-bit, or 32-bit)
when you download chrome's installation package.)

To install chrome, after you download, find chrome's package.
(if you use firefox to download chrome, look in the program called Files >> Downloads)
simply double-click on the chrome package... It should be named something like google-chrome-stable-blah-blah.deb)
double-clicking will open the software center and you can install it from there.

There, of course, is a more complex way to get chrome which involves adding chrome repository information, but I feel it is best to start anyone new off slowly...
(And not confuse them, with odd terminal commands)


Ubuntu comes with radeon drivers already, they are open-source, and sometimes work great and sometimes not.
It also gives you the ability to install closed source drivers.
Open software and updates and go to Additional Drivers. Let it run it's check, and it'll show you a list of available drivers.
You can then choose which one you might want to try.

---

### Post by oldos2er on 2015-02-16
What exactly do you mean by "manually"? To me that would mean compiling and installing from source code, not packages.

If you want to work in a terminal (also referred to as CLI, [COLOR=#ff0000]C[/COLOR]ommand [COLOR=#ff0000][/COLOR][COLOR=#ff0000]L[/COLOR]ine [COLOR=#ff0000]I[/COLOR]nterface), see [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal) and [https://help.ubuntu.com/community/InstallingSoftware#Via_a_Text_Based_Methods](https://help.ubuntu.com/community/InstallingSoftware#Via_a_Text_Based_Methods)

---

### Post by krishfrz on 2015-02-16
I have installed ubuntu 14.04 LTS 64bit and i want to download there application pakages and after install them by terminal.

---

### Post by krishfrz on 2015-02-16
I have installed ubuntu 14.04 LTS and i want to download the application pakages and after install them so i can able to install them after even when i again make a fresh installation of ubuntu by terminal.

---

### Post by krishfrz on 2015-02-16
I mean download the application pakages then install by terminal(offline) so if i do not have a internet connection so i can install them without any problem.

---

### Post by Bucky Ball on 2015-02-17
> **krishfrz said:**
> I mean download the application pakages then install by terminal(offline) so if i do not have a internet connection so i can install them without any problem.

Not sure it makes much difference. You're downloading the packages, and apps, either way. Safer to install from the Software Centre or Synaptics to avoid missing dependencies.

---

### Post by Mark Phelps on 2015-02-17
Installing offline is a LOT of work.  When you download a package, it does not automatically search for and download the dependencies.  Then, when you move that package to the other machine and try to install it, it will halt at the first unsatisfied dependency it finds.  You then have to go back and download that package, move that package to the other machine, and start again.  

And ... you have to repeat this for every dependency the installer finds.

When you install connected to the Internet, the installer searches for the dependencies and adds them to the list to be downloaded for you.

---

### Post by Bucky Ball on 2015-02-17
On your friend's machine, or one that's online, download the ISO> burn to disk or USB.

install on your machine>do an update>install what you need from Software Centre or Synaptics, depending on the flavour.

A lot of the things your are looking for are probably already there. A music player and radeon driver are defaullt. All you would then need to do is install Chrome (or Chromium, which is also available in the Ubuntu repositories), and VLC (also in the repos, i.e Software Centre).

---

### Post by deadflowr on 2015-02-17
[AptOnCd]("https://help.ubuntu.com/community/APTonCD") is probably the kind of thing you'd want to look at.

(Note, in newer versions of Ubuntu you click on add volume, instead of add cdrom, fwiw)

---

