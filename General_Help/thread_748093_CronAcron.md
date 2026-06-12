---
title: "Cron/Acron"
date: 2008-04-07
forum: General Help
---

### Post by chrisbish on 2008-04-07
Can i use cron/acron to turn my ubuntu server off at say 11 o'clock and use acron to turn it on again at 5 o'clock?

and are there any tutorials on how to do this?

---

### Post by prshah on 2008-04-07
> **chrisbish said:**
> Can i use cron/acron to turn my ubuntu server off at say 11 o'clock and use acron to turn it on again at 5 o'clock?
and are there any tutorials on how to do this?

You can use cron to turn OFF the server, but to turn it on, you have to depend on a BIOS "wake-up" feature.

---

### Post by chrisbish on 2008-04-07
ahh

ok thanks

---

### Post by chrisbish on 2008-04-08
i tired using cron to shut the pc down

but it dosnt work


the comand works as ive enterd it into the termial and it did shut the pc down

but it seems the cron mangers isnt working

can any one help?

i want the pc to shut down everynight at 11 pm.

---

### Post by Cadmus on 2008-04-08
Here's a couple of things I remember from an old post...

[LIST]
[*]It has to be root's cron you set this in, as you need root priveleges to shut down the server
[*]In cron you have to use the full path to the command
[/LIST]

---

### Post by chrisbish on 2008-04-08
> **Cadmus said:**
> Here's a couple of things I remember from an old post...

[LIST]
[*]It has to be root's cron you set this in, as you need root priveleges to shut down the server
[*]In cron you have to use the full path to the command
[/LIST]

yes i used the root cron my using the root terminal and typing in crontab -e or somthing like that and it came up with the cron.

i also put the full path to the comand.


once i put these in i set it about 5 mins in advance at the time i set it.

5mins later it hasnt done anything even if i wait a little while longer still nothing...

---

### Post by chrisbish on 2008-04-08
anyone?

---

### Post by prshah on 2008-04-08
> **chrisbish said:**
> anyone?

> Although  cron  requires  that each entry in a crontab end in a newline
       character, neither the crontab command nor the cron daemon will  detect
       this error. Instead, the crontab will appear to load normally. However,
       the command will never run. The best choice  is  to  ensure  that  your
       crontab has a blank line at the end.


Maybe?

---

### Post by chrisbish on 2008-04-08
heres more detail of what im doing

[http://ubuntuforums.org/showthread.php?t=749450]("http://ubuntuforums.org/showthread.php?t=749450")

---

