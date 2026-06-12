---
title: "xorg crash"
date: 2007-02-11
forum: General Help
---

### Post by 21_adam_12 on 2007-02-11
i have beryl install on ubuntu. i have a dual core processor and i have two monitors. my setup works fine when i boot into Ubuntu, kernel 2.6.17-[COLOR="Blue"]10[/COLOR]-generic but when i boot into Ubuntu, kernel 2.6.17-[COLOR="Blue"]11[/COLOR]-generic it manages to start up but it says failed to start xorg or somethig like that. does any one know y this error occurs? and if they do could they please help me to fix it?

---

### Post by bscbrit on 2007-02-11
I cannot  help you fix your immediate problem, but I understood that beryl is still in an early stage of development and is not a fully  released version at present.  In fact, I think that they give you a written warning to this effect.  If that is the case, then  you really should expect this sort of problem and you can bet that the developers are working to fix it - but it is unlikely that anyone else can provide the help that you seek.

Sorry.

---

### Post by Gibbs on 2007-02-11
I think it happens because a driver or device isn't found or working. I don't know anything about Beryl or the sort but you should have a backup of xorg.conf. In the shell terminal rename or move xorg.conf and then replace it with the backup.

Start the X service and go from there. I've heard people have had difficulties with graphic drivers since a kernel update. I ran a nice little script called Envy and it worked fine.

---

### Post by 21_adam_12 on 2007-02-12
so if i wait for a newer release of beryl will that have bug fixes in it?

---

