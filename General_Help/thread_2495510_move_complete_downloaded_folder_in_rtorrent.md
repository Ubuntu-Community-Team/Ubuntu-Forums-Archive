---
title: "move complete downloaded folder in rtorrent"
date: 2024-02-21
forum: General Help
---

### Post by klapvogn on 2024-02-21
Hi,

I am using rtorrent in docker, and I would like it to move the 100% downloaded folder to another folder and continue seeding. 

Here is my attempt so fare and has not been working : 

It should make an hardlink between the folders : ```
/merged/downloads/imported/
```
```
# Define the method
method.insert = d.get_finished_dir,simple,"cat=/merged/downloads/imported/,$d.custom1="


# Bind event "torrent has finished" to action "move to new directory based on label"
method.set_key = event.download.finished,move_complete,"d.directory.set=$d.get_finished_dir=;execute=mkdir,-p,$d.get_finished_dir=;execute=ln,$d.base_path=,$d.get_finished_dir="
```

So fare i'am just getting:
```

--- Error ---
---
mkdir -p /merged/downloads/imported/sonarr
---
```

---

