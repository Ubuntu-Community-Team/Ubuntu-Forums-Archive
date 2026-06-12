---
title: "Shading ALL Pidgin windows with wmctrl?"
date: 2008-04-03
forum: General Help
---

### Post by NonPermissive on 2008-04-03
I'd like to have a keyboard shortcut that would shade all of my chat windows. I have everything I need, except the ability to apply an effect to *all* windows matching my parameters. Here is what I have so far. ```
wmctrl -x -r pidgin.Pidgin -b toggle,shaded
```
It only shades a single window, then stops. How can I make it do this to all of my chat windows and the Buddy List?

---

### Post by ryanhaigh on 2008-04-04
Can you generate a list of windows matching your criteria and then use some bash scripting to perform this operation for all windows in that list.

---

### Post by NonPermissive on 2008-04-04
*head smack*
Yes I can. Thanks.

---

### Post by ryanhaigh on 2008-04-05
Could you maybe post how you ended up doing this I'm actually looking at doing something similar myself in a few days.

---

### Post by NonPermissive on 2008-04-05
Sure, I'll start on it Monday

---

### Post by NonPermissive on 2008-04-08
To be honest, I'm not very experienced at shell scripting, I'll need to learn a bit to get this done.

---

### Post by sdennie on 2008-04-08
Something like this should do the trick:

shade_all.sh:

```

#!/bin/bash

for window in ` wmctrl -l -x | grep $@ | cut -f"1" -d" "`
do
    wmctrl -i -r $window -b toggle,shaded
done

```

If you save that as shade_all.sh, you should be able to type:

```

./shade_all pidgin.Pidgin

```

And it will toggle all the pidgin windows to and from shaded.

---

### Post by ryanhaigh on 2008-04-08
I did something using python for my problem, it may be useful to you:
[http://ubuntuforums.org/showthread.php?p=4677924](http://ubuntuforums.org/showthread.php?p=4677924)

---

### Post by NonPermissive on 2008-04-12
Thanks a ton man, this owns. I'm putting the hotkey in right now. Sorry it took me so long to reply again, I've been busy. Again, thanks. Ryan, I took a look at your thread, looks interesting, glad you fixed up your problem, but vor's script works perfectly for me. They really should've put this feature into wmctrl in the first place, but at least I learned a bit more about shell scripting now.

---

