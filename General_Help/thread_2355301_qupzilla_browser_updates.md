---
title: "qupzilla browser updates"
date: 2017-03-11
forum: General Help
---

### Post by missmoondog on 2017-03-11
i just installed the qupzilla browser yesterday through synaptic and see that it's an older version then what is currently listed on their website. it was released feb 13th, 2017.

[http://blog.qupzilla.com/2017/02/qupzilla-211-released.html](http://blog.qupzilla.com/2017/02/qupzilla-211-released.html)

i know linux updates for browsers are usually a little behind the windows versions, but it's been almost a month. is this browser still supported on linux and able to get updates through synaptic?

thank you

---

### Post by howefield on 2017-03-11
> **missmoondog said:**
> i just installed the qupzilla browser yesterday through synaptic and see that it's an older version then what is currently listed on their website. it was released feb 13th, 2017.

[http://blog.qupzilla.com/2017/02/qupzilla-211-released.html](http://blog.qupzilla.com/2017/02/qupzilla-211-released.html)

i know linux updates for browsers are usually a little behind the windows versions, but it's been almost a month. is this browser still supported on linux and able to get updates through synaptic?

thank you

Your version of Ubuntu is likely stuck with the version of Qupzilla that was included at time of release and being included in the universe repository means that it is community maintained, so no guarantee of support.

Your best bet for a recent version might be to use a PPA or something like the AppImage package downloadable from the Qupzilla website.

---

### Post by kc1di on 2017-03-11
It may take some time for it to be updated by Ubuntu maintainers but you can add their ppa here: [PPA]("http://blog.qupzilla.com/2011/12/qupzilla-gets-ppa.html")
which may get it to you faster.

---

### Post by missmoondog on 2017-03-12
added the ppa and got updated instantly :)

thank you

edit:
some what of a lie. did get the ppa added but browser wasn't updated to most recent version. still at 1.8.9 and not 2.1.1 :(

---

### Post by vasa1 on 2017-03-12
> **missmoondog said:**
> ... did get the ppa added but browser wasn't updated to most recent version. still at 1.8.9 and not 2.1.1 :(
Yes, you can see the version you'll get over here: [https://launchpad.net/~nowrep/+archive/ubuntu/qupzilla](https://launchpad.net/~nowrep/+archive/ubuntu/qupzilla)```

 qupzilla	1.8.9-1~xenial	David Rosca (2015-11-11)
```

---

### Post by howefield on 2017-03-12
To get the latest you could use the AppImage package.

```
wget https://www.qupzilla.com/uploads/QupZilla-2.1.1.AppImage -P ~/Downloads
```
```
cd ~/Downloads
```
```
chmod a+x QupZilla-2.1.1.AppImage
```
```
./QupZilla-2.1.1.AppImage
```

Once running you can right click the Qupzilla icon in the launcher to make it persist and easy to launch.

---

### Post by missmoondog on 2017-03-13
wow! thanks, but that didn't work, at least not yet. probably should've removed the original qupzilla first as i got some error saying something about profile, etc.

have removed original install and will try this later, otherwise i think i'm just going to stick with playing with palemoon, firefox and opera.

totally appreciate your help and especially typing out the commands to try this again later! :)

---

### Post by vasa1 on 2017-03-13
> **missmoondog said:**
> wow! thanks, but that didn't work, at least not yet. probably should've removed the original qupzilla first as i got some error saying something about profile, etc.

have removed original install and will try this later, otherwise i think i'm just going to stick with playing with palemoon, firefox and opera.

totally appreciate your help and especially typing out the commands to try this again later! :)

When you try again, first rename [FONT=COURIER NEW]*~/.config/qupzilla*[/FONT] to something else. That should let you try out the Qupzilla AppImage cleanly.

---

### Post by howefield on 2017-03-13
> **missmoondog said:**
> wow! thanks, but that didn't work, at least not yet. probably should've removed the original qupzilla first as i got some error saying something about profile, etc.

Should have mentioned that would be best although the AppImage should still load, except you'll get the error..

```
QupZilla: Using profile from QupZilla 1.8.9 is not supported!
```

So either purge the existing Qupzilla with..

```
sudo apt purge qupzilla
```

or alternatively as vasa1 suggested, try renaming the existing Qupzilla profile folder.

---

### Post by missmoondog on 2017-03-13
i emailed the person who maintains the browser and this is the reply i got:

Hi,
it
depends on your distribution. All modern distributions now
ship
with at least QupZilla 2.0.

obviously, lubuntu must be behind the times!

will still give what has been posted here a try when i get back on one of my own machines.

thank you

---

### Post by missmoondog on 2017-03-13
well, after doing some more searching and stuff, i found this info:

[http://blog.qupzilla.com/2016/12/qupzilla-2-on-debian-based-distributions.html](http://blog.qupzilla.com/2016/12/qupzilla-2-on-debian-based-distributions.html)
> 
There are lot of users who ask how to build latest QupZilla on Debian based (Ubuntu, Mint, ...) distributions. Unfortunately, there is no easy solution as QtWebEngine is not available in repositories. Moreover, QtWebEngine is not packaged in any version of Debian, so it won't be available for users anytime soon, if ever...
This is the main reason I dropped my Ubuntu PPA, because there is no easy way to build QupZilla there. Please don't use it anymore, I also removed it from homepage.

EDIT: Looks like QtWebEngine made it into Debian Sid repository just after publishing this blog post. In any case, it will still take at least about a year until it gets into stable Debian/Ubuntu release.

How to get latest QupZilla on Debian
Your only option currently is to build it yourself. For this, you need to use Qt version that comes with QtWebEngine (eg. offical builds or from PPA). After that, just proceed with build instructions as usual.

However, this is far from ideal. Recently, there have been efforts to get QupZilla build and run as a universal Linux package (snap, flatpak), none of them are unfortunately in usable state yet. In any case, I believe this is the solution for the Debian issue (and will be useful for other distributions too), and I hope remaining issues will be sorted out soon.

so, for as little as i know about building packages, or anything nearly that difficult, i'm simply going to say the heck with this browser, although it looked like it had great possibilities.

i REALLY do appreciate the help you folks offered though :)

i will remark this topic as solved for anyone who might come across it and has a little more skills at this than me.

---

### Post by Irihapeti on 2017-03-14
In case anyone is interested, I downloaded the appimage and got it to run. However, there are a couple of major problems, probably related to communication between the appimage and the rest of the system. One has to to with ssl certs. Qupzilla seems to think that a huge number of certificates are not trusted, including some sites that aren't using https! The other is that  iBus doesn't work, so I can't use non-ascii characters.

It would be worth keeping if these two problems could be solved, but not in its current condition.

---

### Post by vasa1 on 2017-03-14
> **Irihapeti said:**
> ... Qupzilla seems to think that a huge number of certificates are not trusted, including some sites that aren't using https! ...
At what point do you see this? I too have the AppImage from howefield's link. Are there some links I could check? My bank's login page and those of a couple of other local utilities open fine. I din't actually log in.

---

### Post by Irihapeti on 2017-03-14
Not all certificates do it. The forums seem to be OK and so is Launchpad.

The error message occurs immediately on going to the page. If I dismiss the messages, they often reappear again later. They give me absolutely no idea as to which tab they are referring to if I have more than one open.

I've got the error from:
[https://www.ubuntu.com/](https://www.ubuntu.com/)
[https://www.canonical.com/](https://www.canonical.com/)
[https://bank.westpac.co.nz/one/app.html#login](https://bank.westpac.co.nz/one/app.html#login)
[http://tohi.toastmastersclubs.org/](http://tohi.toastmastersclubs.org/)
[http://www.toastmasters.org/](http://www.toastmasters.org/)
[https://www.lynda.com/](https://www.lynda.com/)

Firefox and Slimjet have no complaints about any of them.

---

### Post by howefield on 2017-03-14
Not sure if the issue is restricted to the AppImage package : [https://github.com/QupZilla/qupzilla/issues/2217](https://github.com/QupZilla/qupzilla/issues/2217)

---

### Post by Irihapeti on 2017-03-14
Thanks, howefield.

I'll just wait until it gets sorted.

---

### Post by missmoondog on 2017-03-15
fwiw,
i did get qupzilla to open up, but that was as far as i made it as no matter what link i tried to go to, all i got was an error page saying i had no internet connection. internet was working perfectly. :(

---

