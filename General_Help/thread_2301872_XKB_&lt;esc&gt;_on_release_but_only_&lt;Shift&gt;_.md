---
title: "XKB: &lt;esc&gt; on release but *only* &lt;Shift&gt; if kept down + other key?"
date: 2015-11-05
forum: General Help
---

### Post by trigone on 2015-11-05
Hi!

All in the title. But, to reformulate in more specific, XKB terms, i'd like to know if it's possible to set a keycode that, if pressed then released (without pressing any other key in the meantime), would deliver the <esc> keysym, but, if used in the typical modifier style (neither lock nor latch/sticky), would act as a level modifier (it could be lvl3-4-5, it doesn't need to be shift, aka lvl2), and, especially (!) would not deliver the <esc> keysym at the same time.

The tricky part being of course this: to avoid the modifier aspect of the key to generate at the same time an escape keysym. Since it's in the idea of using it on vim, i guess every vimers will agree it'd be a bit annoying to quit some mode every time this special modifier would be used.

Now, i'm using XKB because i know more or less how it works and it's precise and complete enough so far, but if you have suggestions for the above described effect outside of XKB... it's good too. :)

Of course if you believe it's impossible, well it's technically a useful input too ^^

Thanks in advance!

---

