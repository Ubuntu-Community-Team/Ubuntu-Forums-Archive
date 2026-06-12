---
title: "How to bind PrtSc to Shutter in Lubuntu 18.04?"
date: 2018-08-30
forum: General Help
---

### Post by petenoob on 2018-08-30
Not sure if this goes here but let me know.

So how do I do this? Thanks

---

### Post by TheFu on 2018-09-01
I don't have 18.04, but if openbox is used still, then this will work ... 

I would edit the XML file in ~/.config/openbox/ and add a stanza ... 
```
<keybind key="W-F6"><action name="Execute"><command>xbacklight -10</command></action></keybind>
```
Obviously, you'd need different stuff, this is how I map the screen dimmer to super-F6.  There's a similar mapping for super-F7 to increase the screen brightness.

There will be lots of examples in the file already.

---

### Post by geofftf on 2018-09-04
The key bindings can be set using  Menu > Preferences > Setup Hot Keys. The relevant key bindings are in the Programs tab. Select the hot key and then Edit from the menu, and follow the instructions here:

[http://shutter-project.org/faq-help/set-shutter-as-the-default-screenshot-tool/](http://shutter-project.org/faq-help/set-shutter-as-the-default-screenshot-tool/)

---

