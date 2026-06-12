---
title: "Python cant open file error Open Drone Map"
date: 2016-06-29
forum: General Help
---

### Post by luckystar3 on 2016-06-29
Hello all,
attempting to run open drone map and run into the below:

/Pictures/images$ python ../OpenDroneMap/run.sh
python cant open file '../OpenDroneMap/run.sh' [Errno2] no such file or directory

Any ideas?

---

### Post by Impavidus on 2016-06-29
You either used the wrong name or are in the wrong directory. For that command to work, you must have a python script at (something)/Pictures/OpenDroneMap/run.sh.

I assume you only gave a partial path in your post, as this looks like an absolute path, but the Pictures directory would normally be placed in your home directory. And .sh files are usually shell scrpts, not python scripts, but this could be an exception. You can give a script file any extension or none at all and it still works.

---

