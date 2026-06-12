---
title: "Electric sheep in 14.04"
date: 2014-05-09
forum: General Help
---

### Post by asigurnjak on 2014-05-09
Did anyone get electric sheep to work in Ubuntu Unity 14.04 ?
If you did , please share. I have tried everything i can , google it   follow bur reports , but no fix so far . 
I really  like it and miss it .

---

### Post by grier-devon on 2014-05-10
Maybe a list of the guides you have tried would help as we don't know what you have tried and everyday more guides are posted. Here is one have you tried this one.

[http://www.distrogeeks.com/install-latest-electricsheep-ubuntu/](http://www.distrogeeks.com/install-latest-electricsheep-ubuntu/)

---

### Post by monkeybrain20122 on 2014-05-10
[https://bugs.launchpad.net/ubuntu/+source/electricsheep/+bug/1266187](https://bugs.launchpad.net/ubuntu/+source/electricsheep/+bug/1266187)

---

### Post by asigurnjak on 2014-05-10
Well , thanks folks . So due to a bug  evn if i do compile it myself it wont work . 
I also found tread on Electricsheep websitee , where compiling with custom settings and flags does not work yet. 
Thank you folks , i guess i will just have wait little more .

---

### Post by dkz666 on 2014-08-30
UPDATE: 

On a fresh install of Ubuntu 14.04 (w/Unity) the following packages were required (w/links)

(WARNING: know your architecture or you'll break your packages(can be found within : ```
uname -a
``` ) )

libavutil51 - [i386 ]("http://pkgs.org/ubuntu-12.04/ubuntu-updates-main-i386/libavutil51_0.8.16-0ubuntu0.12.04.1_i386.deb.html")or [amd64]("http://pkgs.org/ubuntu-12.04/ubuntu-updates-main-amd64/libavutil51_0.8.16-0ubuntu0.12.04.1_amd64.deb.html")
libavformat53 - [i386]("http://pkgs.org/ubuntu-12.04/ubuntu-updates-main-i386/libavformat53_0.8.16-0ubuntu0.12.04.1_i386.deb.html") or [amd64]("http://pkgs.org/ubuntu-12.04/ubuntu-updates-main-amd64/libavformat53_0.8.16-0ubuntu0.12.04.1_amd64.deb.html")
libavcodec53 - [i386]("http://pkgs.org/ubuntu-12.04/ubuntu-updates-main-i386/libavcodec53_0.8.16-0ubuntu0.12.04.1_i386.deb.html") or [amd64]("http://pkgs.org/ubuntu-12.04/ubuntu-updates-main-amd64/libavcodec53_0.8.16-0ubuntu0.12.04.1_amd64.deb.html")
electricsheep - [i386 ]("http://pkgs.org/ubuntu-12.04/ubuntu-universe-i386/electricsheep_2.7%7Eb12+svn20091224-1ubuntu3_i386.deb.html")or [URL="http://pkgs.org/ubuntu-12.04/ubuntu-universe-amd64/electricsheep_2.7%7Eb12+svn20091224-1ubuntu3_amd64.deb.html"]amd64
[/URL]
I recommend using gdebi, availible through the normal software channels.

The result is a functioning version of the program (can be launched via command line, or a desktop entry can be made (see below)). It still doesn't have the full functionality available for windows, mac, or android versions (though I haven't tested the latter). Nothing broke my packages when the architecture was taken into account. I did run updates during the install of these .debs with --fix-missing and -f install.

I am looking into how to package these all together. If anyone knows how to package .deb's together, please let me know, and I'll put out the complete package asap. When I am not in the middlelof school. I will look at getting full functioning going.

-------------------------------------------------------------------------------------------------------------------

Hello All,

I figured there would be some interest in this. I have managed to compile by using an older version of the package : [https://launchpad.net/ubuntu/+source/electricsheep](https://launchpad.net/ubuntu/+source/electricsheep) (you will have to find the package for your architecture).

Download the .deb. After that, use a package installer (I really suggest [gdebi]("https://apps.ubuntu.com/cat/applications/precise/gdebi/") ).

It **will** kick back errors. You're going to have to hunt out those packages which it requires.

Most should be availible through the repositories. Some, such as libav...52 and 53 are no longer shipped.

There happens to be this awesome package archiving website I just found (I'd save this one to bookmarks) : [URL="http://pkgs.org/"]pkgs.org 
[/URL]
By recursively looking at what packages are required by electricsheep, those required by those, etc... you can get it up and running in about 15 minutes.

I have spent *hours* before trying to get electricsheep to work. This is a flawless method. One the installation goes off, find a good logo, [make a desktop entry]("https://developer.gnome.org/integration-guide/stable/desktop-files.html.en") for electricsheep and electricsheep-preferences, and enjoy the fractaline beauty (I also suggest enabling a fullscreen keyboard shortcut so that you can enjoy mplayer in full).

Just as a breif poll: Anyone interested in getting the electricsheep repository back on-line? Or would appreciate it if it was? I don't think there is too much more that would need to be packaged along to get it running in 14.04/10. 

Also, I have been toying around with gnome integration, again, if anyone is interested.

---

### Post by mkoelemay on 2014-09-09
Would LOVE for electric sheep to be back in the repositories!

---

### Post by franny23dmt on 2014-10-01
ive managed to successfully compile ES for both my Desktop 14.04   and my girlfriends EFI Samsung laptop.
By using aptitude to downgrade packages that its dependent on    (done on 64 bit machines despite the i386 thing)

[https://launchpad.net/ubuntu/saucy/i386/curl](https://launchpad.net/ubuntu/saucy/i386/curl)
[https://launchpad.net/ubuntu/saucy/i386/debconf](https://launchpad.net/ubuntu/saucy/i386/debconf)
[https://launchpad.net/ubuntu/saucy/i386/gconf2](https://launchpad.net/ubuntu/saucy/i386/gconf2)
[https://translations.launchpad.net/ubuntu/saucy](https://translations.launchpad.net/ubuntu/saucy)
[https://launchpad.net/ubuntu/saucy/i386/libavcodec53](https://launchpad.net/ubuntu/saucy/i386/libavcodec53)
[https://launchpad.net/ubuntu/saucy/i386/libavformat53](https://launchpad.net/ubuntu/saucy/i386/libavformat53)
[https://launchpad.net/ubuntu/saucy/i386/libc6](https://launchpad.net/ubuntu/saucy/i386/libc6)
[https://launchpad.net/ubuntu/saucy/i386/libexpat1](https://launchpad.net/ubuntu/saucy/i386/libexpat1)
[https://launchpad.net/ubuntu/saucy/i386/libglade2-0](https://launchpad.net/ubuntu/saucy/i386/libglade2-0)
[https://launchpad.net/ubuntu/saucy/i386/libgtk2.0-0](https://launchpad.net/ubuntu/saucy/i386/libgtk2.0-0)
[https://launchpad.net/ubuntu/saucy/i386/libjpeg-progs](https://launchpad.net/ubuntu/saucy/i386/libjpeg-progs)
[https://launchpad.net/ubuntu/saucy/i386/xloadimage](https://launchpad.net/ubuntu/saucy/i386/xloadimage)

Autoreconf was important but rest is as per distrogeeks.
.

Then i re-installed Ubuntu to all new again,  and the same  "make" compiled code worked for sudu make install....    Viola.
.
i am wondering if i upload this compiled "make"    that other may be able to use it

---

