---
title: "New to Ubuntu, eager to learn and customize. Webapp embedded in Desktop for Carputer?"
date: 2015-03-25
forum: General Help
---

### Post by joew89 on 2015-03-25
Hello Ubuntu Forums, 

I am hoping to use Ubuntu and Unity to create a touchscreen carputer. I think it might be the most simple to embed an instance of chrome with no borders into the Unity desktop (next to the icon bar, using all available desktop space). Then I can create a web application for my needs that will launch at startup. Is this possible? I am not looking for a step by step guide but rather resources to check out to help me develop this and also a reality check if this is a foolish approach. Also, if anyone knows of anything similar, I'd love to hear about it. 

Thank you!

---

### Post by ian-weisser on 2015-03-25
If the webapp handles all your needs, then why keep the icon bar?

---

### Post by joew89 on 2015-03-25
I would like to retain the icon bar so that I can quickly launch different apps, while the web app will provide information and allow me to control an Arduino. Also, I can still have a functioning computer while developing the web app. Maybe eventually I can get rid of the icon bar altogether, this is uncharted territory for me.

---

### Post by ian-weisser on 2015-03-25
I'm not understanding what help you are seeking.

Are you asking how to find the 'Startup Applications' control?
Or are you asking how to change the home page of your web browser?
Or how to start an application maximized?

---

### Post by joew89 on 2015-03-25
I am wondering if it is possible (or advisable) to have a borderless instance of chrome / chromium where the desktop wallpaper would usually be, at startup.

---

### Post by ian-weisser on 2015-03-25
Certainly it's possible.
I'm not quite sure what you mean 'borderless'. I think you mean 'maximized'; the Chrome window occupying the entire desktop space, except for the Shortcut Bar (icon bar)

See [http://www.google.com/support/chrome/](http://www.google.com/support/chrome/) for all the options you can use when starting Chrome, including maximized and custom home page.
See the Startup Applications control panel (use Dash to find it). Put the Chrome command there (with all those options you want).
See the Users and Groups control panel for autologin - how to start a desktop session without requiring login each time.

---

### Post by joew89 on 2015-03-25
Sorry for the vague terminology... I mean to say that chrome would be displaying a single page without a dock/taskbar/tabs, essentially just full screen mode. Seems this is actually quite easy. Thank you for the help! Can I also set x,y coordinates for specific applications when I launch them (or automatically at startup for that matter)? For instance, whenever I open the terminal it would display at the same position and scale? Can I control this across multiple displays?

---

### Post by ian-weisser on 2015-03-25
> **joew89 said:**
> Can I also set x,y coordinates for specific applications when I launch them (or automatically at startup for that matter)? For instance, whenever I open the terminal it would display at the same position and scale? Can I control this across multiple displays?

Generally yes...though there is no standard way, and some applications will ignore your settings and do what they wish. And the feature may well change (it's been pulled before) due to planned codebase convergence over the next year or so. For example, Compiz-based methods will stop working when Unity is soon rewritten without Compiz. I wouldn't invest a lot of energy in the feature at this time.

A couple possible ways to do it. Each application may use several (or none) of these methods:
- Compiz controls the layout: CCSM
- Individual application settings: Edit ~/.config/<application>/<config_file>
- Launch flags: Edit /usr/share/applications/<application>.desktop

---

