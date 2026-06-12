---
title: "Synaptic freezes my computer"
date: 2005-10-31
forum: General Help
---

### Post by interval on 2005-10-31
Hi i have ubuntu since june, and i upgraded on the 13th to breezy, and everything worked more or less fine, except for general slowness, and a few buggs.

But yesterday i got this new problem with synaptic. When I try to install a package, my computer freezes completely. I can still move my mouse perfectly well, but nothing else responds and the only solution is to swith the cp off.

The thing is, this doesnt happen only with synaptic. It also happenened while surfing with firefox or chatting with aMSN. Suddenly, the computer just instantly freezes for no particular reason...

This never happened before, it just started yesterday during the night and i had to reboot like 7-8 times in the evening.

Ive searched the forums but nobody seems to have the same problem..

Thanks for helping

---

### Post by suRoot on 2005-10-31
When it happens, can you switch to another console?... meaning, press ctrl+alt+f1 or ctrl+alt+f2 or ctrl+alt+f3 / etc / etc?  If so, log in to one of those consoles to troubleshoot.

You could...

Run top to see if that gives any info...

Look at the logs - I would probably look at either /var/log/messages or /var/log/X*.log first

You could try to start Synaptic with strace:

```
strace -o out.txt synaptic
```

which might give some clues.  This would produce a file called "out.txt" in the current directory which you could review for any errors.

---

### Post by theFallen on 2005-11-03
Hi,

I had the same Problem. I did have a unclean Java installation, after deleting java and doing it described in the Official Guide and after a reboot Synaptic seems to work well again. 
But nevertheless by tracing the output I get the following error and I don't know if its important:

(synaptic:11303): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

cheers,
theFallen


EDIT: Well, it seems I was wrong. It worked fine twice, but then again the same :(

---

