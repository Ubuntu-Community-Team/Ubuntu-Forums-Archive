---
title: "Make a Barebones ubuntu live cd"
date: 2007-07-31
forum: General Help
---

### Post by chuwy on 2007-07-31
Hey guys, I love ubuntu, this is my first post so please excuse me if I have posted in the wrong section!

Basically, I want to make a customized live cd, but I want to make it 'barebones'.

On my normal ubuntu installs, i download and burn an [Ubuntu Minimal iso]("https://help.ubuntu.com/community/Installation/MinimalCD"). Once the minimal ubuntu is installed and i am logged into the command line, I type in:

> sudo aptitude install x-window-system-core gnome-core gdm firefox synaptic xubuntu-system-tools gnome-app-install

this installs all the minimum software I need for a basic ubuntu install. From there I can install more software as needed.

Basically, how would I get this type of ubuntu into a live cd environment? I know of software like Reconstructor and Uck, and I have successfully used them to change things such as wallpapers and icons etc, but when it comes to more advanced stuff this is where i get stuck!

Thanks alot for all your help, ubuntu is just fantastic.

---

### Post by rjohnsonxx00 on 2007-08-03
Sounds good.  I would like to identify an absolutely minimum installation of Ubuntu, just what is necessary to support my application.  Would your procedure help me do this?

Thanks!

Richard Johnson
[email]rjohnsonxx00@yahoo.com[/email]

---

### Post by splintercellguy on 2007-08-03
Ubuntu Server gives a pretty minimal install.

---

### Post by az on 2007-08-03
I started a wiki page about that.  Here:
[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

I have been working on that for another project ([http://rescubuntu.info/](http://rescubuntu.info/))

That wiki page needs to be improved, to add the details about how to make ubiquity work from a remixed live cd.  Please, try it out and add your ideas to the page.

(Look at the contents of the ubuntu-live task - (run: tasksel --task-packages ubuntu-live).  Try installing the ubiquity-relevant packages.  Take a look at how to run ubiquity in various user interfaces)

---

