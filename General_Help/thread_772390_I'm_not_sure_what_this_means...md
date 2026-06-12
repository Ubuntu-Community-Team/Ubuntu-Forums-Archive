---
title: "I'm not sure what this means.?."
date: 2008-04-28
forum: General Help
---

### Post by doondoon on 2008-04-28
When I opened CCSM on Hardy I got this message:
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

What do I do with this?

---

### Post by Islington on 2008-04-28
go to the scale plugin and relook at the bindings for Initiate Window picker (monitor icon). There is some sort of conflict with what you have picked and something else and this is why this setting is being ignored.

---

