---
title: "A linux OS what takes very little ram?"
date: 2014-09-09
forum: General Help
---

### Post by dafuqmanlolz on 2014-09-09
Hi I've been on ubuntu but sadly I can't use it to stream on runescape because of the ram take.. ( I got low PC) 

Is there any other Disto what takes very little ram and isn't ubuntu? Cause Ubuntu has wi-fi problems with my.

---

### Post by cogier2 on 2014-09-09
Why not try Lubuntu, that uses less RAM that Ubuntu.

If you want more help I suggest you post the make and model of your computer, the amount of RAM you have and which version of Ubuntu you are using.

---

### Post by dafuqmanlolz on 2014-09-09
I got  
intel core 2 CPU  166ghz
2.5 ram
intel gma 950 252 MB video card.

The problem is when I started using ubuntu too i had wireless problems the only way to fix it was to use internet, but now i got no cable so I'm scared on lubuntu after install no internet too :(

---

### Post by sudodus on 2014-09-09
Please specify your computer (not only RAM)

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

It will make it much easier to give relevant advice.

For a starter, please see the following links
[URL="http://ubuntuforums.org/showthread.php?t=2130640"]
Old hardware brought back to life[/URL]

[http://Light Linux Distributions - Hardware Testing (RAM)](http://Light Linux Distributions - Hardware Testing (RAM))

---

### Post by stalkingwolf on 2014-09-09
i run mint 13 quite happily on 1gb of ram.  The wireless issue is not an issue with buntu it is a driver issue with the manufacturer of the wireless card.

---

### Post by sudodus on 2014-09-09
For that computer I would suggest that you try Xubuntu 14.04 LTS and if it is not fast enough for your particular applications, try Lubuntu 14.04 LTS.

 			 			[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

---

### Post by dafuqmanlolz on 2014-09-09
Yea but what do I do with the wireless? After I install ubuntu no wireless?

---

### Post by uRock on 2014-09-09
Can you run the following command in a terminal, then copy/paste the output here?```
lspci
``` This will tell us what chipset your wireless NIC is using.

The lightest and most responsive distro I have used thus far is ElementaryOS. [http://elementaryos.org/](http://elementaryos.org/)

---

### Post by Dragonbite on 2014-09-09
If you Google "desktop environment memory usage" you can get some information on which desktops are "lighter" which is really waht you are looking at, as distribution may pose less of an issue except with ensuring driver compatibility.

[Memory consumption of Linux desktop environments]("https://flexion.org/posts/2014-03-memory-consumption-of-linux-desktop-environments.html")```

| Desktop Environment  | Memory Used |
| ---------------------|------------:|
| Enlightenment 0.18.8 |    83.8 MiB |
| LXDE 0.5.5           |    87.0 MiB |
| XFCE 4.10.2          |   110.0 MiB |
| LXQt 0.7.0           |   113.0 MiB |
| MATE 1.8.1           |   123.0 MiB |
| Cinnamon 2.2.13      |   176.3 MiB |
| GNOME3 3.12.2        |   245.3 MiB |
| KDE 4.13.1           |   302.6 MiB |
| Unity 7.2.0.14       |   312.5 MiB |
```

[A Memory Comparison of Light Linux Desktops – Part 3]("http://l3net.wordpress.com/2014/02/15/a-memory-comparison-of-light-linux-desktops-part-3/")
[ATTACH=CONFIG]256300[/ATTACH]

And of course there are more... but you get the idea ;)

For me, I have a netbook (1.2GHz, 1.7GB Ram or something like that) and started off with Ubuntu... then went to Fedora when I thought the fan was not turning off... then I switched to Xubuntu for Ubuntu's hardware support and Xfce's light weight.  That's where I am currently at.

I also find KDE working surprisingly well on older systems, despite being one of the heavier desktop environments.

---

