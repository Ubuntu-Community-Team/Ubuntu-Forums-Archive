---
title: "OpenProject +Let's Encrypt"
date: 2021-09-05
forum: General Help
---

### Post by mixmegapol on 2021-09-05
[COLOR=#0E101A][COLOR=#0E101A]Hi all[/COLOR][/COLOR]
[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A][COLOR=#0E101A]I have Ubuntu 20.04 LTS and want to install OpenProject.[/COLOR][/COLOR]
[COLOR=#0E101A][COLOR=#0E101A]However, I have an issue in which order I shall install it:[/COLOR][/COLOR]

[LIST]
[*][COLOR=#0E101A]Let's Encrypt[/COLOR] 
[*][COLOR=#0E101A]OpenProject[/COLOR] 
[/LIST]
[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A][COLOR=#0E101A]When I configure OpenProject, it asks for a web server and SSL certificate location. However, this is the default one from the OS itself.[/COLOR][/COLOR]
[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A][COLOR=#0E101A]Shall I install[/COLOR][/COLOR]
[COLOR=#0E101A][COLOR=#0E101A]apache; letsencrypt; openproject?[/COLOR][/COLOR]
[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A][COLOR=#0E101A]How do you do for having an ssl encrypted OpenProject in domain.cx/op ?[/COLOR]
[/COLOR]
[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A][COLOR=#0E101A]Any help appreciated[/COLOR][/COLOR]
[COLOR=#0E101A][COLOR=#0E101A]Regards[/COLOR][/COLOR]
[COLOR=#0E101A][COLOR=#0E101A]Daniel[/COLOR]
[/COLOR]

---

### Post by dragonfly41 on 2021-09-05
I have been struggling with SSL certificates in desktop Ubuntu 20.04 Apache2 where I hope to test some virtual host sites before publishing on a server.

I have failed so far to get my self signed certificates to work, and be accepted in browser, although I have found some interesting references.

Your query about OpenProject adds a new dimension and being curious I installed it to experiment with it.

According to this video tutorial

[https://www.youtube.com/watch?v=MTHZVQ_89-k&ab_channel=OpenProject](https://www.youtube.com/watch?v=MTHZVQ_89-k&ab_channel=OpenProject)

 at around time at time 8.30 we see that SSL (Let's Encrypt installation) can be deferred until later. So, to answer your question, you can start with OpenProject only. You can test OpenProject/Apache first (HTTP only). Apache should already be installed by default.

I will continue experimenting with installation of OpenProject / Let's Encrypt since it seems a good plan of action.

We can compare notes.

---

