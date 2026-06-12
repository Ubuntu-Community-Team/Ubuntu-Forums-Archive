---
title: "GADMIN-PROFTPD Cant allocate enough ram, exiting"
date: 2013-01-27
forum: General Help
---

### Post by l2d4y3 on 2013-01-27
After I opened GADMIN-PROFTPD on lubuntu for the first time, A windows poped up.

> GADMIN-PROFTPD could not find the proftpd configuration
or you are using a basic configuration that doesnt have
all the features that this program requires.


Do you want to overwrite your current proftpd configuration
with a suitable standard configuration for gadmin-proftpd ?

            (If you don't know then press yes)And after I clicked yes, the program exited and in the terminal it showed > Cant allocate enough ram, exiting

How can I fix this?

---

### Post by dagomar on 2013-05-14
I found the nswer on a German ubuntu forum here: [http://forum.ubuntuusers.de/topic/gadmin-proftpd-cant-allocate-enough-ram-exitin/](http://forum.ubuntuusers.de/topic/gadmin-proftpd-cant-allocate-enough-ram-exitin/)

The steps in the answer work for me:

[COLOR=#000000][FONT=sans-serif]1. At the first prompt, click no
[/FONT][/COLOR][COLOR=#000000][FONT=sans-serif]2. Press the tab 'configuration'
[/FONT][/COLOR][COLOR=#000000][FONT=sans-serif]3. Empty the contents
[/FONT][/COLOR][COLOR=#000000][FONT=sans-serif]4. Click safe[/FONT][/COLOR][COLOR=#000000][FONT=sans-serif]5. Click standard
[/FONT][/COLOR][COLOR=#000000][FONT=sans-serif]6. The same prompt apears
[/FONT][/COLOR][COLOR=#000000][FONT=sans-serif]7. Now click Yes
[/FONT][/COLOR][COLOR=#000000][FONT=sans-serif]8. A new config should appear
[/FONT][/COLOR][COLOR=#000000][FONT=sans-serif]9. Click safe
[/FONT][/COLOR][COLOR=#000000][FONT=sans-serif]That should do it![/FONT][/COLOR]

---

### Post by eikoninaru on 2013-09-14
Thanks! Your advice helped me a lot!

---

