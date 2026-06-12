---
title: "Firefox 3 b5 Scrolling is very slow on some sites"
date: 2008-05-02
forum: General Help
---

### Post by musther on 2008-05-02
Using some sites in Firefox 3 beta 5 (in Hardy), the scrolling is very jumpy.  Notably when scrolling up and down gmail mail lists or conversations.  Everything is fine on most other sites.

Yes, I have smoothscrolling on, but as I said, it's fine on most sites, and even which smoothscrolling off, there's a notable lag between scrolling with the mouse wheel, and seeing the effect.  Again, with smoothscrolling off, it's only an issue on certain sites, most notably gmail.  It feels exactly like I'm using a very slow computer (which I'm not), but only on certain pages.

So, is this just a bug in FF3b5 that will be fixed, or is it something else, is there anything I can do now?

Cheers

---

### Post by Serpentinsek on 2008-05-02
I have the same problem over here:
[http://ubuntuforums.org/showthread.php?t=779111&highlight=slow+scrolling](http://ubuntuforums.org/showthread.php?t=779111&highlight=slow+scrolling)

Hope you find something useful

---

### Post by musther on 2008-05-02
To be honest, I don't think this is the same problem, yours is a general one, while mine is something going on with firefox.  They could be related, but I really don't think they're the same.

---

### Post by Endolith on 2008-05-11
> **musther said:**
> Using some sites in Firefox 3 beta 5 (in Hardy), the scrolling is very jumpy.  Notably when scrolling up and down gmail mail lists or conversations.  Everything is fine on most other sites.

Yes, I have smoothscrolling on, but as I said, it's fine on most sites, and even which smoothscrolling off, there's a notable lag between scrolling with the mouse wheel, and seeing the effect.  Again, with smoothscrolling off, it's only an issue on certain sites, most notably gmail.  It feels exactly like I'm using a very slow computer (which I'm not), but only on certain pages.

So, is this just a bug in FF3b5 that will be fixed, or is it something else, is there anything I can do now?

Cheers


I have exactly the same problem.  I can't believe this would be considered acceptable for release.

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/217580](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/217580)

---

### Post by Endolith on 2008-05-12
Does this workaround work for Gmail?

1. Install the Stylish Add-on ([https://addons.mozilla.org/en-US/firefox/addon/2108](https://addons.mozilla.org/en-US/firefox/addon/2108))
2. Right click the icon --> Write style --> For google.com
3. Add "*{border-style: none !important;}"

---

