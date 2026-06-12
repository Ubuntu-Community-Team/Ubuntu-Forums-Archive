---
title: "Terminal problem"
date: 2007-08-25
forum: General Help
---

### Post by bash on 2007-08-25
Somehow I managed that now my terminal onyl displays "$" instead of the usual "user@comp$". Even if I have cd into a different folder its still just the "$". Also Terminalhistory doesn not work. If I try press up or down key it just displays "^[[A" or "^[[B".

Anybody know how to get back to normal. Oh and im using the default profile.

Included a screenshot for easier understanding:

[[IMG]http://img183.imageshack.us/img183/5/namenlosgx0.png[/IMG]](http://imageshack.us)

---

### Post by flipjarg on 2007-08-25
In regards to your problem with no prompt showing up. You might want to take a look at this guid to [Customizing the Bash Shell Prompt](http://sids.motd.org/wordpressLinux/?p=7).

It might help you figure out if there is something wrong with your **.bashrc** file. I think you can edit how many commands are stored in the history in one of the options menus in the terminal. Try changing the number of lines once. It might fix it... however, I don't know what you were doing before this occurred. If you share that you will probably get better help.

---

### Post by bash on 2007-08-25
I would be happy as well if I would remember what I did when it happened.

I copied now the .bashrc and the .bash_logout file from a system where everything is fine. Still doesn't work. I did a bit of tweaking in gconf_editor. Could I have messed up my console in there? Althougth I don't think there are settings saved in gconf that are terminal related.

---

### Post by flipjarg on 2007-08-26
Have you tried copying **.bashrc** from the root user? You can do this, it would probably be better to do then using one from another system. I'd copy both files from the root user. See if that does anything. Otherwise I haven't any other clues since I don't know what you were doing when this occurred.

---

