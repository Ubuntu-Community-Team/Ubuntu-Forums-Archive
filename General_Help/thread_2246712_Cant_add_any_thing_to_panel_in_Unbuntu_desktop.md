---
title: "Cant add any thing to panel in Unbuntu desktop"
date: 2014-10-02
forum: General Help
---

### Post by dorlow on 2014-10-02
Some reason my Ubuntu desktop just crashed and my clock and option to log out of Ubuntu disappeared.  Now if I hold down Alt + right click, I don't get the add to panel option either.  If I just right click, I get nothing.  If I alt+right click, I get a menu that says "minimize," "maximize," "move," "resize," "always on top."  That's it.  So, I can't figure out how to add my clock and option to log out back to the panel.  Any suggestions on how to fix this?

---

### Post by grahammechanical on 2014-10-02
What version of Ubuntu are you using and what user interface are you using? In Ubuntu with the Unity user interface we have not been able to add to the top panel by Alt + right click for some years. So, the behaviour that you are seeing is most likely according to design. The missing clock and the power/cog icons is a different matter. You could try this

```
killall unity-panel-service
```

The unity-panel-service should restart automatically and you may get those application indicator icons back.

Regards

---

### Post by deadflowr on 2014-10-02
See if killing it resets it
```
killall unity-panel-service
```
I know this will make it restart when it does exist, so...

Totally ninja'd. lol

---

### Post by dorlow on 2014-10-03
> **grahammechanical said:**
> What version of Ubuntu are you using and what user interface are you using? In Ubuntu with the Unity user interface we have not been able to add to the top panel by Alt + right click for some years. So, the behaviour that you are seeing is most likely according to design. The missing clock and the power/cog icons is a different matter. You could try this

```
killall unity-panel-service
```

The unity-panel-service should restart automatically and you may get those application indicator icons back.

Regards

I'm running Ubuntu 14.04 LTS with the Gnome Flashback Compiz desktop.  I tried what you said by killing it but it didn't work.  I just restarted the PC too by using the shutdown command in a console window (seeing my shutdown menu is also missing) and that didn't work either.

---

### Post by dorlow on 2014-10-03
Just figured it out.  I needed to hold down the windows key + alt + right click.  Beats me why they would require the windows key seeing I'm not running Windows!

---

