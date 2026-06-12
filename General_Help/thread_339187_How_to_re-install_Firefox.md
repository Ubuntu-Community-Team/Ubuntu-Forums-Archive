---
title: "How to re-install Firefox?"
date: 2007-01-15
forum: General Help
---

### Post by chapterthree on 2007-01-15
Hi All,

On my fairly fresh install of 6.10, Firefox 2.0.0.1 seems to be crashing when I access certain websites.  I am able to reliabily reproduce the issue, meaning Firefox will crash every time I go to these certain websites.

I would like to try to 'uninstall' and reinstall Firefox to see if that helps.  But if I try to uninstall Firefox, it wants to uninstall a bunch of other stuff, some of which looks pretty important:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ekiga ubuntu-desktop firefox firefox-gnome-support gnome-app-install yelp
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  ekiga* firefox* firefox-gnome-support* gnome-app-install* ubuntu-desktop*
  yelp*
0 upgraded, 0 newly installed, 6 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 46.8MB disk space will be freed.
```

Any idea how I can uninstall and re-install Firefox without having to remove what looks like critical stuff?

---

### Post by hikaricore on 2007-01-15
you should probably move or remove your config folder in your home directory first:

```

cd ~
mv .mozilla .mozilla-backup

```

then simply run:

```

sudo aptitude reinstall firefox
```

Hope this helps ya out,

--Aaron

---

### Post by NeoLithium on 2007-01-15
check through [http://www.ubuntuguide.org](http://www.ubuntuguide.org) as well, with their firefox plugin sections; there's a few snippets in there about fixing the crashing.

---

### Post by hikaricore on 2007-01-15
just so you know, your old bookmarks will now be located at:
**~/.mozilla/firefox/_random_.default/bookmarks.html**

^^ Pleas note that random is a randomly generated directory name followed by .default :)

Just incase you need it, didn't want you to lose your bookmarks.

---

### Post by chapterthree on 2007-01-15
> **hikaricore said:**
> you should probably move or remove your config folder in your home directory first:

```

cd ~
mv .mozilla .mozilla-backup

```

then simply run:

```

sudo aptitude reinstall firefox
```

Hope this helps ya out,

--Aaron

This worked perfectly and it actually resolved my crashing issue.  Thanks!

---

### Post by hikaricore on 2007-01-15
> **chapterthree said:**
> This worked perfectly and it actually resolved my crashing issue.  Thanks!

Not a problem :)

However one other thing you should know, that method probably also removed flash, which may have been why you were crashing in the first place.  If you need flash check around the forums for resolutions to the firefox & flash crashing bug.  Otherwise enjoy.

---

### Post by chapterthree on 2007-01-15
> **hikaricore said:**
> Not a problem :)

However one other thing you should know, that method probably also removed flash, which may have been why you were crashing in the first place.  If you need flash check around the forums for resolutions to the firefox & flash crashing bug.  Otherwise enjoy.

Yes, you are correct.  I found that out shortly after I visited a site that had me install the Flash plugin. :)  I did find the solution to the issue was posted at UbuntuGuide.org as NeoLithium had hinted to.

---

