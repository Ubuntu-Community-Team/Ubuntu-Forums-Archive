---
title: "Systemwide Installation of Firefox Plugins?"
date: 2007-11-17
forum: General Help
---

### Post by Master One on 2007-11-17
Is it possible, to install certain firefox add-ons (like Adblock Plus and FoxyProxy) systemwide, so that they are available by default for newly added users?

If I try to add an add-on through Firefox, it installs it in the users homedir under /home/USER/.mozilla/firefox/, which means, if you have a bunch of users (or even more, think of an Edubuntu LTSP server, which is what I am actually setting up), every user has to download his copy of the add-on individually, and it is pretty redundant to have it installed in every users homedir.

It would be best, if a add-on could not only be installed systemwide, but also preconfigured, so that when I add a new user to the system, he already has that add-on configured and activated right from the first start of Firefox. Can this be done somehow?

---

### Post by llamakc on 2007-11-17
Yes.

Put them in 

```

/usr/lib/firefox/plugins/

```

---

### Post by Master One on 2007-11-17
Just discovered, that I made a mistake, by writing "plugins" instead of "addons". The mentioned addons (Adblock Plus and FoxyProxy) are Firefox Extensions, not plugins.

As seen, plugins like Flashplayer or Mplayer-Plugin get automatically installed systemwide. But how is it with addons like Extensions?

The Adblock Plus addon is an .xpi file, and if you try to install it through Firefox, it gets installed automatically in the users homedir, and there doesn't seem to be a possibilty, to choose systemwide installation instead, although there are some systemwide shared extension folders.

I am a little confused concerning this issue. If there is no other way, is it possible to install such an extension through Firefox into the users homedir, and then copy or move it over to a systemwide extension dir (which would that be?)?

---

### Post by ghat on 2008-02-19
hi

I also am interested in knowing how to deploy  Firefox/Thunderbird themes and add-ons(aka extensions) on a system-wide basis. 

G

---

