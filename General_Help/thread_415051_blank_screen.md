---
title: "blank screen"
date: 2007-04-20
forum: General Help
---

### Post by rikamus on 2007-04-20
wasn't sure where to stick this (possibly in destop effects?) but nm. thought i'd play with desktop effects just now so installed the nvidia drivers it prompted and everything was working cool. then i rebooted. seems like that was an error - now ubuntu gets to the login screen, i login and then nothing loads. just the cursor. and a horrible light beige background. it'll quite happily sit there forever. umm...help?

---

### Post by strabes on 2007-04-20
What have you changed since your desktop was working properly? Did you change anything in your xorg.conf?

You can remove the nvidia drivers that apparently broke your system via terminal by hitting ctrl+alt+F1 and then typing "sudo aptitude remove <nvidia package name>"

I don't know anything about nvidia since I unfortunately have an ATI card. Sorry if this doesn't help you.

---

