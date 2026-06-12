---
title: "Nautilus/Nemo Script for &quot;touch&quot; (update timestamp of selected file)?"
date: 2014-12-13
forum: General Help
---

### Post by NTL2009 on 2014-12-13
I'd like to update the selected file in Nautilus/Nemo to the current time by right-clicking and selecting a script. I'm using Nemo now (Xubuntu 14.04 LTS if it matters), and I have scripts in the script folder that work for other tasks (I downloaded those somewhere). I tried making my own simple one based on another, I set permissions to match and made it executable, but I get no effect when I right-click it.

Here's a simple one that does work in Nemo, to open the selected file in gedit:

```
#!/bin/bash

gedit $NEMO_SCRIPT_SELECTED_URIS
```

Can't get much simpler than that, right?

And my mod to update the timestamp on the selected file:

```
#!/bin/bash

touch $NEMO_SCRIPT_SELECTED_URIS
```

when I type the touch command into the terminal, and drag the folder I'm trying to update to the terminal, and hit ENTER, it works just fine. What could possibly be wrong with this script?

Is there a simple way to get the script to output any info for debugging?

TIA- NTL2009

---

