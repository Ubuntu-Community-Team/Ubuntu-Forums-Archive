---
title: "Information Kiosk/Monitor"
date: 2013-06-30
forum: General Help
---

### Post by rathodr on 2013-06-30
I am in process of installing Ubuntu monitor for our religious organization. In this scenario, I simply want to display information .... no keyboard or mouse will be available.

Here are my needs:
1. Monitor to display various types of content: service prices, events, pictures (JPG, PNG, etc.), PDF, PPT, etc.
2. Must be totally automated. When system turns on in the morning, logs into a generic account and begins to display content in #1.
3. Full-screen so no borders are showing
4. The contents (perhaps in a directory) can be updated dynamically by FTPing files to the PC or by copying over the network.

I am able to code something in Pythin, BSH, etc. but am hoping an out-of-box solution (or somthing configurable) is available.

Any thoughts?

---

### Post by elliotn on 2013-06-30
am clueless but also wanna know how to do that

---

### Post by achelis on 2013-06-30
For hardware you could check out Raspberry-Pi. It's fairly cheap and uses significantly less power than a full blown computer and for just showing stuff on screen you shouldn't really need more computation power.
It runs Raspbian - a Debian variant. FTP/SSH is fairly easy to set up. With ssh you could control everything from another computer.

For software I don't know of any single program that meets your demands -  which if I understand correctly is to display files of a lot of different formats on screen.
I guess most of it could be deployed as a web-page and shown fullscreen in a browser. But for powerpoint you would need something else...

Unless you need to automatically switch between what is shown I'd propably just use whatever program is appropriate for the current thing you want to show.

That's my two cents.

---

### Post by oldfred on 2013-06-30
This question pops up regularly so I have saved some links. 
Not sure if they will help with what you want?

Kiosk discussions:
[http://ubuntuforums.org/showthread.php?t=2113023](http://ubuntuforums.org/showthread.php?t=2113023)
[http://ubuntuforums.org/showthread.php?t=1872560](http://ubuntuforums.org/showthread.php?t=1872560)
[http://ubuntuforums.org/showthread.php?t=1881141](http://ubuntuforums.org/showthread.php?t=1881141)
[http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/](http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/)
[http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/](http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/)
chromium kiosk using Tiny Core Linux. Talk about small and light!
[http://ubuntuforums.org/showthread.php?t=1891594](http://ubuntuforums.org/showthread.php?t=1891594)
[http://spins.fedoraproject.org/kiosk/#home](http://spins.fedoraproject.org/kiosk/#home)
Older
[http://users.telenet.be/mydotcom/howto/linuxkiosk/intro.htm](http://users.telenet.be/mydotcom/howto/linuxkiosk/intro.htm)
[http://jacob.steelsmith.org/category/section/ubuntu-kiosk-edition](http://jacob.steelsmith.org/category/section/ubuntu-kiosk-edition)

---

