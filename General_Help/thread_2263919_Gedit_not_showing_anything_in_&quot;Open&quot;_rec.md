---
title: "Gedit not showing anything in &quot;Open&quot; recent document list"
date: 2015-02-04
forum: General Help
---

### Post by wendt-mark on 2015-02-04
Ubuntu 14.04 LTS, gedit v3.10.4.  Seen plenty of ways to disable the recent docs in gedit, tried to reverse those, but no luck.

Open gedit, click on the down arrow next to the "Open" button, but it's always grayed out and say no items found.

Is there a setting somewhere that's keeping gedit from saving a list of the last opened files?

Thanks,
Mark

---

### Post by CantankRus on 2015-02-04
Open a few files then look at ~/.local/share/recently-used.xbel 
It should show something like...
```
<?xml version="1.0" encoding="UTF-8"?>
<xbel version="1.0"
      xmlns:bookmark="http://www.freedesktop.org/standards/desktop-bookmarks"
      xmlns:mime="http://www.freedesktop.org/standards/shared-mime-info"
>
  <bookmark href="**[COLOR="#FF0000"]file:///home/glen/conky/configs/demo-conkyrc[/COLOR]**" added="2015-02-04T20:50:01Z" modified="2015-02-04T20:50:01Z" visited="2015-02-04T20:50:01Z">
    <info>
      <metadata owner="http://freedesktop.org">
        <mime:mime-type type="text/plain"/>
        <bookmark:groups>
          <bookmark:group>gedit</bookmark:group>
        </bookmark:groups>
        <bookmark:applications>
          <bookmark:application name="gedit" exec="&apos;gedit %u&apos;" modified="2015-02-04T20:50:01Z" count="1"/>
        </bookmark:applications>
      </metadata>
    </info>
  </bookmark>
  <bookmark href="**[COLOR="#FF0000"]file:///home/glen/conky/configs/weather-waters.conkyrc[/COLOR]**" added="2015-02-04T20:50:04Z" modified="2015-02-04T20:50:49Z" visited="2015-02-04T20:50:04Z">
    <info>
      <metadata owner="http://freedesktop.org">
        <mime:mime-type type="text/x-matlab"/>
        <bookmark:groups>
          <bookmark:group>gedit</bookmark:group>
        </bookmark:groups>
```

---

