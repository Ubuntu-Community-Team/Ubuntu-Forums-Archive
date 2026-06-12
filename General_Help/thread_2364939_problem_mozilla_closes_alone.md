---
title: "problem mozilla closes alone"
date: 2017-06-30
forum: General Help
---

### Post by jaircho0312 on 2017-06-30
hello, i have a problem with mozilla firefox, I open mozilla from the terminal To verify errors and later Mozilla closes alone At a specific time and me appears this message in the terminal "(firefox:28918): GLib-GObject-CRITICAL **: g_object_unref: assertion 'object->ref_count > 0' failed", I use selenium ide. please help. thanks

---

### Post by shridhar-kapshikar on 2017-06-30
The cause is obviously in your FF-profile.

Click in FF the menu  (sandwich) icon -> help icon -> information for  troubleshooting  -> click the button on the top right to clean up FF. This will create  a new profile, the bookmarks will be preserved.

And one more thing - Is this an official firefox build from mozilla.org?

---

### Post by jaircho0312 on 2017-07-01
thanks for answering, I already did it and it was closed again And the only thing that changed in the error was this  (firefox:9428). Download mozilla firefox of windows and run it with wine and it worked perfectly, So I want it to work he of linux perfectly. thanks very much

---

### Post by cam17 on 2018-03-21
I have this same problem. I would open firefox and use a web application like [https://testmy.net](https://testmy.net) which measure Internet speed several times over a period of time and when I come back to 16.04.3 LTS firefox has closed. It does seem to be sometime at night possibly after the screen lock occurs.

When I reopen Firefox I am still logged into the account but the measurement has stopped. This occurs on more than one Ubuntu 16.04 LTS.

---

