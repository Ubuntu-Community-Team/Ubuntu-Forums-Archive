---
title: "Where can I find the profile for Firefox 2 in Hardy?"
date: 2008-05-03
forum: General Help
---

### Post by navneeth on 2008-05-03
I have Firefox 2 installed in 8.04, but I'm not able to enable any of the extensions that were disable by Fx3Beta5. I actually wanted to import my settings from the earlier installation (using FEBE, which is also disabled, BTW.), so I went in search of the profile manager. And

```
./firefox -profilemanager
```,

from ~/firefox, just restars Firefox 2. :( (I guess that may be wrong since it's the folder F3B5?)

Any tips to find the location of the profile, or to enable the extensions would be great. 

Thank you. 

FYI: I have the dev build of Tabs Mix Plus installed.

---

### Post by Zorael on 2008-05-03
I'm not sure I can answer all of your questions, but FF3 and FF2 seem to share profile folder, which is located at **~/.mozilla/firefox**.

As for FF3 disabling extensions and FF2 being unable to enable them again, I managed to do it by clearing cache before exiting FF3, then opening and closing FF2 once. Then I could enable them again.

---

### Post by navneeth on 2008-05-03
> **Zorael said:**
> I'm not sure I can answer all of your questions, but FF3 and FF2 seem to share profile folder, which is located at **~/.mozilla/firefox**.

Thanks for the reply and the information about the folder. 

> As for FF3 disabling extensions and FF2 being unable to enable them again, I managed to do it by clearing cache before exiting FF3, then opening and closing FF2 once. Then I could enable them again.

That didn't work. :( Even re-booting didn't help. In fact, something I forgot to mention earlier, even the enabled extensions don't work in Fx2. (But they do in Fx3.) I'm missing the services of important ones like NoScript, ABP, etc. I guess I'd have to stick with Fx3, until I find a solution or Fx3 comes out of beta and extensions are available, whichever is sooner.

---

