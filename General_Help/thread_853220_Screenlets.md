---
title: "Screenlets"
date: 2008-07-08
forum: General Help
---

### Post by lucky.developer on 2008-07-08
i downloaded screenlets 0.0.7 from compiz web site.
And i installed it by sudo make install command

then, i wrote the following command to start the screenlets daemon

$screenletsd start

it said...

Session-file /home/lakshmanan/.config/Screenlets/screenletsd.ses not found (will be created automatically).

when i tried to add Clock screenlet(by screenletsd add Clock), it said

Error: Screenlets-Backend (screenletsd) not found.


How can i resolve this... please help

---

### Post by sayakb on 2008-07-08
At a terminal:
```
screenlets-manager
```

---

