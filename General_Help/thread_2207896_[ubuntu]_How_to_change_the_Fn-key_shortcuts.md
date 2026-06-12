---
title: "[ubuntu] How to change the Fn-key shortcuts?"
date: 2014-02-25
forum: General Help
---

### Post by KillEmAllx on 2014-02-25
Hi! I have a Asus Zenbook UX32A and I would like to know how I can change the Fn-key shortcuts so that for example, if I want to mute the volume I just hit the "F10" key instead of "Fn+F10". Also, if I do that, I want "Fn+F10" to function as "F10".
Thanks in advance!

---

### Post by TheFu on 2014-02-26
Controlling the key-to-function mapping is controlled by the WM, window manager. Each WM has a different config file ... for example, I use LXDE and it installed openbox .... I wanted super-1, super-2, super-3 to launch different programs, so I edit the file "~/.config/openbox/lxde-rc.xml" and find the parts with keymappings.

```
    <keybind key="W-1">
      <action name="execute">
        <command>firefox</command>
      </action>
    </keybind>
    <keybind key="W-2">
      <action name="execute">
        <command>thunderbird</command>
      </action>
    </keybind>
    <keybind key="W-3">
      <action name="execute">
        <command>keepassx</command>
      </action>
    </keybind>

```

Simple.

You know how alt-tab goes to the next window? Here are those settings in the same file:
```
    <keybind key="A-Tab">
      <action name="NextWindow"/>
    </keybind>
    <keybind key="A-S-Tab">
      <action name="PreviousWindow"/>
    </keybind>

```

Making sense?
There may be a GUI to control this stuff - much harder to explain and it will be different for every "*buntu".  So, you just need to figure out which WM is running on your machine, find the config file and make these small edits.

---

### Post by KillEmAllx on 2014-03-05
How do I find out which WM I'm using? I'm now using Ubuntu 13.10...

---

### Post by Simon_WM on 2014-03-05
Check the BIOS, There will be an option to swop the Fn+Media or Number, and reboot and you can press F10 the audio. and FX to Increase and Decrease volume and brightness

---

### Post by ibjsb4 on 2014-03-05
> How do I find out which WM I'm using

[http://ubuntuforums.org/showthread.php?t=815177&page=2&p=7641318#post7641318](http://ubuntuforums.org/showthread.php?t=815177&page=2&p=7641318#post7641318)

---

### Post by KillEmAllx on 2014-03-14
> **Simon_WM said:**
> Check the BIOS, There will be an option to swop the Fn+Media or Number, and reboot and you can press F10 the audio. and FX to Increase and Decrease volume and brightness

Can you please be more specific? I can't find the setting...

---

