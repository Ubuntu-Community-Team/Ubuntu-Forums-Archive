---
title: "Conky Gold &amp; Grey installation"
date: 2014-07-28
forum: General Help
---

### Post by andy69 on 2014-07-28
Hey guys, recently installed the Gold & Grey Conky application.

however after 10 seconds this happends to the application.

[IMG]http://i.imgur.com/4JrP4AG.png[/IMG]

does anyone know anyway to fix this ?

Cheers

---

### Post by Cliff_Simonds on 2014-07-28
It looks like you have multiple instances of conky running(they're stacking on top of each other; it's happend to me), go to system moniter and click the "processes" tab then click "view"  then "my processes" in the drop down box and see how many conkys are running. If it's alot then go to the extra conky and kill their processes. Or just "kill conky" in terminal then restart by typing "conky".
  Are you using conky manager?
Almost forgot: in system monitor, pause your mouse over the conkys and read the pop-up information first,to see if each is the same or different.

---

### Post by andy69 on 2014-07-28
Hey

in the system monitor there are 5 conkys open, however they are all different, one is cpu, other is net, mem, time and disk.

by killing it and retyping conky in terminal, this message shows up

```
Conky: invalid configuration file '/home/andy/.conkyrc'

Conky: missing text block in configuration; exiting
***** Imlib2 Developer Warning ***** :
    This program is calling the Imlib call:

    imlib_context_free();

    With the parameter:

    context

    being NULL. Please fix your program.

```

No i do not have conky mananger, did not know there was one, i am currently installing it

---

### Post by Cliff_Simonds on 2014-07-28
Do you have "conky-all" installed? You'll need it to use and install conky manager. If you're using 14.04 or earlier it should be in software center. If not go to [https://launchpad.net/ubuntu/utopic/amd64/conky-all/1.9.0-4](https://launchpad.net/ubuntu/utopic/amd64/conky-all/1.9.0-4) to download it.

---

### Post by Frogs Hair on 2014-07-28
Conky looks that way when it crashes and changing the window type in the .conkyrc can keep that from happening. I use panel for my current Conky with Unity 14.04 and you can try different options.  

```
own_window yes
own_window_type panel  # other options are: override/dock/desktop/panel
```

---

### Post by QIII on 2014-07-28
Hello!

Are you by chance using a script that sleeps for 10 seconds and then starts conky?  Are you starting after logging out/rebooting from a previous session?

Conkys can build up that way and start creating multiple instances.  The "blur" you see is from the slightly different update times due to different instantiation times.

---

### Post by Cliff_Simonds on 2014-07-29
@andy69,
Have you got your Gold&Grey working correctly now? Did conky manager help?

---

