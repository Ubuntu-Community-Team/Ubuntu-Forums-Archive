---
title: "Help with new Volume Control in 14.04"
date: 2014-12-29
forum: General Help
---

### Post by leegold on 2014-12-29
Hi,

Using 14.04 for first time. Something the volume control in the indicator panel area  is confusing me. When I click the control I get the volume control but I also get this strange looking control which cites other media packages that are installed. For example I'm watching a movie/vid with Parole and I click the volume and along with the volume control I see an unintuitive (for me at least)  control for Audacious (a music player).  What is the purpose of this? Can I disable this action and only get a volume control, which is all I want?

Thanks

---

### Post by deadflowr on 2014-12-29
In a perfect world you would add the media players to the blacklist option in dconf editor (needs to be installed)
com >> canonical >> indicators >> sound > blacklist-media-players
But unfortunately you might run into this
[https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/1320634](https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/1320634)

---

