---
title: "[SOLVED] Sopcast Problem"
date: 2008-04-21
forum: General Help
---

### Post by Smudger on 2008-04-21
OK,

I have installed Sopcast, however, when I click on a link to view a sporting event I get the following error:

[IMG]http://i28.tinypic.com/2uz8h8p.png[/IMG]

Any ideas as to how I resolve this problem.

When using Windows if you click on the "Play" link, sopcast automatically pops up and connects to the chosen channel.

---

### Post by phidia on 2008-04-21
I beieve this is an issue with firefox see the webpage [here]("http://kb.mozillazine.org/Register_protocol")

---

### Post by atomkarinca on 2008-04-21
Type "about:config" in your linkbox (without the quotes) then add a new string:

preference name: network.protocol-handler.app.sop
value: gsopcast (or qsopcast or whatever you are using)

---

