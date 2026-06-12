---
title: "Firefox 3 b5 on 8.04 - Segmentation fault"
date: 2008-04-24
forum: General Help
---

### Post by KrisWillis on 2008-04-24
I have just upgraded by dev box to 8.04 and upon launching the bundled Firefox 3 b5 it crashes after a second or two. When launching from a terminal, it reports a segmentation fault.

I have tried reinstalling via Synaptic with little success, anybody else experiencing this? Ideas?

---

### Post by hermes0710 on 2008-04-24
> **KrisWillis said:**
> I have just upgraded by dev box to 8.04 and upon launching the bundled Firefox 3 b5 it crashes after a second or two. When launching from a terminal, it reports a segmentation fault.

I have tried reinstalling via Synaptic with little success, anybody else experiencing this? Ideas?


Haven't tried it yet but you should use synaptic to remove (Complete remove) both old and beta firefox and then try reinstalling them since you upgraded and not clean installed hardy.

---

### Post by KrisWillis on 2008-04-24
I have just tried completely removing Firefox, old and new, via Synaptic as well as removing ~/.mozilla/firefox/ then installing again. It's still crashing, but I am getting some more exotic error messages on occasion now...

```
kris@kris:~$ firefox
firefox: tpp.c:63: __pthread_tpp_change_priority: Assertion `new_prio == -1 || (new_prio >= __sched_fifo_min_prio && new_prio <= __sched_fifo_max_prio)' failed.
Aborted
kris@kris:~$ firefox
Segmentation fault
kris@kris:~$ firefox
Segmentation fault
kris@kris:~$ firefox
Segmentation fault
kris@kris:~$ firefox
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
Segmentation fault
kris@kris:~$ firefox
Segmentation fault

```

---

### Post by natrixgli on 2008-04-24
Try launching it with a URL, for example:

```
you@yourbox.com~$ firefox http://www.google.com
```

Could be that your home page has something (i.e. Flash) that is crashing firefox. 

The terminal output you posted looks similar to what you get when flash crashes firefox. 

-n8

---

### Post by KrisWillis on 2008-04-24
No luck launching with a URL either...
```
kris@kris:~$ firefox http://www.kriswillis.com
Segmentation fault
kris@kris:~$ firefox http://www.google.co.uk
Segmentation fault
kris@kris:~$ firefox http://www.google.com
Segmentation fault
```

Sometimes, it doesn't crash on load, but clicking any links on the initial loaded page just makes the browser hang until I kill it - Then I'd get the segmentation fault error, or rarely just 'Killed'.

---

### Post by dorkdork777 on 2008-04-24
Try using Synaptic to uninstall "libflashsupport". I came across this error while testing 8.04 Beta, and removing libflashsupport fixed it completely. It does not remove flash, as I thought originally. :)

---

### Post by KrisWillis on 2008-04-25
> **dorkdork777 said:**
> Try using Synaptic to uninstall "libflashsupport". I came across this error while testing 8.04 Beta, and removing libflashsupport fixed it completely. It does not remove flash, as I thought originally. :)

Thanks for the suggestion, but libflashsupport isn't actually installed on my machine.

---

### Post by FLCLFan on 2008-04-30
I'm getting the exact same problem. The only way to temporally fix it for me is to restart. But this is really annoying.

A fix or cause of this would be great.

---

### Post by KrisWillis on 2008-05-07
After doing a big of digging elsewhere on the internet - I have found a solution that works for me. There appears to have been an incompatability between Firefox and SCIM on my machine. After removing SCIM and its associated packages, my Firefox works fine now.

Is there anything I should be aware of after removing SCIM? I'm not totally clued-up on what it is for...

---

### Post by apocalypso on 2008-08-10
> **KrisWillis said:**
> After doing a big of digging elsewhere on the internet - I have found a solution that works for me. There appears to have been an incompatability between Firefox and SCIM on my machine. After removing SCIM and its associated packages, my Firefox works fine now.

Is there anything I should be aware of after removing SCIM? I'm not totally clued-up on what it is for...

Just for the record, this SCIM removal workaround did it for me too. Still, it makes me wonder why this happens... :-k

---

### Post by apocalypso on 2008-08-16
Ok, ok... this really sucks. One week later, after I thought the problem had solved, as my post above states, I'm back to square one, as Flash started failing again in Firefox. I don't know if it has anything to do with having installed Freeciv, OpenArena and 7Zip, but it doesn't make much sense to me anyway. [-X

I'm going to try installing Flash Player 10 from Adobe Labs and let you all know.

---

### Post by Macdelaney on 2008-09-17
I'm having this same problem with google.com/ig, and i've pinned it down to the official dilbert widget. I've tried removing FF and also the SCIM thing, but nothing works for me. Any one has any ideas??? 
Here's what i get when i run FF from the terminal, just in case
> 
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
Segmentation fault

I've just tried using epiphany and i have the same problem, i really dont know what to do :S

---

### Post by Macdelaney on 2008-09-18
I managed to solved this using this instructions:

[http://www.ubuntu-unleashed.com/2008/05/howto-fix-firefox-and-epiphany-web.html](http://www.ubuntu-unleashed.com/2008/05/howto-fix-firefox-and-epiphany-web.html)

just for the record, the update manager will pop up and tel you there's a update to install, but everything stops working for me after this, so, you are warned.

---

