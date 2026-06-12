---
title: "How do I speed up the panels' unhide animation"
date: 2008-06-07
forum: General Help
---

### Post by rainwalker on 2008-06-07
I like the animation, but I want it to happen as soon as I hover over the panel area (like the dock does in OS X). I know there has to be a way to change this...can anyone help?

---

### Post by ShodanjoDM on 2008-06-07
press Alt+F2 or open terminal, then type:

```
gconf-editor
```

Navigate to /apps/panel/global/panel_hide_delay and change the value there.

See the screenshot:

[ATTACH]73312[/ATTACH]

EDIT:

There's also /apps/panel/global/panel_0/animation_speed with three options: slow, medium and fast. Hope that helps.

---

### Post by rainwalker on 2008-06-07
I set that and "panel_show_delay" to 0 but didn't see a change. Looking around in Gconf I've found "panel_animation_speed" under that global section, with the current value as "panel-speed-medium". I tried changing that to "panel-speed-fast", but there wasn't any change then either. I also found these settings again under the "toplevels/top_panel_screen0" section and set them to 0, but there's still a delay between mousing over the panel and it unhiding.

---

### Post by ShodanjoDM on 2008-06-07
Oops, my bad, sorry. You're correct that's under /apps/panel/toplevels/

In my case there are two panels (default) the panel0 and top_panel_screen0

if you don't see an option named: animation_speed on the right side, you can create your own. Right click anywhere on option list, and choose "New Key"

Change the Type tab into "string" and fill in the entries as shown in the screenshot below:

[ATTACH]73319[/ATTACH]

---

### Post by rainwalker on 2008-06-07
Perfect! Thanks :)

---

### Post by ShodanjoDM on 2008-06-08
You're welcome. Glad I can help :)

---

### Post by redonwhite on 2008-06-08
> **ShodanjoDM said:**
> Oops, my bad, sorry. You're correct that's under /apps/panel/toplevels/

In my case there are two panels (default) the panel0 and top_panel_screen0

if you don't see an option named: animation_speed on the right side, you can create your own. Right click anywhere on option list, and choose "New Key"

Change the Type tab into "string" and fill in the entries as shown in the screenshot below:

[ATTACH]73319[/ATTACH]

Thanks that helped me too. =)

---

### Post by BrMBr on 2009-07-04
W00T!
Helped me too!
Thank you!!! ):P

---

