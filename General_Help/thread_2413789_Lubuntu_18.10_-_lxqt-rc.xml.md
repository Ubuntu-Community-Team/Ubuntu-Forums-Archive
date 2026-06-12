---
title: "Lubuntu 18.10 - lxqt-rc.xml"
date: 2019-03-02
forum: General Help
---

### Post by ttylernowicki on 2019-03-02
Hello all,

I'm in the process of converting a couple of machines over to Lubuntu 18.10 which i'm really enjoying by the way! My only problem that I haven't been able to fix or find any information on myself is setting up keyboard shortcuts that use the "windows" key or the left "super" key. Most keyboards bind that key to W in the lxqt-rc.xml file. Only on my laptop, Acer Swift it isn't working with the W.  For example I have the following to snap windows using the shift and directional keys:
   
```
 <keybind key="S-Left">
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>0</x>
        <y>0</y>
        <height>100%</height>
        <width>50%</width>
      </action>
    </keybind>
    <!--
        # HalfRightScreen
    -->
    <keybind key="S-Right">
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>-0</x>
        <y>0</y>
        <height>100%</height>
        <width>50%</width>
      </action>
    </keybind>
```

The S = Shift. I'd like to be able to use the window key instead which would look like this W - Right, W - Left. Only when I set it as that nothing happens when I press those keys. If anyone knows which key I should be using or a simple method to find out it would make my morning!

---

