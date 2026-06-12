---
title: "Devilspie2, Lua scripting and Firefox"
date: 2016-02-27
forum: General Help
---

### Post by Qd64erK on 2016-02-27
Hi,

I'm using Devilspie2 to control some windows on my Xubuntu Trusty 14.04.4. Here's the snippet from devilspie.lua for Firefox:
```

-- Firefox
if (get_window_name()=="Mozilla Firefox") then
-- x,y, xsize, ysize
set_window_geometry2(407,0,1347,1055);
end
```

The thing is, as all Firefox's windows respond to get_window_name()=="Mozilla Firefox" the same way, if I open a new window, devilspie2 puts it on top of each other.
I need something like this:
```

-- Firefox
if (get_window_name()=="Mozilla Firefox")
then
      [COLOR=#ff0000]if the number of opened Firefox windows is 1[/COLOR]
      then
      set_window_geometry2(407,0,1347,1055);
      else
      -- change geometry
      set_window_geometry2(744,264,673,527);
      end
end
```

Is there any way I can "script" the red part? I don't know how...

Thanks in advance
Cheers
**ASENSIO**

---

