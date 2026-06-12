---
title: "Flash not detected on certain sites"
date: 2006-11-03
forum: General Help
---

### Post by nim278 on 2006-11-03
I recently clean-installed Edgy, but I have had this problem since I first installed Breezy. Certain pages that use Flash complain that I don't have it and need to install it, while other sites display the content no problem.

Example of a site: [http://arborsports.com](http://arborsports.com)

I am using Macromedia Flash Player 7 (auto-installed within Firefox when I first when to a Flash site)

Any thoughts or workarounds?

Maciej

---

### Post by bettlebrox on 2006-11-03
Looks like the site requires Flash 8. Look at the source of the page there is this:

// Globals
**// Major version of Flash required**
**var requiredMajorVersion = 8;**
// Minor version of Flash required
var requiredMinorVersion = 0;
// Revision of Flash required
var requiredRevision = 0;
// the version of javascript supported
var jsVersion = 1.0;

U could try the Beta version of Flash 9 that is available for Linux. There should be a few HOWTO's on how to install it in the forums.

---

### Post by nim278 on 2006-11-03
Works perfectly. Thanks!

---

