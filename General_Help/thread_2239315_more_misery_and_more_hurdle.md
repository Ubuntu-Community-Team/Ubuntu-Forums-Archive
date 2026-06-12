---
title: "more misery and more hurdle"
date: 2014-08-13
forum: General Help
---

### Post by christon74 on 2014-08-13
Hello, yes it is me again and I am in 'whino' mood:cry:
I have checked what's in the setting and here is my list:
-language support; security and privacy;printers; landscape service (which I certainly do not need at all); software and updates. And that's it. Is that it? Yes! 
sound settings? not there. Appearance? not there either. 
And if I try dowloading any software from the ubuntu software centre I get this message:
'You are not allowed to perform this action!'
Failed: ('system-bus-name', {'name': ':1.118'}): org.debian.apt.install-or-remove-packages

Now I wish I HAD NOT upgraded to 14.04 !!!!!

---

### Post by CantankRus on 2014-08-13
Usually caused by adding repositories and/or other desktop environments.
Quick fix: Backup and do a fresh install. 

P.S. The whinos I know usually carry brown paper bags.

---

### Post by christon74 on 2014-08-13
Hello CantankRus and thank you for answering so quickly. 
Awww no! Doing a back-up and a fresh install? Thanks but no thanks. I think I now have to make do with what I have got. As for adding new repositories... I do not even know how to do that. Adding other desktop environments? What do you mean? I have had this reconditioned hp Dc 7700 for nearly four years now....

---

### Post by christon74 on 2014-08-13
Hello again CantankRus 
Another reason for which I am loath to do a re-install: I am on dual boot. I have windows vista and Ubuntu14.04 LTS. It was almost a fluke I successfully installed Ubuntu 12.04 LTS the first time and I am not confident I can re-install it without losing Vista. And I do not want to lose it.

---

### Post by christon74 on 2014-08-13
Problem solved! Hallelujah (and this from me, a professed atheist! :lolflag:)
Here is the solution for all of us who have been faced with this particular difficulty:
open a terminal window and type this:
sudo apt-get install ubuntu-desktop

___re-installing the package ubuntu desktop___ 
it worked for me: why should not this work for others? ;)

---

