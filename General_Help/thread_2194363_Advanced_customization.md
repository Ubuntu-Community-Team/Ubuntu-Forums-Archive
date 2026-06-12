---
title: "Advanced customization"
date: 2013-12-18
forum: General Help
---

### Post by Tristan_Williams on 2013-12-18
I would first like to say that I have been posting a lot on here lately. It's not because I have a bunch of problems, it's because I have a few problems, people I know have problems, and I see problems that haven't yet been solved, and am generally curious about everything linux related. 

So my question for today is:

What are some advanced customization options for ubuntu?

I have already compiled my own version of the linux-3.11.0-15-lowlatency Kernel.
I have edited my bashrc, /etc/bash.bashrc, and buttloads of other configurations.
I have installed my entire system from the 13.10 minimal install, and built it from there.
I have installed Xfce, and added pieces of gnome, cinnamon, and a few other DE's
I have made my own Gtk theme (I actually edited the source for Numix Gtk)

So what else is there for me to do that would allow me to waste days on end messing with to get just right?
I want something that I absolutely HAVE to backup because it will take a few times to get it right.
I want something that will make me want to gently apply a fist sized hole to my monitor...

---

### Post by ian-weisser on 2013-12-21
You can use Bootchart to monitor your boot services and order, and then tweak those Upstart jobs in /etc/init

You can fidde around with Plymouth's bootsplash options and image.

You can poke around connecting some dbus signals to the notification system, so you get notified every time the wireless strength changes or some trivial event occurs in the background every few seconds.

You can rewrite system tasks or jobs in a new language to get that extra .001 second performance from it.

You can use Conky to fill your desktop with trivia.

You can convert your custom jobs into Unity Scopes.

You can learn to use 'at' jobs.

It's a rich tapestry.

---

