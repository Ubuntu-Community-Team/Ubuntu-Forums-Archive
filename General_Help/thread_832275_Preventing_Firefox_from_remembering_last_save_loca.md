---
title: "Preventing Firefox from remembering last save location."
date: 2008-06-17
forum: General Help
---

### Post by bluekage on 2008-06-17
Ok, so what I'm asking might sound pretty stupid, but let me explain. As you all know after you save one file, the next file you try to save will bring up the location for the last file saved. Great for saving multiple files relatively quickly, and I like that. My problem is that even after closing Firefox and restarting Ubuntu it still remembers and displays that last save location the next time I try to save a file.

Now there are other people that use this computer on occasion, not enough to warrant giving them their own user, and I would prefer the last thing I saved not be paraded in front of them should they choose to save something.

Is there any way to get Firefox to default to say, my home folder or some other folder after being closed? Please keep in mind that I'm still rather Ubuntu illiterate at this point in time, love everything about it so far and it's great to be rid of Windoze. Thanks for any help in advance.

---

### Post by manfer on 2008-06-17
There is no automatic solution for that on firefox.

You can config automatic deletion of download history, navigation history, cache, cookies, ..., but the last dir used for download would be retained. Maybe it would not be a bad idea that firefox developers included this in the private data clean feature. :)

Only can be done with manual solution. You have to enter the advance configuration about:config, then search for the preference browser.download.lastDir, right-click on it and select "reset" or download some small file to any other directory (desktop for example) before exiting firefox.

I don't know if there's any extension or script to achieve it automatically.

---

