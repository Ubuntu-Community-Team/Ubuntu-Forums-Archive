---
title: "No right click &gt; Properties option"
date: 2018-08-10
forum: General Help
---

### Post by webmiester on 2018-08-10
Hi guys,

I am using Ubuntu Mate 16.04 on a Raspberry pi unit.  I am using it for a kiosk system.  As a kiosk system, I locked-down the panel using the dconf Editor:

> Mate > Panel > general > locked-down=true

But I also unchecked and checked a lot of other items which I think is advantageous to my design.

Now I need to fix something on the panel of one of the computers...

So I unchecked the >locked-down from dconf editor, and when I right click the icons, a menu pops up, but there is no "Properties" as an option.  I dont know which of the items in the dconf editor removed "Properties" from the right click menu.

If anyone has any ideas how I can return "Properties", I will really appreciate it.

Thank so much

---

### Post by webmiester on 2018-08-12
Hi guys,

I was able to solve this one finally!  But it took me quite awhile to figure it out.  I would like to share my solution for those working on locking down their system:

from dconf editor:  I found the >org>mate>desktop>app;lications>lockdown>disable command line checkbox.  When it is checked, the properties option disapopears, and when we add to panel, the custom command line option also disappears.  I want to thank all those who read my post.

---

