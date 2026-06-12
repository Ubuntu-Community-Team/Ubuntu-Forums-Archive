---
title: "Galeon/Mozilla package issue (5.10, AMD64)"
date: 2006-11-23
forum: General Help
---

### Post by darsu on 2006-11-23
I normally use Galeon as browser. Today I updated my Firefox, Mozilla-browser and Epiphany packages to try out the latest versions after a long while. This update broke Galeon!

It seems to me the program stopped being able to know where the Mozilla installation is located. Some shared libraries had gone "missing": libgtkembedmoz.so and libxpcom.so. They were both there in /usr/lib/mozilla, but I symlinked them to /usr/lib, which fixed that. Galeon still won't start, though - now I only get a notification dialog that states

*Ensure the "MOZILLA_FIVE_HOME" environment variable is set to the correct Mozilla installation directory.*

and then exits.

I exported MOZILLA_FIVE_HOME=/usr/lib/mozilla, and consequently MOZILLA_FIVE_HOME=/every/path/i/could/possibly/imagine... No setting seems to work and I'm rather stumped. Can anyone suggest what to do?

---

