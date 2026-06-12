---
title: "Laptop: Gnome desktop no option for suspend/hibernate on critical battery level"
date: 2018-03-01
forum: General Help
---

### Post by danjde on 2018-03-01
Hi Friends,
using Ubuntu 16.04 and GNOME Shell 3.18.5, on the control panel I've not the option to set if supend or hibernate the laptop on critical battery level.
And so happens that when the battery lever is very low the laptop shut down suddenly.

Do you have any suggestion for me? :-)

Many many thanks!

Davide

---

### Post by dragonfly41 on 2018-03-01
I have looked at my installed GKrellM widget and I see that there is a battery plugin (although I don't have a battery).
You can set an alert.

---

### Post by kerry_s on 2018-03-01
plug it in when it gets to 10%

what else are you looking for suggestions wise?

---

### Post by ajgreeny on 2018-03-01
Hibernation has been disabled by default for a few years in the whole of the *ubuntu family, and it is not really needed as startup from it, in my experience, takes as long as a cold boot, so that being missing from the options is no surprise.

However, suspend should be available.

I have no idea if it would even be possible, but have you considered using another power-manager package such as xfce4-power-manager instead of gnome-power-manager which is what I assume you're using now?
Anybody know if that might work when using gnome-shell?

---

### Post by kerry_s on 2018-03-01
suspend is set to the power button or closing the laptop lid.

there are also extensions you can use for that.

on mine i'm using a applications menu, that has a suspend button
[ATTACH=CONFIG]278728[/ATTACH][ATTACH=CONFIG]278729[/ATTACH]

---

### Post by danjde on 2018-03-02
Hi Friends and thanks for your kind help!
But my question is: why automatically the laptop desn't shout down or hibernate or suspend on critical level battery? It simply go down immediately!
And no options on Gnome power management where to decide what to do..

Thanks again!

Davide

---

### Post by kerry_s on 2018-03-02
if it go's down that's a shutdown = expected if there is no more power
hibernate is disabled & not recommended, but if there's no power it can't hibernate anyway.
suspend would not be good as that relies on power, if it went dead while suspended you could have system corruption.

---

