---
title: "How do I change default behaviour of firefox?"
date: 2013-04-09
forum: General Help
---

### Post by arroy_0209 on 2013-04-09
I use firefoox 20.0 in ubuntu12.04. This version of firefox has a new behaviour, if I download a pdf file, a green downward arrow appears next to search window in the navigation toolbar. The arrow becomes bigger suddenly and when download is completed, iut disappears. Although this will be helpful for some people, I do not want this kind of arrow to tell me when downloading is completed. How do I remove this feature?

Second, I notice with this version of firefox, often at start, firefox automatically chooses to "work offline" which probably means to work ignoring network connection (I am not sure though). But it does not work and I have to use "try again" button in the browser and then it goes online. How do I change this behaviour of transition to offline mode by default?

---

### Post by nerdtron on 2013-04-09
You can still access the old manager by clicking the Firefox Menu>Downloads or Tools>Downloads.

Still, I found this tutorial in a quick google search.
> if you don't like the new Firefox download manager, you can go back to  the old one by toggling a preference in about:config. Just type  "about:config" in the address bar, then search for **browser.download.useToolkitUI**. Toggle the preference from the false value, to true. The old download manager will now be enabled.

Hope that helps.

---

### Post by papibe on 2013-04-09
Hi arroy_0209.

If you remove the download icon, the animation does not happen:
[LIST]
[*]Right click any icon so you can select 'Customize...'.
[*]A new window will open. Position it so you can see the download icon (green arrow).
[*]Grab the icon from where it is, and drag it to the window with the other icons.
[/LIST]
Hope it helps. Let us know how it goes.
Regards.

---

### Post by arroy_0209 on 2013-04-11
It'd worked. Thanks!

---

