---
title: "Firefox ignores image names.  &quot;url.ext&quot;"
date: 2013-07-11
forum: General Help
---

### Post by Adam_GUI on 2013-07-11
I've done some rudimentary Google-fu and found examples of this as far back as 2009, but no answers.

I'm on Xubuntu12.04.

Firefox version 22.0.
Add-ons - Adblock Plus.
User Agent Switcher.

Behavior:
When saving an image from a Google search to save an image, the image name is ignored and replaced with "url".
This happens most consistently with jpegs.  Though, sometimes pngs are affected.  
I haven't tested other image types, as this recently started happening this evening.

So, in doing a Google Search for The Old Pepsi Logo, I get [http://www.findthatlogo.com/wp-content/gallery/pepsi-logos/old-pepsi-logo.jpg]("http://www.findthatlogo.com/wp-content/gallery/pepsi-logos/old-pepsi-logo.jpg").

When I right-click and save as on the image, Firefox offers to save "url.jpeg" instead of "old-pepsi-logo.jpg".

Is this a semi-recurring bug that I can reset by changing the default user profile?
Old info said that surfing in "Safe" or "Private Mode" would keeps this from happening.  It does not.

The only "help" solution generally offered was to use a different browser.

---

### Post by Adam_GUI on 2013-07-11
So, I reset my default profile and Firefox is no longer acting erratically.
For future Google-Fu reference, if your Firefox is replacing image names with "url.ext", your first course of action should be to reset your default user profile.

Current method:  Help > Troubleshooting Information > Reset Firefox.

---

