---
title: "Problem with wine"
date: 2007-06-05
forum: General Help
---

### Post by bailout on 2007-06-05
I installed wine from the repos 0.9.33 so that I could run s7raw which is a windows prog for editing fuji camera raw files. It is a single exe prog so didn't need actual installing. I have can run it by opening the wine explorer and going to the exe and running it so the first question is what is the easiest way of starting programs through wine.

The program runs but there is no maximise button and I cannot alter the size of the window. I really need to run it maximised. Any ideas.

I seem to remember installing wine previously from an alternative repo that had later versions than the official ubuntu ones. Is this still recomended?

thanks

---

### Post by happy-and-lost on 2007-06-05
You could create a launch script for it in /usr/bin (probably not the right way of going about it... but it works) like...

*sudo nano /usr/bin/s7rawwin*

paste + edit into that:

```

#!/bin/bash
wine /path/to/s7raw.exe &&
exit
```

then *sudo chmod +x /usr/bin/s7rawwin*

Hopefully, you should then just be able to create a launcher to it using the command *s7rawwin*

There is lots of RAW editing software available for Ubuntu, though ;)

---

