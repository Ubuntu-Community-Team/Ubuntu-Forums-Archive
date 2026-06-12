---
title: "Edgy: how to get rid of two icons on desktop"
date: 2006-11-03
forum: General Help
---

### Post by FrankVdb on 2006-11-03
Does anyone happen to know how to remove the "Computer" and "Garbage bin" icons on the Edgy desktop? Their properties don't offer any delete function and I can't find how to remove the icons through the system preferences.

---

### Post by jocko on 2006-11-03
> **FrankVdb said:**
> Does anyone happen to know how to remove the "Computer" and "Garbage bin" icons on the Edgy desktop? Their properties don't offer any delete function and I can't find how to remove the icons through the system preferences.

Start up gconf-editor (run this in a terminal):
```
gconf-editor /apps/nautilus/desktop
```
There you'll see the keys "computer_icon_visible" and "trash_icon_visible".

---

### Post by FrankVdb on 2006-11-03
No key entries there...

I've used the Find function and the keys you mention are nowhere to be found. Even not with the * wildcard.

I see you're an Edgy user. Did you clean install or upgraded from Dapper?

---

### Post by jocko on 2006-11-03
> **FrankVdb said:**
> No key entries there...

I've used the Find function and the keys you mention are nowhere to be found. Even not with the * wildcard.

I see you're an Edgy user. Did you clean install or upgraded from Dapper?

I did a clean install of the edgy release candidate. I don't think the install method will make any difference (dapper had the same keys). Do you have any keys under /apps/nautilus/desktop?

---

### Post by FrankVdb on 2006-11-03
No, not a single key is mentioned.

I don't think this is a nautilus thing. I found a report of a xfce user having the same problem. Xfce doesn't use nautilus.

The gconf-editor is obviously only the GUI of something else. Do you happen to know what?

I've been using Linux for a week now. I still have the impression I know nothing...

---

### Post by jocko on 2006-11-04
> **FrankVdb said:**
> I don't think this is a nautilus thing. **I found a report of a xfce user having the same problem. Xfce doesn't use nautilus.**

I've been using Linux for a week now. I still have the impression I know nothing...

But you are using gnome, right? If you are using Xfce or KDE I wouldn't know how to help you.

Try this:
```
gconftool-2 --install-schema-file /usr/share/gconf/schemas/apps_nautilus_preferences.schemas

```It should add those keys to gconf-editor. 

Or, if you don't have the file /usr/share/gconf/schemas/apps_nautilus_preferences.schemas:
```
sudo aptitude reinstall nautilus nautilus-data
```

---

### Post by FrankVdb on 2006-11-04
Thanks Jocko! Problem solved.

I applied the schema you proposed and the icons indeed showed up in gconf-editor.

Just had to tick them on and then off again  to have them disappear from my desktop.

Looks much better now.

---

