---
title: "Warning if a download is in progress"
date: 2017-04-11
forum: General Help
---

### Post by raleigh3 on 2017-04-11
Sometimes I have a download occurring when my browser is minimized.

And then I shutdown my computer.

Is there a way to warn me before shutdown that I have a download in progress ?

Thanks.

---

### Post by vasa1 on 2017-04-11
I guess it depends on *how* you shutdown. I try to be as careful as possible to first close all programs I intentionally opened.

Over at the BunsenLabs forum, people came up with a script to close programs nicely before shutdown. It shouldn't be too difficult to rig up something to warn you of certain running applications: [https://forums.bunsenlabs.org/viewtopic.php?id=508](https://forums.bunsenlabs.org/viewtopic.php?id=508)

---

### Post by raleigh3 on 2017-04-12
I use this.

```
#!/bin/bash
# 
#  Shutdown computer  

echo jjjj | shutdown -h now

```
I have found that Ubuntu is pretty good about anticipating when users forget to shutdown properly. :-)

---

