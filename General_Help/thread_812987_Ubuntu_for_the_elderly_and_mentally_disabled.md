---
title: "Ubuntu for the elderly and mentally disabled?"
date: 2008-05-30
forum: General Help
---

### Post by wintremute on 2008-05-30
I have been tasked with setting up public internet machines for a group nursing home residents.  The PCs that have been donated are 600mhz P3's with 128mb ram.  After setting one up with XP (and locking it down), I can tell that they will be slooow. So I'm considering an ubuntu environment. Most if not all of the users have never used a computer before, so no windows-to-linux learning curve will be needed.  Edubuntu looks promising, since it's made for kids, but I really need something that they can just run firefox on and play a few preinstalled games. It needs to be as light weight as possible due to the amount of ram. Maybe point me to a tutorial about slimming down and locking down gnome or KDE?

I'm a fully certified windows admin, but I'm still pretty much a noob when it comes to ubuntu. 

Thanks.

---

### Post by ibuclaw on 2008-05-30
For lower hardware spec. You may want to check out [Xubuntu]("http://www.xubuntu.org/") or [Fluxbuntu]("http://fluxbuntu.org/js.html").

It will make better use of the system than what Gnome or KDE will do.

[EDIT]
I almost forgot that there is [OpenGEU]("http://opengeu.intilinux.com/Home.html") too.

All three make nice desktops with Low Hardware requirements.

Regards
Iain

---

### Post by wpshooter on 2008-05-30
I sure hope that you have high speed internet access for these folks !!!

I think I would consider just having the Ubuntu/gnome automatically login to the user account at boot up and then just not give any of the users the user name and password and that way there is probably not going to be very much that they can break.

P. S. - If at all possible you should see if the machines can be bumped up to at least 512 of RAM.  I doubt that you are going to get any thing other than perhaps Xubuntu to run in 128.

Good luck.

---

### Post by wintremute on 2008-05-30
Well, that's the problem.  Since they're donated machines, there's no money for upgrades.  And no offense to the ubuntu community, but if they had 512mb ram I'd run XP on them (just what I know best) :rolleyes:

They're on a 1M cable connection.

---

### Post by wintremute on 2008-05-30
> **tinivole said:**
> For lower hardware spec. You may want to check out [Xubuntu]("http://www.xubuntu.org/") or [Fluxbuntu]("http://fluxbuntu.org/js.html").

It will make better use of the system than what Gnome or KDE will do.

[EDIT]
I almost forgot that there is [OpenGEU]("http://opengeu.intilinux.com/Home.html") too.

All three make nice desktops with Low Hardware requirements.

Regards
Iain
I'll check them out,
Thanks

---

### Post by aquavitae on 2008-05-30
Ubuntu's a great system, but not the most economical on system resources! Maybe have a look at Arch Linux - I think its also really easy and designed for low-end machines. Otherwise xubuntu. Gnome and kde are both relatively resource hungry, and I doubt either will work well on machines with those specs.

But I'd suggest Arch.

---

### Post by aquavitae on 2008-05-30
Just another thought - firefox is also quite slow - there are more efficient options such as swiftfox (I think!) or seamonkey. But most low-end distros (such as arch or xubuntu) should come with a low end browser.

---

### Post by ibuclaw on 2008-05-30
Q&A stuff I've found on the OS'

[OpenGEU:]("http://geubuntu.wikispaces.com/Q+%26+A")
> 
Geubuntu uses E17 and a small part of Xfce, for paneling. That being said the minimum system requirements are the same as Xubuntu.
**128MB RAM** to run, or **192MB RAM** to install. Desktop install requires **at least 1.5GB of free space** on your hard disk. But has been known to run on less


[Xubuntu:]("http://www.xubuntu.org/get")
> 
To run the Desktop CD (LiveCD + Install CD), you need **128MB RAM** to run or **192MB RAM** to install. The Alternate Install CD only requires you to have **64MB RAM**.

To install Xubuntu, you need **1.5 GB of free space** on your hard disk.

Once installed, Xubuntu can run with **192MB RAM**, but it is strongly recommended to have at least **256MB RAM**.


