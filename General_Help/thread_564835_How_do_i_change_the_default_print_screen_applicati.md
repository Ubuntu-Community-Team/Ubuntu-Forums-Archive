---
title: "How do i change the default print screen application"
date: 2007-10-01
forum: General Help
---

### Post by indiix2 on 2007-10-01
I want to change the default application that is launched when i hit "Print Screen". I want to lauch ksnapshot which i have installed and works. The Gnome default just isn't powerful enough for what i need.

I used to do this on Debian using gconf-editor, but i've looked through that and don't see that option (i believe it used to be under Metacity bindings).

Any ideas?

---

### Post by mexlinux on 2007-10-01
I don't know but, there are some tips in the comments of this post, that might help you:
[http://bbnuke.com/kdevsgnome/2007/09/26/screen-captures/]("http://bbnuke.com/kdevsgnome/2007/09/26/screen-captures/")

---

### Post by indiix2 on 2007-10-02
> **indiix2 said:**
> 
I used to do this on Debian using gconf-editor, but i've looked through that and don't see that option (i believe it used to be under Metacity bindings).

Ok. i figured it out. It was in gconf-editor. Putting it here for others to find if searching:
[LIST=1]
[*]Hit ALT+F2 and type "gconf-editor".
[*]Click apps -> metacity -> keybinding_commands.
[*]Change "command-screenshot" value to "ksnapshot"
[*]Change "command-windows-screenshot" value to "ksnapshot --current"
[*]Close gconf-editor
[*]Try Print Screen and ALT+Print Screen
[/LIST]

---

### Post by jcarey on 2008-03-16
Thanks for posting your solution indiix2.  Found it on from google search, exactly what I was looking for.  Worked great! (of course I'd already installed ksnapshot)

---

