---
title: "Why can't I install this? Please help."
date: 2008-06-25
forum: General Help
---

### Post by skoalman88 on 2008-06-25
I'm trying to install Ubuntu SE, but I can't install the satanic-gnome-themes because I get this message:

satanic-gnome-themes:
 Depends: gtk2-engines-aurora but it is not going to be installed

Why is it not being installed?

I'm running fesity

---

### Post by mcduck on 2008-06-25
> **skoalman88 said:**
> I'm trying to install Ubuntu SE, but I can't install the satanic-gnome-themes because I get this message:

satanic-gnome-themes:
 Depends: gtk2-engines-aurora but it is not going to be installed

Why is it not being installed?

I'm running fesity

Probably because it's not in the repositories.. ;)

You should be able to find a package from gnome-look.org.

---

### Post by angry_johnnie on 2008-06-25
The aurora engine is available in the repos, actually.  You can't install it because it has some dependency issues.  It happens all the time. :-(  It seems Ubuntu SE is only available for the latest version (at least the themes are).

So, what you could do instead, is use another gtk theme, and customize it.  Use a different controls theme, different colors and icons (at least you can install the Sanguine icon theme), so that it *sort-of* looks like SE.

You can install everything else, though.

That is, the usplash themes, wallpapers, icons, and sounds.

---

### Post by skoalman88 on 2008-06-25
Thanks for the help

---

### Post by mcduck on 2008-06-25
> **angry_johnnie said:**
> The aurora engine is available in the repos, actually.

Is it? At least the search in packages.ubuntu.com doesn't find it in any of repositories fror any of available Ubuntu versions..

I even tested by searching for _all_ gtk engines available from repositories, and it still isn't there..

Are you sure you haven't added some extra repository that contains the Aurora engine?

(edit: also, dependency issues should _not_ happen "all the time". Actually they should never happen as long as you are only using official repositories)

---

### Post by angry_johnnie on 2008-06-26
> **mcduck said:**
> Is it? At least the search in packages.ubuntu.com doesn't find it in any of repositories fror any of available Ubuntu versions..

:-) Well, this is, in fact, an extra repository:  The Ubuntu SE repository.  What I meant when I said it happens 'all the time' was that every time I have tried installing SE on older versions of Ubuntu I get the same error about the aurora engine not going to be installed.  Only with the latest version --whether it's Feisty or Gutsy or Hardy-- will it work without problems.  Even if I select only the aurora engine, I get an error, concerning dependencies.

Of course this should _not_  happen "all the time" with official repos, but then, these aren't official repos.  They're SE repos. :-)

Hope that cleared things out a little.

---

### Post by parker13 on 2008-06-30
The Aurora engine which is in the Ubuntu SE repo only works for Gutsy and Hardy (and Intrepid, I assume). I don't think that even the source available on Gnome-look will work on earlier versions due to library dependencies.

---

