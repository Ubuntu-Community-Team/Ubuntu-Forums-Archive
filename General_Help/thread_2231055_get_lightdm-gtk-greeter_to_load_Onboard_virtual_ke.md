---
title: "get lightdm-gtk-greeter to load Onboard virtual keyboard?"
date: 2014-06-23
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2014-06-23
Has anyone been able to get Onboard to work with lightdm-gtk-greeter so it can be used to log in? This bug report:
[https://bugs.launchpad.net/lightdm-gtk-greeter/+bug/905809](https://bugs.launchpad.net/lightdm-gtk-greeter/+bug/905809)
sounds like they got it working about a year ago but I'm having no luck.

I know the unity greeter can be made to work but I'm not at all enthused about switching to that. It demands an INSANELY long list of dependencies including all sorts of stuff that I can't imagine why a login greeter should find necessary - gstreamer and bluetooth stuff for example.

---

### Post by Dreamer Fithp Apprentice on 2014-06-24
Solved:
In case some future reader wants to know:
lightdm-gtk-greeter doesn't put the vkb on the login screen the way some greeters do. It puts it in an accesibility menu. The line "keyboard=onboard" (or whatever vkb you want) puts onboard on that menu, but you also have to make the button for the menu show. What menu buttons are shown is specified by a line beginning "indicators=" and in addition to strings for whatever other menu buttons you want, you have to include "~a11y;". Note, I believe those middle characters are numeral ones, not letter els. So the whole line might look like:
indicators=~language;~a11y;~session;~power;
for instance.

All credit and my great appreciation to Sean Davis whose response to my inquiry at the launchpad link above is the source of my enlightenment.

---

