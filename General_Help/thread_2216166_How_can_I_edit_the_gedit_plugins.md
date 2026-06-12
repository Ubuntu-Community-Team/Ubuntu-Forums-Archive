---
title: "How can I edit the gedit plugins?"
date: 2014-04-10
forum: General Help
---

### Post by Digital Ninja on 2014-04-10
There is a plugin for gedit called Code Comment which, when a key shortcut is pressed, comments all selected lines with the '#' sign. There is nothing in the settings that would allow me to change this behavior, so I would like to know how would I go about editing this plugin to change the comment character to '/'.

---

### Post by Kirboosy on 2014-04-10
So I don't think its a relatively small and easy feat to change but on my Ubuntu system (13.10 64 bit) I found the files relating to the plugin under 

```
/usr/lib/x86_64-linux-gnu/gedit/plugins/codecomment.py
/usr/lib/x86_64-linux-gnu/gedit/plugins/codecomment.plugin
```

I found it running the following commands
```
sudo updatedb
locate codecomment
```

Hope that helps!
~Caboose

---

### Post by Digital Ninja on 2014-04-11
> **Caboose885 said:**
> So I don't think its a relatively small and easy feet to change but on my Ubuntu system (13.10 64 bit) I found the files relating to the plugin under 

```
/usr/lib/x86_64-linux-gnu/gedit/plugins/codecomment.py
/usr/lib/x86_64-linux-gnu/gedit/plugins/codecomment.plugin
```

I found it running the following commands
```
sudo updatedb
locate codecomment
```

Hope that helps!
~Caboose

It helps a bunch! 

If only I knew I could have simply searched for a "codecomment" file, i wouldn't have had to open the thread at all :P On my system (Mint), it was actually under ```
/home/nino/.gnome2/gedit/plugins/codecomment.py
``` and as it turns out the characters are being defined by the language's metadata, not the plugin author himself. So what i could do instead in the plugin, is enlist PHP as one of the languages suitable for block comments (because originally only C was in there), which is also consistent with my other code **and** it allows me to enlist CSS under there too, since CSS only has block comments. 

So that's great. Thank you very much.

---

