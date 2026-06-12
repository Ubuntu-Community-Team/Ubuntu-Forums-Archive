---
title: "How to identify official Ubuntu packages from a directory of debs?"
date: 2006-09-12
forum: General Help
---

### Post by jamadagni on 2006-09-12
I have downloaded many debs from many sources and they resided in my apt cache. Now I want to classify them and archive them for later use. So I want to know which debs were from official Ubuntu sources and which from third parties.

Is there a way I can do that? Using the key that the deb was signed with or something?

Thanks.

---

### Post by mssever on 2006-09-12
The easiest way I can think of is to open up Synaptic and search for each package name. Make sure the Section column is visible. If it has an Ubuntu logo, it's from the main repository. If the column contains universe, multiverse, etc.--well, you get the point.

I know this isn't a quick way, but the APT system wasn't really designed for what you're trying to do. It's intended that you manage packages, not specific files.

---

