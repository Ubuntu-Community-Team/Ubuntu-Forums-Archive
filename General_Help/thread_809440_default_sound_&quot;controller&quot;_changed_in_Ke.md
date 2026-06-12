---
title: "default sound &quot;controller&quot; changed in KeyTouch"
date: 2008-05-27
forum: General Help
---

### Post by rbprogrammer on 2008-05-27
Like many people, I have my own keyboard with multimedia keys.  By default, they don't work. So I installed KeyTouch and it works fine.  Except that the "progress bar" that KeyTouch uses for the sound looks soooooooo ugly.  I like the default that ubuntu has.

How do I get back to that default volume controller??  For some reason, Hardy understood the keycodes for the volume before I installed KeyTouch, but none of the other keys.  But somehow KeyTouch changed the sound controller display.  And I hate it, it looks so ugly.

When I had Gutsy, all I had to do was go into the config file KeyTouch has in my home directory and comment out the volume settings, but that does not work in Hardy.  In Gutsy, this is what I did:

/home/michael/.keytouch2/S510.logitech
```

<keyboard>
  <keyboard-name>
    <model>S510</model>
    <manufacturer>Logitech</manufacturer>
  </keyboard-name>
  <key-list>
    <key>
      <name>Sleep</name>
      <action isdefault="true" action-type="plugin">
        <plugin-name>Lock Screen</plugin-name>
        <plugin-function>Lock Screen</plugin-function>
      </action>
    </key>
    <key>
      <name>WWW</name>
      <action isdefault="true" action-type="plugin">
        <plugin-name>WWW Browser</plugin-name>
        <plugin-function>Home</plugin-function>
      </action>
    </key>
    <key>
      <name>Rotate</name>
      <action isdefault="true" action-type="program"></action>
    </key>
    <key>
      <name>Zoom In</name>
      <action isdefault="true" action-type="plugin">
        <plugin-name>Zoom</plugin-name>
        <plugin-function>In</plugin-function>
      </action>
    </key>
    <key>
      <name>Zoom Out</name>
      <action isdefault="true" action-type="plugin">
        <plugin-name>Zoom</plugin-name>
        <plugin-function>Out</plugin-function>
      </action>
    </key>
    <key>
      <name>100%</name>
      <action isdefault="true" action-type="plugin">
        <plugin-name>Zoom</plugin-name>
        <plugin-function>100%</plugin-function>
      </action>
    </key>
    <key>
      <name>(F1) Battery</name>
      <action isdefault="true" action-type="program">keytouch</action>
    </key>
    <key>
      <name>(F2) Text Processor</name>
      <action isdefault="true" action-type="program">oowriter</action>
    </key>
    <key>
      <name>(F3) Spreadsheet</name>
      <action isdefault="true" action-type="program">oocalc</action>
    </key>
    <key>
      <name>(F4) Presentation</name>
      <action isdefault="true" action-type="program">ooimpress</action>
    </key>
    <key>
      <name>(F5) Undo</name>
      <action isdefault="true" action-type="plugin">
        <plugin-name>Common actions</plugin-name>
        <plugin-function>Undo</plugin-function>
      </action>
    </key>
    <key>
      <name>(F6) Redo</name>
      <action isdefault="true" action-type="plugin">
        <plugin-name>Common actions</plugin-name>
        <plugin-function>Redo</plugin-function>
      </action>
    </key>
    <key>
      <name>(F7) Print</name>
      <action isdefault="true" action-type="plugin">
        <plugin-name>Common actions</plugin-name>
        <plugin-function>Print</plugin-function>
      </action>
    </key>
    <key>
      <name>(F8) Save</name>
      <action isdefault="true" action-type="plugin">
        <plugin-name>Common actions</plugin-name>
        <plugin-function>Save</plugin-function>
      </action>
    </key>
    <key>
      <name>(F9) [a]</name>
      <action isdefault="true" action-type="program">keytouch</action>
    </key>
    <key>
      <name>(F10) [b]</name>
      <action isdefault="true" action-type="program">keytouch</action>
    </key>
    <key>
      <name>(F11) [c]</name>
      <action isdefault="true" action-type="program">keytouch</action>
    </key>
    <key>
      <name>(F12) [d]</name>
      <action isdefault="true" action-type="program">keytouch</action>
    </key>
    <key>
      <name>Media</name>
      <action action-type="program">amarok </action>
    </key>
    <key>
      <name>Play/Pause</name>
      <action action-type="plugin">
        <plugin-name>Amarok</plugin-name>
        <plugin-function>Play/Pause</plugin-function>
      </action>
    </key>
    <key>
      <name>Stop</name>
      <action action-type="plugin">
        <plugin-name>Amarok</plugin-name>
        <plugin-function>Stop</plugin-function>
      </action>
    </key>
    <key>
      <name>Next song</name>
      <action action-type="plugin">
        <plugin-name>Amarok</plugin-name>
        <plugin-function>Next</plugin-function>
      </action>
    </key>
    <key>
      <name>Previous song</name>
      <action action-type="plugin">
        <plugin-name>Amarok</plugin-name>
        <plugin-function>Previous</plugin-function>
      </action>
    </key>
    <key>
      <name>Shuffle</name>
      <action isdefault="true" action-type="program"></action>
    </key>
[B]    <!--
    <key>
      <name>Volume Up</name>
      <action isdefault="true" action-type="plugin">
        <plugin-name>Amixer</plugin-name>
        <plugin-function>Volume increase</plugin-function>
      </action>
    </key>
    <key>
      <name>Volume Down</name>
      <action isdefault="true" action-type="plugin">
        <plugin-name>Amixer</plugin-name>
        <plugin-function>Volume decrease</plugin-function>
      </action>
    </key>
    <key>
      <name>Mute</name>
      <action isdefault="true" action-type="plugin">
        <plugin-name>Amixer</plugin-name>
        <plugin-function>Mute</plugin-function>
      </action>
    </key>
    -->[/B]
  </key-list>
</keyboard>

```

---

### Post by rbprogrammer on 2008-06-17
bump

---

