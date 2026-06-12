---
title: "Fixed firefox crashed would not restart"
date: 2008-01-03
forum: General Help
---

### Post by sdowney717 on 2008-01-03
I was changing a theme and firefox crashed. go figure.

it would not restart. corrupted somehow?? 
running firefox from terminal yielded no errors.

the fix was this.

go into home folder
show hidden files
select .mozilla folder and rename

use synaptic to completely uninstall firefox including config files
use synaptic to reinstall firefox

reboot

start firefox. it did this time start up
import bookmarks from saved mozilla profile 
they can be retrieved from the renamed .mozilla folder.
bookmarks are showing up as an html doc.

I might try restoring my .mozilla folder back to see if it will work as I had all my extensions there.
at least it is working again.


yes this works. I was able to reuse my .mozilla folder in its entirety. 
everything is as it was before.

---

