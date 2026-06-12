---
title: "Laptop multiple x configs (docked/undocked)"
date: 2005-05-10
forum: General Help
---

### Post by jjanssen on 2005-05-10
Hi,
  I've been poking around the forums and reading the dual head threads with no luck.  What I want to accomplish with my laptop is to have a dual-head xinerama x config for when I'm docked (with 2 external LCD's) and a standard x config for my laptop screen when I'm not docked.  The trick would be being able to easily dock/undock my laptop as seemlessly as possible.  Any ideas?
  My initial thought is runing two X servers, one on :0 for my laptop config and one on :1 for my dual head setup.  I'm not sure that would play nice with gnome and xfce, and would suck up extra memory.

Jay

---

### Post by elsewhere on 2005-05-10
I played around with different scenarios trying to do the same thing.  You could create two server layout sections in your xorg.conf, one for single display and one for dual-head.  Doing a startx -- -layout xxx would let you manually start X with the layout of your choice.  If you really wanted to make it slick, you could create a script that could determine whether you were docked or not and start X with the appropriate layout.

In my case, I cheated a bit with some nVidia specific settings, I'm not sure that they would work on every card.  When I was running spanning desktops with my laptop, I did it with twinview (unique to nVidia) as opposed to xinerama.  The trick was to "force" a monitor onto the second video card with a "connectedDisplay" flag refering to my external monitor.  By forcing a connected monitor, spanned desktops would be enabled as long as the second monitor was attached when X started.  If it wasn't, X would generate an error to the log file refering to the second display not being found, and then continue with a single screen.  Worked well for my purposes because it did specifically what I wanted.  Could be it would work for others, I came across that setup by trial and error mostly.

Under my current setup, I run dual-head with separate desktops, I actually find it easier to work with than spanning.  Now I just don't worry about the config, I just let X boot as it is.  If I'm running on my laptop display only, I just use that desktop.  But if I'm docked with my monitor attached, I have access to that desktop as well.  In reality, both desktops are running whether I'm docked or not.  Not the slickest solution, but it requires no intervention on my part, the additional overhead is imperceptible to me and it doesn't require a restart of X when I dock / undock (which is necessary when spanning desktops).

Certainly not the sexiest way to do it, but works for me.

Hope something here helps ?

Cheers,
KV

---

### Post by jjanssen on 2005-05-11
[QUOTE=elsewhere]I played around with different scenarios trying to do the same thing.  You could create two server layout sections in your xorg.conf, one for single display and one for dual-head.  Doing a startx -- -layout xxx would let you manually start X with the layout of your choice.  If you really wanted to make it slick, you could create a script that could determine whether you were docked or not and start X with the appropriate layout.
[/QUOTE]

That's not a bad idea, it would be reasonable to have all the config in one file.  It would be nice if there was an X mechanism to easily switch between the two, preferably without having to stop your window manager and close all your windows.



[QUOTE=elsewhere]Under my current setup, I run dual-head with separate desktops, I actually find it easier to work with than spanning.  Now I just don't worry about the config, I just let X boot as it is.  If I'm running on my laptop display only, I just use that desktop.  But if I'm docked with my monitor attached, I have access to that desktop as well.  In reality, both desktops are running whether I'm docked or not.  Not the slickest solution, but it requires no intervention on my part, the additional overhead is imperceptible to me and it doesn't require a restart of X when I dock / undock (which is necessary when spanning desktops).

Certainly not the sexiest way to do it, but works for me.

Hope something here helps ?
[/QUOTE]

Thanks for the insight.  I had thought of that, but I'd be more concerned with the window manager sticking new windows on the missing screen, or if I undocked when I was using both screens and then only could use one.  The other difference for me would be having two _external_ monitors and one laptop screen.  I'd only want to use the laptop screen when I'm undocked.  

Another thing that has occurred to me is I've seen X run with a "bigger than the screen" desktop, and you can scroll around it by moving the mouse to the extremeties.  Maybe that could be utilized in some way?  It seems like there's a clever way to do this somehow.


BTW, I'm new to Ubuntu, but I've been using Linux for close to 10 years now.  These forums are great not because of the distro specifically, but because of a lot of good Linux desktop experience to draw from.  (The signal to noise ratio is nice too).  Thanks alot to the Ubuntu developers and maintainers, as well as the admins on this excellent forum.  Thanks!

---

### Post by TryAFrog on 2005-05-11
I too am wanting to do something similar. If you don't mind my asking (still new to Linux), what sections in xorg.conf do I need to edit to enable that second desktop?

---

### Post by jjanssen on 2005-05-12
[QUOTE=TryAFrog]I too am wanting to do something similar. If you don't mind my asking (still new to Linux), what sections in xorg.conf do I need to edit to enable that second desktop?[/QUOTE]
 There is a good thread about getting started with dual-heads here:

[http://ubuntuforums.org/showthread.php?t=31686](http://ubuntuforums.org/showthread.php?t=31686)

My problem is a little more beyond that, but that should get you going.  Hope it helps!

---

