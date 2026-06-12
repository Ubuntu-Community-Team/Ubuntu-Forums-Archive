---
title: "Lubuntu/linux questions from a noob"
date: 2019-10-19
forum: General Help
---

### Post by donkidonki on 2019-10-19
Any feedback would be greatly appreciated. 

Due to windows 7 end of date soon I downloaded lubuntu 19.4 as my main os and put it on the hard drive,I love it. However its end of term date is only January. 
Q1. Will they replace it and add a new version to download again after this?
Q2. What is the resolution? I have a HD screen and i want to make use of it. No distro seems to mention this or am I just asking daft questions? 
Q3. Why does linux on seemingly all distro not require a gpu. 
&#128075;

---

### Post by DuckHook on 2019-10-19
Welcome to Ubuntu and Linux, donkidonki.
> **donkidonki said:**
> &#8230;
Q1. Will they replace it and add a new version to download again after this?
Ubuntu follows a convention wherein LTS (Long Term Support) versions are meant for most users. The main flavour LTSes last for five years. They are produced every two years on the April release, hence, 16.04 and 18.04 are LTS. The next one will be 20.04

The other releases are called standard releases, but the use of the word "standard" is unfortunately something of a misleading misnomer. Standard releases are not really meant for the majority of users, but for those with bleeding-edge HW, or who want the latest less stable features or who are interested in testing and reporting bugs. They come out every six months and only last nine months, hence users must be committed to running on the upgrade hamster wheel. I do not recommend standard releases for everyday users, but since you are already there, you may as well install 19.10 which just came out yesterday. It won't be available for a network upgrade for a few days yet. When it is, your OS should automatically alert you to its availability and then it is simply a matter of following instructions to install it. Then, when 20.04 rolls around, I recommend that you stick with that one for the long term and not upgrade until 22.04, or even 24.04.

Before doing so, back up all of your important data. Please read the link in my sig.
> Q2. What is the resolution? I have a HD screen and i want to make use of it. No distro seems to mention this or am I just asking daft questions? 
Ubuntu should automatically detect the best resolution for your monitor in most recent HW. Old HW is another matter, but new-ish HW is usually fine. It is also possible to change resolutions once installed.
> Q3. Why does linux on seemingly all distro not require a gpu.
All modern OSes make use of a GPU and Linux is no different. Perhaps I am not understanding your question.

---

### Post by guiverc on 2019-10-19
just fyi:  Ubuntu 19.04 means the 2019-April release; ie. Ubuntu releases use a *yy.mm* format so it's easy to calculate when a release reaches EOL.  9 months for standard as @DuckHook already stated; or 5 years for LTS, however note it's 3 years for flavors like Lubuntu, but you should still check release notes for exact details.

---

### Post by Artim on 2019-10-20
And welcome to the world of Linux!  It's big, beautiful, and free!  I'm a fan of [COLOR=#0000cd]**Xubuntu**[/COLOR] (LTS versions), in part because I think it's the easiest and simplest interface for newbies.

---

### Post by TheFu on 2019-10-20
DuckHook covered it nicely, but some more reading, if you like: [https://ubuntu.com/about/release-cycle](https://ubuntu.com/about/release-cycle)
[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

And my personal beliefs about which release should be used: [https://blog.jdpfu.com/2013/07/19/why-ubuntu-users-should-run-an-lts-release](https://blog.jdpfu.com/2013/07/19/why-ubuntu-users-should-run-an-lts-release)

>  Q3. Why does linux on seemingly all distro not require a gpu. 

Not all distros are desktop distros, so they are only accessed over a network or using something called "a console."  Why spend any money for hardware that a specific distro won't use? As an end-user, it is unlikely that you would deploy any distro that doesn't need, at least, some minor level of GPU. At least VESA support. The most likely would be some specialized router distro or network monitoring distro that would only have a web interface to manage and configure it.  By default, all Ubuntu distros require *some* sort of GPU, but it is just because using GPU APIs to show text is well-understood. It is possible to configure Ubuntu Server to only use a serial console, if you like. This would be pure text output.

You could buy a Raspberry Pi Zero, which doesn't have any GUI capability.  Normal Raspberry Pi v4 computers have reasonable GUI capabilities which support 2 4K displays. Not bad for a $35 computer.

In the Unix world, it is very common to access systems remotely through ssh. ssh provides a text-only interface which is secure, but behaves like a local terminal.  There is no mouse, now windows, no GUI for that connection.  If you've heard of VPS or "cloud" servers, they don't normally have any GUI.  The internet is run on Linux systems that don't have any GUI at all.  GUIs tend to require the most processing power on any computer. If we avoid even loading a GUI, that power can be put to work processing other things, like more data, faster webpages, more programs, more files.

To someone used to MS-Windows, these ideas might strange.  In the end, it really comes down to being efficient.  Through a text-only interface, a capable single Unix admin can manage 2, 20, 200, 2000, 20,000 servers with little difference and no paid tools.  Typing a single command and having it run on 20,000 servers is pretty cool, but it is also a way to break 20,000 servers quickly if a mistake is made.

---

### Post by mörgæs on 2019-10-20
If I may modify Duckhook's post a little: If 19.04 works without problems for your hardware then I suggest staying with it until January when support ends (the precise date is not given yet but will be posted here in Ubuntuforums). At that time do a fresh install of 19.10. When that is out of support in July 2020 do a fresh install of 20.04 which can be kept for three years.

---

