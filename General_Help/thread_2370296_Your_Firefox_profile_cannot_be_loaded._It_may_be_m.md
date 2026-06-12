---
title: "Your Firefox profile cannot be loaded. It may be missing or inaccessible"
date: 2017-09-01
forum: General Help
---

### Post by raleigh3 on 2017-09-01
I get that message when I click on Visit homepage from within Package Manager.

---

### Post by deadflowr on 2017-09-01
Synaptic?

---

### Post by raleigh3 on 2017-09-02
Yes.

---

### Post by deadflowr on 2017-09-02
Synaptic is probably running as root.
So in general, it failing would be a good thing.
You should always avoid running any browser as root.

(An application running as root usually sets up any application opened through that app to also run as root)

I believe you can run synaptic non-root from a terminal
```
synaptic
```
and then click on the link to open a browser window of whatever app's homepage you click on.

(or right click on the visit homepage link and copy the url then paste it into a browser address bar; this can be done whether root or non-root)

---

### Post by raleigh3 on 2017-09-02
I run Seamonkey as my browser.

---

### Post by vasa1 on 2017-09-02
> **deadflowr said:**
> ...
(or right click on the visit homepage link and copy the url then paste it into a browser address bar; this can be done whether root or non-root)
I think that that is the best route: paste the url into a browser running [s]with[/s]without elevated privileges.

---

### Post by raleigh3 on 2017-09-04
Thanks.

---

### Post by vasa1 on 2017-09-04
I edited my post! Using a browser with elevated privileges is certainly not a good thing to do! Sorry about that.

---

