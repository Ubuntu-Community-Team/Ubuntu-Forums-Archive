---
title: "find searches to recursively delete files"
date: 2015-05-19
forum: General Help
---

### Post by derekcentrico on 2015-05-19
I'm having an issue where my cleaning script is wiping out smaller video files that are actually worth keeping.  The scripts reside outside the parent directory.

Originally, I used "find . -name "*.avi" -size -90000k -delete" to wipe out the files matching the argument recursively.  It wiped out files that were outside the paths I intended. (whoops).

However, I figured I should change it to "find /media/storage2/sorting/videos/ . -name "*.avi" -size -90000k -delete" so that it actually acts in the right parent directory and the associated subdirectories.

Is this accurate?  Scared to wipe out more data!

Thanks for any and all help!

---

### Post by Vaphell on 2015-05-19
the easiest way is to have a dry run with the *-delete* part out, so you get to see the default printout. Only when you confirm the files to be deleted are the ones you think they are, press arrow up, type *-delete* at the end and go.
And yes, providing the explicit path instead of . = current dir is advisable. The less ambiguosity, the less things that can go wrong.

---

### Post by papibe on 2015-05-19
Hi derekcentrico.
> **Vaphell said:**
> the easiest way is to have a dry run with the *-delete* part out, so you get to see the default printout.
+1

Be careful, in your example are including both directories:
```

find /media/storage2/sorting/videos/ **[COLOR="#FF0000"].[/COLOR]** -name "*.avi" -size -90000k -delete"
                                     ^
```
find will work in both directories: '/media/storage2/sorting/videos/' and '.' (the current directory).

Regards.

---

### Post by derekcentrico on 2015-05-19
> **papibe said:**
> Hi derekcentrico.

+1

Be careful, in your example are including both directories:
```

find /media/storage2/sorting/videos/ **[COLOR=#FF0000].[/COLOR]** -name "*.avi" -size -90000k -delete"
                                     ^
```
find will work in both directories: '/media/storage2/sorting/videos/' and '.' (the current directory).

Regards.

Okay, so I decided to use -prune instead.  Apparently, there's an issue with -delete and -prune.

"[COLOR=#000000]find: The -delete action atomatically turns on -depth, but -prune does nothing when -depth is in effect.  If you want to carry on anyway, just explicitly use the -depth option.[/COLOR]"

I read the manpage and I'm confused as there is little information on -depth.

The script seemed to work fine though as "[COLOR=#000000]find . -path ./Misc -prune -o -name "*.avi" -size -90000k -delete[/COLOR]"

Any thoughts?

---

