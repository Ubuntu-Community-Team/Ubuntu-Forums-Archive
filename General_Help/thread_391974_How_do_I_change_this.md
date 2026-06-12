---
title: "How do I change this???"
date: 2007-03-23
forum: General Help
---

### Post by jakev383 on 2007-03-23
I've finally made the switch to 100% Ubuntu. I've been dual booting for 2 years now and finally got everything to a point where I could switch.
When I first installed 5.10 I got kind of used to a few things. Running Edgy now, and one of the things I want to change is the deskbar panel. It used to have a border around each individual desktop space so I could tell them apart. Now it's "seamless". Is there a way to get the borders between the desktops back? I've attached a screen shot to show where I'm talking about. Can I get a line between the 4 desktops there?
Thanks in advance.

---

### Post by ubuntu27 on 2007-03-24
Strange, I have lines between those workspaces...

Look at my screenshot
[[IMG]http://img256.imageshack.us/img256/1992/edgydesktophj1.th.png[/IMG]](http://img256.imageshack.us/my.php?image=edgydesktophj1.png)

Maybe it has something to do with theme.

---

### Post by jakev383 on 2007-03-24
> **ubuntu27 said:**
> Strange, I have lines between those workspaces...

Look at my screenshot

Maybe it has something to do with theme.

I scrolled through all the themes, even Human and the lines didn't reappear. I'm sure it's something I changed somewhere (I've changed a bit to get it the way I like), but where?!?!?!??!?
Thanks!

---

### Post by jakev383 on 2007-03-24
> **jakev383 said:**
> I scrolled through all the themes, even Human and the lines didn't reappear. I'm sure it's something I changed somewhere (I've changed a bit to get it the way I like), but where?!?!?!??!?
Thanks!
Beryl/Emerald. That's whats changing it. When I switch back to Metacity I get the defining lines back. Now I just need to dig in Beryl/Emerald and see where to change that.

---

### Post by chewearn on 2007-03-24
In Beryl Settings Manager, General Options; there is an item on "Horizontal VIrtual Size" (default 4) and another item on "Number of Desktops" (default 1).

Under Metacity, you get 4 desktops.  In Beryl, you get 1 desktop, which contains 4 horizontal viewports (the viewports form the 3D cube).  So, if you increase the number of desktops to 4, and decrease horizontal virtual size to 1, you get Beryl == Metacity.  But, you loose the 3D cube.

---

### Post by jakev383 on 2007-03-24
> **AstalaVista said:**
> In Beryl Settings Manager, General Options; there is an item on "Horizontal VIrtual Size" (default 4) and another item on "Number of Desktops" (default 1).

Under Metacity, you get 4 desktops.  In Beryl, you get 1 desktop, which contains 4 horizontal viewports (the viewports form the 3D cube).  So, if you increase the number of desktops to 4, and decrease horizontal virtual size to 1, you get Beryl == Metacity.  But, you loose the 3D cube.
Lose the 3D cube.... One of the main reasons I installed Beryl. <sigh> Oh well. Guess I can live with it unless someone knows of another hack to put the borders in there.
Thanks for clarifying that!

---

