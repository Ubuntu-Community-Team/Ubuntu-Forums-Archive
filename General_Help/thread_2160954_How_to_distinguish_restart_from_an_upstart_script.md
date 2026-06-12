---
title: "How to distinguish restart from an upstart script"
date: 2013-07-08
forum: General Help
---

### Post by drjimmy42 on 2013-07-08
From the documentation when "restart" is called on an upstart service, it sends a SIGTERM to the process being managed by upstart and then starts the process again. 

Is there any way, from the process being managed, to determine if upstart is attempting to stop it permanently or is about to restart it? Anything in the environment? Any function to call maybe?  I'd like the app to behave differently when restarting than just stopping and I can't find out how to tell when that is happening. 

Thanks

---

