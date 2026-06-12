---
title: "Gnome panel acts like desktop"
date: 2008-06-02
forum: General Help
---

### Post by JayeD on 2008-06-02
Is there any way to have a panel on the Gnome toolbars that acts like the desktop? The reason I ask is that I often use applications fullscreen and then just dive around the workspaces to switch between them.

My current way to change workspaces is to hover over the workspace switcher and spin the mouse wheel. However, with Compiz turned on I can no longer do this. I also cannot use the cube since I cannot see the desktop to be able to click on it to start the cube. I spend most of my time controlling the PC using the mouse and don't have the keyboard anywhere near me, so the CTRL+ALT+Left/Right is not any use to me either.

I thought that an alternative could be to have a panel on one of the Gnome toolbars that responds like the desktop background would when using Compiz. If I hover over it and spin the mouse wheel the workspaces will change. If I hover over it and click both mouse buttons the cube will start. Maybe even right clicking on it would show the nautilus menu.

I thought about not expanding one of the toolbars and having the desktop exposed at either side, but I didn't like this idea.

Is anyone else aware of any panels that I could add that could have this functionality?

I'm using Ubuntu 8.04

---

### Post by kshane on 2008-06-02
> **JayeD said:**
> Is there any way to have a panel on the Gnome toolbars that acts like the desktop? The reason I ask is that I often use applications fullscreen and then just dive around the workspaces to switch between them.

My current way to change workspaces is to hover over the workspace switcher and spin the mouse wheel. However, with Compiz turned on I can no longer do this. I also cannot use the cube since I cannot see the desktop to be able to click on it to start the cube. I spend most of my time controlling the PC using the mouse and don't have the keyboard anywhere near me, so the CTRL+ALT+Left/Right is not any use to me either.

I thought that an alternative could be to have a panel on one of the Gnome toolbars that responds like the desktop background would when using Compiz. If I hover over it and spin the mouse wheel the workspaces will change. If I hover over it and click both mouse buttons the cube will start. Maybe even right clicking on it would show the nautilus menu.

I thought about not expanding one of the toolbars and having the desktop exposed at either side, but I didn't like this idea.

Is anyone else aware of any panels that I could add that could have this functionality?

I'm using Ubuntu 8.04

Doesn't the viewport switcher in Compiz do just that?  Check under the Compiz Config Mgr.  Lot's of options available to you...

Kevin

---

### Post by JayeD on 2008-06-02
> **kshane said:**
> Doesn't the viewport switcher in Compiz do just that?  Check under the Compiz Config Mgr.  Lot's of options available to you...

Kevin

No. The wheel doesn't work with desktop effects enabled. I did loads of searching on it and it seems to be something that has been reported as a bug a while back but not fixed.

---

### Post by Forlong on 2008-06-02
You know you can actually click on the workspace switcher, right?

If that's not intuitive enough for you, there are several other ways:

For example, enabling **Edge Flip Pointer** in the **Rotate Cube** plugin, will change workspaces, when moving the mouse pointer to a screen edge.

Then there's the **Bindings** tab, where you can bind **Rotate Left/Right** to virtually anything you like (I bound them to the arrows of my "multimedia" keyboard).

You can also map "Edge Flip Pointer" to a screen corner there.

And there's also the possibility to bind your viewports to a key combination (Rotate to Cube Face), e.g [Strg]+[F4] could take you to your fourth desktop.

---

### Post by JayeD on 2008-06-02
> **Forlong said:**
> You know you can actually click on the workspace switcher, right?

Yes, but I don't really like doing that. I find the wheel selection better for me.

> **Forlong said:**
> If that's not intuitive enough for you, there are several other ways:

For example, enabling **Edge Flip Pointer** in the **Rotate Cube** plugin, will change workspaces, when moving the mouse pointer to a screen edge.

That sounds a bit too slow. I have 6 workspaces and currently spin my wheel to get to the one I want. With that I'd have to move to 4 edges of the screen to get from 1 to 5, unless I misunderstood. I will look anyway.

> **Forlong said:**
> Then there's the **Bindings** tab, where you can bind **Rotate Left/Right** to virtually anything you like (I bound them to the arrows of my "multimedia" keyboard).

You can also map "Edge Flip Pointer" to a screen corner there.

And there's also the possibility to bind your viewports to a key combination (Rotate to Cube Face), e.g [Strg]+[F4] could take you to your fourth desktop.

My keyboard is not usually near me when I am on my computer so keyboard bindings aren't an option, plus when I am near me keyboard I am find with CTRL+ALT+Left/Right.

---

### Post by Forlong on 2008-06-02
Then I have another two possible solutions:

If you don't have one, buy a mouse with more mouse buttons -- then bind those to "Rotate Left/Right"

Do not expand one of your panels, so you have some desktop space to scroll on.

---

### Post by JayeD on 2008-06-02
> **Forlong said:**
> Then I have another two possible solutions:

If you don't have one, buy a mouse with more mouse buttons -- then bind those to "Rotate Left/Right"

I have a trackball due to hand problems and don't want to get new hardware just for this. I would just do as I am now and not enable desktop effects.

> **Forlong said:**
> Do not expand one of your panels, so you have some desktop space to scroll on.

I did try this option but didn't really like it. I set the top bar to unexpanded but it then sat in the middle at the top. If it had been on the left at the top then I may have gone for it.

I appreciate your ideas though.

Surely a panel that just captures mouse events and forwards them to nautilus/desktop is possible...

---

### Post by Forlong on 2008-06-02
> **JayeD said:**
> I did try this option but didn't really like it. I set the top bar to unexpanded but it then sat in the middle at the top. If it had been on the left at the top then I may have gone for it.
You can move it anywhere you want (just grab one of the dotted lines on the far left or right).
> **JayeD said:**
> Surely a panel that just captures mouse events and forwards them to nautilus/desktop is possible...
You could file a wish-list report over at GNOME's bugzilla for that (but don't get your hopes up).

---

### Post by JayeD on 2008-06-02
> **Forlong said:**
> You can move it anywhere you want (just grab one of the dotted lines on the far left or right).

You could file a wish-list report over at GNOME's bugzilla for that (but don't get your hopes up).

I'm actually having a look at whether I could write one myself. I think I may try moving the panel at the top tonight. Potentially, If I could have two bars at the top I could almost have a split bar. The drop down menus would still be on the left, the clock on the right and a gap between them would leave me access to the desktop.

---

### Post by Forlong on 2008-06-02
> **JayeD said:**
> Potentially, If I could have two bars at the top I could almost have a split bar. The drop down menus would still be on the left, the clock on the right and a gap between them would leave me access to the desktop.
Also doable. In fact, I had such a setup myself back on Feisty (I had kiba-dock sitting between the two).
Just right-click one of your existing panels and create another one via the context menu.
Like I said, when you disable expand, you can move them anywhere you want.

---

### Post by JayeD on 2008-06-02
Thanks for your help Forlong. I'm gonna have a see what I can do when I get home tonight and I'll report back.

---

### Post by DaymItzJack on 2008-06-02
Have you tried the scale plugin?

---