[Fluxbuntu:]("http://wiki.fluxbuntu.org/index.php?title=FAQ")
> 
Fluxbuntu uses **35-46MB RAM**. If you have **64MB RAM** we would definitely recommend having adequate swap space


Hope that gives you a general idea of what is needed from them.
Although being an old Peoples home, I would definately be after the one that gives the most "appealing looks" on the hardware given.

Regards
Iain

[EDIT]
> **aquavitae said:**
> Just another thought - firefox is also quite slow - there are more efficient options such as swiftfox (I think!) or seamonkey. But most low-end distros (such as arch or xubuntu) should come with a low end browser.
I'd go for Iceweasel, but that's just me...

---

### Post by dagnabit dang doohickey on 2008-05-30
I'd say the bigger issue is the PIII, not the RAM. Windows XP can run on 128MB quite well for most basic tasks. To increase performance, try disabling as many unnecessary services as possible. You would need a highly stripped down and customized version of Ubuntu to offer noticeably more zip than XP on your PIII machines, let alone any noticeable improvement on web browsing.

Another consideration is your users experience. If your users will mostly be using a web browser, Windows will offer a more satisfying experience. Probably more satisfying for you, the admin, as well.

I opt for Linux over Windows for as many tasks as reasonably possibly. But, this wouldn't be one of them.

---

### Post by Zorael on 2008-05-30
As for performance:
[indent]I find *ubuntu to be fast enough if you just disable services you don't need and pick a low-end desktop environment. I like Xfce (Xubuntu) but it's hardly the lightest around. It's a good compromise, though.

The underlying X.org will still be the same, so you just need to focus on environment and applications. Stress on applications. If you use KDE (Qt) apps in Gnome, it must load the Qt libraries (which were thitherto not used, since Gnome's stuff is GTK-based), meaning extra memory overhead.

Replacing Firefox with [Swiftweasel](http://swiftweasel.tuxfamily.org/) might be a good idea, if not to use another browser altogether. Opera, Epiphany, Konqueror (Gnome/KDE), etc.[/indent]

As for accessibility:
[indent]There's a chance that most/the best accessibility applications and features exist only in Gnome/KDE, though now I'm only guessing. Brightness, contrast, font size, font DPI, resolution; all of this should be alterable regardless of environment.[/indent]

---

### Post by snowpine on 2008-06-19
> **wintremute said:**
> I have been tasked with setting up public internet machines for a group nursing home residents.  The PCs that have been donated are 600mhz P3's with 128mb ram.  After setting one up with XP (and locking it down), I can tell that they will be slooow. So I'm considering an ubuntu environment. Most if not all of the users have never used a computer before, so no windows-to-linux learning curve will be needed.  Edubuntu looks promising, since it's made for kids, but I really need something that they can just run firefox on and play a few preinstalled games. It needs to be as light weight as possible due to the amount of ram. Maybe point me to a tutorial about slimming down and locking down gnome or KDE?

I'm a fully certified windows admin, but I'm still pretty much a noob when it comes to ubuntu. 

Thanks.

I would try Xubuntu first if I were you, see if it will work for you. It is the heaviest of the "lightweight" options but also the most functional and user-friendly. I have never tried it on 128mb but I have on 256 and it worked fine. 

I like a lot of things about Fluxbuntu, but it can be kind of infuriating sometimes, definitely not user-friendly for your target audience. Unless you were willing to spend some time to set it up as a "kiosk" with just a few desktop launcher icons in Rox, then it could be perfect. Its default theme is colorful and might be very calming for your users.

Good luck, this is an interesting thread!

---

### Post by avtolle on 2008-06-19
Late to this most interesting thread. [http://ubuntuforums.org/showthread.php?t=707688&highlight=To%3AUbuntu+Public+Library](http://ubuntuforums.org/showthread.php?t=707688&highlight=To%3AUbuntu+Public+Library) is not strictly "on point", but it does provide some suggestions about locking down the computers so users cannot foul things up inadvertently. HTH, and good luck with the project.

---

