---
title: "Swiftfox - jre 6 isn't working."
date: 2007-03-09
forum: General Help
---

### Post by old_geekster on 2007-03-09
I have Firefox 2.0.0.2 and Swiftfox 2.0.0.2 installed on my rig.

There is a website that I frequent that requires "JRE" to run a video.  I have JRE 6 installed and the video works great with FF, however, when I go to the website in SF the video will not play.  A message tells me that I require "JRE" to continue.

I have checked in "about:config" in both browsers and the java section is identical.

I would appreciate your suggestions on how to solve this dilema.:confused:

---

### Post by kerry_s on 2007-03-09
You need to check " about: plugins " not about:config.
You probably need to copy the plugins since swiftfox installs somewhere else.

 ```
about:plugins
```

---

### Post by old_geekster on 2007-03-12
Thanks Kerry,

I did exactly what you suggested.  There are two plugins shown in Swiftfox and about seven in FF.  I guess I have to determine which I need and figure out how to install them.

I am still a bit shaky on installing anything, if I can't simply copy and paste.  This will be a great learning experience.

---

### Post by kerry_s on 2007-03-12
It is just copy and paste, just copy and paste the plugins from /usr/lib/ firefox to where ever you have swiftfox installed. You can find the swiftfox location->

in terminal:
sudo updatedb
locate swiftfox


Your going to need root privileges->

gksu nautilus /

---

### Post by old_geekster on 2007-03-12
Well, problem solved!

Here is the post that helped me:

[B]"Originally Posted by taurus  View Post
See if the new java plugins is in /usr/lib/firefox/plugins. If it is, then just copy it over to /opt/swiftfox/plugins."
[/B]
Thanks to all, especially taurus.

---

