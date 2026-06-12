---
title: "starting/stopping services from GUI?"
date: 2007-06-15
forum: General Help
---

### Post by tedk on 2007-06-15
With Gnome, I went to System --> Administration --> Services. I see my services. I can check or uncheck them to have them started at boot time. The help says I should also be able to stop, start, and restart them. The Figure in the Help bears no relation to the screen I see. I don't see any facility in the screen that came up to control the service (other than deselecting it so that it does not start on a reboot).

Does anyone know what's going on here?
 -ted

---

### Post by merlinus on 2007-06-15
Try right-clicking and Properties.

-merlin

---

### Post by tedk on 2007-06-15
I tried that before I posted ... does right-click, show up a Properties for you?

I ended up controlling apache2 from the command line
apache2 -k stop
apache2 -k start
but it's not what I wanted to do.

 -ted

---

### Post by merlinus on 2007-06-15
When I right-click on the name of a service, I get a popup that says Properties.  If I right-click on that, it brings up a settings dialogue with choices.

-merlin

---

### Post by tedk on 2007-06-15
Hmmm ... that does not happen for me. (I'm using Gnome). If I right-click the Service name is highlighted but no popup results. Right-clicks work in other places though.

---

### Post by merlinus on 2007-06-15
I am using Gnome as well,  I have to right-click and hold the button, and then drag it over the Properties pop-up.

-merlin

---

### Post by tedk on 2007-06-15
I do appreciate you're trying this out but honestly I have no Properities popup. Right-click operates the same as Left-Click and just selects (highlights the name). I am on Dapper (because it's supported for so long). Possibly my problem is a Dapper thing.

---

### Post by merlinus on 2007-06-15
I am using Feisty.  I guess the feature has been added since Dapper.

-merlin

---

