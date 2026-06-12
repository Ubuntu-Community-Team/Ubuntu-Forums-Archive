---
title: "Dekstop"
date: 2006-10-28
forum: General Help
---

### Post by bugz0r on 2006-10-28
After I upgraded to Edgy, the Computer and Trash icons have been stuck on my desktop. I checked gconf-editor and the schemas(whatever those are) weren't there. So I followed something on the forums and fixed that, but the visible icons weren't checked. I checked then unchecked them but the Computer and Trash icons are still there. How do I make them go away.

---

### Post by aysiu on 2006-10-28
Is it possible that your *gconf-editor* settings aren't sticking because you lost ownership of some config files in your /home folder?

Does this make any difference? ```
sudo chown -R bugz0r:bugz0r /home/bugz0r
``` Substitute your real username for *bugz0r*, of course.

---

