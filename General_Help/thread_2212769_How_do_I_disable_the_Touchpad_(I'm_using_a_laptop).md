---
title: "How do I disable the Touchpad (I'm using a laptop)"
date: 2014-03-23
forum: General Help
---

### Post by Ferinand_Bartolome on 2014-03-23
I want to disable the touchpad because when I'm using the mouse, and when I'm typing, my palm accidentaly touches the touchpad and messes up everything. Please Help.

---

### Post by bug67 on 2014-03-23
Which *buntu are you using?  I would imagine it's similar in all various *buntus.  I don't have my Unity machine in front of me right now so, I can't say for sure how to do this.  However, in Xubuntu, if you launch Settings Manager > Mouse and Touchpad, there should be a setting to enable/disable the touchpad while typing or disable the touchpad all together.  Let us know if this helps.

---

### Post by Rex Bouwense on 2014-03-23
If you are using Lubuntu as your title states, read this.
[https://help.ubuntu.com/community/Lubuntu/Mouse#Disable_touchpad_while_typing](https://help.ubuntu.com/community/Lubuntu/Mouse#Disable_touchpad_while_typing)

---

### Post by Peter Maunder on 2014-03-23
Many laptops have a function key to enable/disable the touchpad. You should check to see whether yours does. On mine pressing the Fn key with F7 gives me this function. Otherwise follow the advice above to use the software.

---

### Post by walterorlin on 2014-03-23
You can if you open up a terminal if you want to completely turn it off just by software try ```
synclient TouchpadOff=1
``` I think you could make a keybinding for this if you wanted to in ~/.config/openbox/lubuntu-rc.xml to make a keyboard shortcut. use ```
synclient TouchpadOff=0
``` if you want to turn it back on.

Edit it will be more useful to have it bee like this in 
~/.config/openbox/lubuntu-rc.xml not between any of the xml tags in with the other places that say keybind. 

```

 <keybind key="W-q">
      <action name="Execute">
      <command>synclient TouchpadOff=0 </command>
      </action>
  </keybind>
 <keybind key="W-w">
      <action name="Execute">
      <command>synclient TouchpadOff=1 </command>
      </action>
  </keybind>

```

This has the super (windows) key plus q have turn the touchpad off and super w turn the touchpad off. Making a toggle button would be a little more complicated.

Also after putting that in the file and saving the file run 


```
openbox --reconfigure
``` to load the new openbox configuration.

---

