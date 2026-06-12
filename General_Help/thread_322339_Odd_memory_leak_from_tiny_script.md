---
title: "Odd memory leak from tiny script"
date: 2006-12-20
forum: General Help
---

### Post by happy-and-lost on 2006-12-20
So I got Conky set up nicely, but I had to write a tiny script (27 bytes on disc) which looks like

```
#!/bin/bash
sleep 15
conky

```

Which prevented weird conflicts with Conky and Nautilus and Beryl. I added this script (.conkystart) to my startup and it works a charm. However, when I start the System Monitor, it reports that this tiny script is using 456k of memory (Where Conky itsself only uses 364k)

I know this is only a tiny leak, but why is it happening?

---

