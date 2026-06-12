---
title: "HOWTO: Fix Beryl White/Black Cube"
date: 2007-02-28
forum: General Help
---

### Post by v8YKxgHe on 2007-02-28
Hey,

This is for people with ATI/XGL and Beryl who are having the Black/White cube bug.

I've been getting the infamous Beryl White/Black cube recently, and so with some help I found on the Beryl forums I've made a very simple, convenient script to make loading Beryl easy and avoid the White/Black cube.

Ok, make a new file where ever you want (I put mine in my home dir) So, either open up gedit or in Terminal type:

```
gedit ~/.beryl-loader.sh
```

and enter the following in:

```

#!/bin/bash
beryl-manager --no-force-window-manager && beryl-xgl --use-copy

```

Now to make it executable/have correct permissions, in Terminal type:

```

sudo chmod +x ~/.beryl-loader.sh

```

Remove "beryl-manager" from you're startup session (System->Prefs->Session->Startup Tab). What I did then was create a new Custom Application Launcher to my Panel. So, when I load into my XGL session all I do is click the Beryl Icon for my Custom Launcher and Beryl is launched and no White/Black Cube =)

---

