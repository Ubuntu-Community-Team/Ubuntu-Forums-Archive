---
title: "Aptitude and apt-get, (--)purge vs remove"
date: 2008-05-11
forum: General Help
---

### Post by Zorael on 2008-05-11
So I've been lurking around on some of these forum sections and hopefully helping some people (when I'm not hosing their systems with nub advice); mainly those who upgraded for whom programs no longer work since older versions left remnants in their systems. Remnants which are only removed if you let Synaptic "**completely remove**" or Adept/aptitude/apt-get "**purge**" the program packages. I'm at a point where I don't use Synaptic or Adept beyond searching for packages (since [FONT="Courier New"]apt-cache search[/FONT] output is hard to parse by eye), sticking instead to [FONT="Courier New"]aptitude purge[/FONT] for removal.

What I'm trying to say is that purging then reinstalling "almost always"/"often" fixes application-related issues, which makes me wonder; when should I ever use remove instead? When do I want these "remnants" (at a lack of better word for them) to remain?

Inquiring minds want to know.

---

### Post by sdennie on 2008-05-11
Remove just removes the binaries whereas purge also removes config files.  It seems logical that purge and then re-install would fix problems if those problems were initially caused by config files because upon re-install you'd have clean configs again.  I think remove is generally preferable because, possibly user edited configs just sit there idle and, if you re-install the package at a later time (assuming it wasn't broken), you haven't lost any user edited content.

---

### Post by Zorael on 2008-05-11
While I guess most user-edited configurations are user-specific, and as such, kept in your /home directory, I see your point.

So merely removing leaves .confs and /etc/directory entries, or what forms of configuration are we talking about?

---

