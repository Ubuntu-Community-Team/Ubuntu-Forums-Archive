---
title: "Creating a custom Ubuntu installation"
date: 2008-04-08
forum: General Help
---

### Post by Ozor Mox on 2008-04-08
I was thinking it would be a nice idea to install Ubuntu on one of my computers and set it up exactly how I want it, instead of installing it with its standard GNOME desktop and applications and things, so I can make it run faster and try other desktop environments etc. Originally I was thinking I'd need to use something like Debian for this, but I've been reading about Ubuntu Server and the alternate install CD and wondering if they might do the job.

Anyone tried this sort of thing with Ubuntu? I would use Debian, or even something more difficult like Slackware or FreeBSD, but it would be nice to build using a familiar distribution that I know and love.

Cheers.

---

### Post by Ozor Mox on 2008-04-08
Ok I've been investigating this a bit more and I've found basically 4 options for a customised installation. Does anyone know what the main differences between these are, or suggest any as being more suitable?

1. Ubuntu Server Edition.
2. Ubuntu alternate install CD.
3. Minimal CD found [here](https://help.ubuntu.com/community/Installation/MinimalCD).
4. Debian net install.

---

### Post by atomkarinca on 2008-04-08
Ubuntu has a net install, too. You can find it [here]("https://help.ubuntu.com/community/Installation/Netboot").

---

### Post by Ozor Mox on 2008-04-08
> **atomkarinca said:**
> Ubuntu has a net install, too. You can find it [here]("https://help.ubuntu.com/community/Installation/Netboot").

Thanks for the link, I think that is different to the net install Debian has though. I have a bootable CD-ROM drive, I'd just like to install packages myself. That page gives a link to the minimal CD for Ubuntu that I linked to, which seems to be the equivalent of Debian's net install.

[These](https://help.ubuntu.com/community/Installation/MinimalCD) are official right?

---

### Post by atomkarinca on 2008-04-08
Yes they are official. I suggest minimal install, though. And you should know what you're doing once you start the minimal install, because you won't get a GUI at first.

---

### Post by Ozor Mox on 2008-04-08
> **atomkarinca said:**
> Yes they are official. I suggest minimal install, though. And you should know what you're doing once you start the minimal install, because you won't get a GUI at first.

Thanks! I know that I will get command line only. This is purely experimental and I fully expect to break it several times! :)

---

### Post by FakeOutdoorsman on 2008-04-08
I always do a custom Ubuntu install with the alternate disc and it works great.  Choose to the "command-line" option and you can build up from there.  This is a good start:
[Installation / Low Memory Systems]("https://help.ubuntu.com/community/Installation/LowMemorySystems") [Ubuntu Wiki]

Also:
[K.Mandla's Software Page]("http://kmandla.wordpress.com/software/") (offers suggestions suited for an efficient, fast, and lightweight system).
[Howto: Set up Gutsy for speed, v1.2]("http://kmandla.wordpress.com/2007/10/20/howto-set-up-gutsy-for-speed/")
[Feisty Openbox on 1Ghz Pentium III, start to finish]("http://kmandla.wordpress.com/2007/04/01/feisty-openbox-on-1ghz-pentium-iii-start-to-finish/")

Also, you might like Arch Linux.  I recommend taking a look at that too.

---

### Post by Ozor Mox on 2008-04-08
> I always do a custom Ubuntu install with the alternate disc and it works great. Choose to the "command-line" option and you can build up from there.

This is what I've been trying out and it works great, Only one thing though, which I presume is a side effect of the customised packages in Ubuntu's repositories. When I install GDM, I get the error:

> Error loading Human theme. Can't open file /usr/share/gdm/themes/Human/ Human.xml

I have solved this with apt-get install ubuntu-artwork, but is there any way to remove this dependency and have GDM load its default background or something?

---

