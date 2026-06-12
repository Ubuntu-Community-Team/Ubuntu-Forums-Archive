---
title: "stop taskbar stacking multiple instances of same app"
date: 2020-02-16
forum: General Help
---

### Post by porphyry52 on 2020-02-16
I often run command line apps (vim mc rtorrent) in xterms, which the taskbar sees as 3 instances of xterm, and shows only a single icon for them in the task bar. Any way to get it to show them individually?

---

### Post by thehipho on 2020-02-16
You didn't say what you're using?

```
inxi -S
```

---

### Post by porphyry52 on 2020-02-18
> **thehipho said:**
> You didn't say what you're using?

```
inxi -S
```


```
~ $ inxi -S
System:    Host: a Kernel: 4.15.0-76-generic x86_64 bits: 64
           Desktop: LXDE (Openbox 3.6.1) Distro: Ubuntu 18.04.4 LTS

```

---

### Post by thehipho on 2020-02-18
Let's say you use along xterms, uxterm, and lxterm (they should already be pre-installed|)?

---

### Post by porphyry52 on 2020-02-20
Thanks for the suggestion, but I decided to specify each such xterm's position on screen instead, and forget about using the taskbar to access them.

---

### Post by thehipho on 2020-02-20
Good, there's also many docks you could try like docky, cairo-dock ..etc.

---

### Post by porphyry52 on 2020-02-21
I've never used a dock, but actually I'm now going to take up your first suggestion, a different terminal emulator for each app. You can specify xterm's screen position in its command line, but whether you get it or not depends on how openbox feels; it looks like if the space you want is free you get that space, but if not it instead religiously puts it where the maximum unused space can be covered. Thanks for all your help.

Actually I was a little ahead of myself there. It is far more complex. It is easier to work directly in the openbox rc file, on my system that is > ~/.config/openbox/lubuntu-rc.xml, derived from > /etc/xdg/openbox/rc.xml, because you can update both your hotkeys and your placement specs, <Keybindings for Desktop switching> ln the same file, and if you include an entry like below in that section, by just saving the .xml file and pressing the hotkeys Windows+e it instantly reconfigures openbox with your new settings. ```
        <keybind key="W-e">
          <action name="Reconfigure"/>
        </keybind>

```

But the main problem, setting xterms without their being stacked on top of each other if they have either or both of height and width in common, I was only able to solve by explicitly specifying both size and position and name in each xterm command line in lubuntu-rc.xml, for example, 
```
        <keybind key='W-v'>
            <action name='Execute'>
                <command>xterm -g 80x59+0-1 -name "Vim" -e vim +&quot;norm &apos;0&quot;</command>
            </action>
        </keybind>

```
See man xterm for details. 
```
        <application class='Xterm' name="Vim">
            <desktop>1</desktop>
            <position>
            <x>default</x>
            <y>default</y>
            </position>
        </application>

```
The position setting of default for x and y is the only way that openbox will position xterm as you request in the xterm command line, and it will be placed on the desktop specified, 1.

---

