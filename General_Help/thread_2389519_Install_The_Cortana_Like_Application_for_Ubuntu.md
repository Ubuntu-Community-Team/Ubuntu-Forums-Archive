---
title: "Install The Cortana Like Application for Ubuntu"
date: 2018-04-17
forum: General Help
---

### Post by open4epl on 2018-04-17
I would like to have an Application that works just like Cortana for Ubuntu. I saw one saw on the web but I'm not sure how to install it. Does anyone here know how to do it?

---

### Post by kerry_s on 2018-04-18
what did you see, did you get a name?

---

### Post by open4epl on 2018-04-18
> **kerry_s said:**
> what did you see, did you get a name?

I look through this search> [https://www.google.com/search?ei=J3zGWpVM6ebmAsvwnZAC&q=cortana+for+ubuntu&oq=cortana+for+u&gs_l=psy-ab.1.0.0j0i22i30k1l4j0i22i10i30k1j0i22i30k1l4.847.5044.0.8177.6.4.0.0.0.0.1118.2590.2-1j1j6-1j1.4.0....0...1c.1.64.psy-ab..3.3.2204...35i39k1.0.UuOs6BOe6oc](https://www.google.com/search?ei=J3zGWpVM6ebmAsvwnZAC&q=cortana+for+ubuntu&oq=cortana+for+u&gs_l=psy-ab.1.0.0j0i22i30k1l4j0i22i10i30k1j0i22i30k1l4.847.5044.0.8177.6.4.0.0.0.0.1118.2590.2-1j1j6-1j1.4.0....0...1c.1.64.psy-ab..3.3.2204...35i39k1.0.UuOs6BOe6oc)  

I think it was here> [https://www.pcworld.com/article/2898148/meet-sirius-the-open-source-siri-clone-that-runs-on-ubuntu.html](https://www.pcworld.com/article/2898148/meet-sirius-the-open-source-siri-clone-that-runs-on-ubuntu.html)

The name is "Sirius". How do I install it?

---

### Post by kerry_s on 2018-04-18
i checked out the github for most of those, there like 2->3 years old.
i very much doubt they will work if your running ubuntu 16 or newer.

i'll look around, might be interesting to play with.

---

### Post by kerry_s on 2018-04-18
i would suggest trying this 1:
[https://github.com/DragonComputer/Dragonfire/releases/tag/v0.9.7](https://github.com/DragonComputer/Dragonfire/releases/tag/v0.9.7)

it's a deb you just click on it to install. which will also make removal easy.
the main page at github:
[https://github.com/DragonComputer/Dragonfire](https://github.com/DragonComputer/Dragonfire)

i can't test it for you because my system is not debian based, i would have to build from source & i don't want to.

---

### Post by monkeybrain20122 on 2018-04-18
Sirius has been dead for some times, it became [lucida]("https://groups.google.com/forum/#!topic/lucida-users/OUP7OskemfI"), but the last commit for lucida was like 9 months ago, so that may be dead too. [Mycroft AI]("https://mycroft.ai/documentation/linux/") seems to be the most promising, it is expanding and under rapid development and I think it is a partner of Canonical's, it has a gnome and KDE gui. In other DE it has to be started from terminal, there is a ppa for Ubuntu. I don't know how good it is, it seemed like mainly a toy for enthusiasts and developers last I checked over a year ago, there are some Youtube demos you can check out.

---

