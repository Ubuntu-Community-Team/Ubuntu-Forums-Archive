---
title: "Samba unable to share external drive"
date: 2019-05-17
forum: General Help
---

### Post by lanternmywilly on 2019-05-17
Hello everyone

I'm actually looking for a solution on my Raspbian RaspberryPi but I figured some of you would be able to help me.

So I'm quite new to the Linux community so I'm having some issues with Samba.

Here's what I'm trying to do:
I've got an external drive connected to my raspberryPi (permanently) and I want to share this drive with Samba so I can add files to it from my laptop.

Now, I've followed several tutorials on how to properly install and connect samba to a Windows 10 system and I've been able to connect with my /home/pi folder but that's it.

I'll add several screenshot to give you an idea of what I've been doing and where I mounted my external drive.

To give you an idea of how my drive is connected/mounted:
h[ttps://imgur.com/81rb8RS]("https://imgur.com/81rb8RS")
[https://imgur.com/pqjBsZR](https://imgur.com/pqjBsZR)
[https://imgur.com/nbqSo2F](https://imgur.com/nbqSo2F)

My smb.conf file:
[https://imgur.com/P3vNiDE](https://imgur.com/P3vNiDE)[IMG]https://imgur.com/81rb8RS[/IMG]
[https://imgur.com/knpqmu5](https://imgur.com/knpqmu5)
[https://imgur.com/Df3CzMV](https://imgur.com/Df3CzMV)[IMG]https://imgur.com/81rb8RS[/IMG]
[https://imgur.com/AWA9agi](https://imgur.com/AWA9agi)[IMG]https://imgur.com/81rb8RS[/IMG]
[https://imgur.com/COfLheg](https://imgur.com/COfLheg)[IMG]https://imgur.com/81rb8RS[/IMG]

testparm output:
[https://imgur.com/iI7re6K](https://imgur.com/iI7re6K)[IMG]https://imgur.com/81rb8RS[/IMG]

My current profiles linked to Samba:
[https://imgur.com/xkNKirs](https://imgur.com/xkNKirs)

Error message on windows:
[https://imgur.com/aDE5tD3](https://imgur.com/aDE5tD3)[IMG]https://imgur.com/81rb8RS[/IMG]

Currently, I've disabled the option to go to the home directory because whenever that was enabled, I wasn't even able to get a single response from the /disks and /disks/pexserver

Note: I know I misspelled pexserver (normally plexserver) but that isn't the issue :).

I'm really out of ideas.

Thanks in advance!

---

### Post by TheFu on 2019-05-18
Which version of Ubuntu are you running?

If not Ubuntu, [https://wiki.samba.org/index.php/Main_Page](https://wiki.samba.org/index.php/Main_Page) is the best place I know for configuration information.
imgur doesn't work for me, so I can't see any of those posts.  Does posting text not work for you?

---

