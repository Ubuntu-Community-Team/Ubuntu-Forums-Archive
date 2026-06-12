---
title: "most aps ignore ~/.config/openbox/rc.xml's window size/position settings"
date: 2014-01-10
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2014-01-10
In plain openbox (no Lubuntu or LXDE, just Openbox) under Saucy, 32 bit, most of my aps ignore ~/.config/openbox/rc.xml's window position/size settings despite the use of```
<position force="yes">
```.
 The only one I know honors it is Mirage, the image viewer. Certainly firefox, thunar, gedit, and synaptic  ignore it. Here's the relevant portion of rc.xml:
```
  .  .  . [starting near the bottom] . . .
  </menu>
  <applications>
    <!--
  # this is an example with comments through out. use these to make your

 .  .  . [skipping some commented out stuff]

  # end of the example
-->
<!--*************************************-->
<!--
This should correspond to the wmctrl menu line for "very big":
            <position force="yes">
                <x>0</x>
                <y>60</y>
                <width>1912</width>
                <height>970</height>
            </position>
            <maximized>no</maximized>
but doesn't work.
-->
<!--=====================================-->
        <application title="*">
            <position force="yes">
                <x>0</x>
                <y>60</y>
                <width>1912</width>
                <height>150</height>
            </position>
            <maximized>no</maximized>
        </application>
<!--=====================================-->
        <application name="XScreenSaver: StarWars Settings">
            <position force="yes">
                <x>0</x>
                <y>200</y>
                <width>1800</width>
                <height>1080</height>.
            </position>
            <maximized>no</maximized>
        </application>
<!--=====================================-->
        <!-- I want height 970 but I have it set 
            noticeably low so if this finally works
            I'll know it.-->
        <application name="thunar" type="normal">
            <position force="yes">
                <x>0</x>
                <y>60</y>
                <height>150</height>
                <width>1912</width>
            </position>
            <maximized>no</maximized>
        </application>
<!--=====================================-->
        <application title="*File Manager*" type="normal">
            <position force="yes">
                <x>0</x>
                <y>60</y>
                <height>97</height>
                <width>1912</width>
            </position>
            <maximized>no</maximized>
        </application>
<!--=====================================-->
<!--=====================================-->
    <application name="*gedit*">
      <position force="yes">
        <x>2</x>
        <y>60</y>
        <width>1912</width>
        <height>970</height>.
      </position>
      <maximized>no</maximized>
    </application>
<!--=====================================-->
<!--=====================================-->
    <application name="LXTerminal">
      <position force="yes">
        <x>2</x>
        <y>60</y>
        <width>1912</width>
        <height>970</height>.
      </position>
      <maximized>no</maximized>
    </application>
<!--=====================================-->
        <application name="CLEO Options">
            <position force="yes">
                <x>0</x>
                <y>200</y>
                <width>1800</width>
                <height>1080</height>.
        </position>
            <maximized>no</maximized>
        </application>
<!--=====================================-->
        <application name="Conky">
            <decor>no</decor>
            <desktop>all</desktop>
            <layer>above</layer>
            <skip_taskbar>yes</skip_taskbar>
        </application>
<!--=====================================-->
<!--=====================================-->
        <application title="Mirage">
            <position force="yes">
                <x>2</x>
                <y>1</y>
                <width>1912</width>
                <height>1025</height>
            </position>
            <maximized>no</maximized>
        </application>
<!--=====================================-->
    </applications>
<!--*****************************************-->

</openbox_config>
<!-- extra lines to force gedit to show 
     the line numbers correctly 
 . . . [skipping a lot of commented out blank lines]
   extra lines to force gedit to show 
   the line numbers correctly 

-->

```

Any ideas on how to make it work will be appreciated. Thanks for reading.

---

### Post by sandrobrincher on 2014-01-14
3 years later... and I'm still having the same problem! 
=(

---

### Post by vasa1 on 2014-01-14
> **sandrobrincher said:**
> 3 years later... and I'm still having the same problem! 
=(Then follow this thread: [http://icculus.org/pipermail/openbox/2014-January/008409.html](http://icculus.org/pipermail/openbox/2014-January/008409.html)

---

