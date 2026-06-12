---
title: "Gvim not available in Applications list"
date: 2006-07-26
forum: General Help
---

### Post by mafitzpatrick on 2006-07-26
I've installed Gvim but it doesn't show up in the Applications list. I've tried this both via Synaptic & the Add/Remove... option available under "Applications"

Clicking Advanced (under Add/Remove...) just starts synaptic, rather than allowing me to create entries directly, so I'm at a bit of a loss what to do.

Any suggestions?  

Thanks,

---

### Post by 5-HT on 2006-07-26
You can use Alacarte Menu Editor (Applications -> Accessories) to add gvim to the Applications menu.

Under the command field for the entry, simply using 'gvim' should work.
If it doesn't, however, you'll need to use the absolute path for gvim.

To find out what the absolute path is, enter the following command in a terminal: ```
which gvim
``` 

HTH

---

### Post by mafitzpatrick on 2006-07-29
> **5-HT said:**
> You can use Alacarte Menu Editor (Applications -> Accessories) to add gvim to the Applications menu.

Thanks for that, I'd knew I had seen something somewhere for doing it but that was not one of the places I looked - seems a counter-intuitive way of editing a menu.

Thanks again for the help!

---

