---
title: "Chrome Won't Play Protected Content From Yahoo"
date: 2017-05-04
forum: General Help
---

### Post by sasafrass452 on 2017-05-04
When I try to play a yahoo view video in chrome, it says it can't play protected content (error 3336). I have the setting ticked to allow protected content, but it apparently doesn't work. Is there something I can do?

---

### Post by vasa1 on 2017-05-04
Link to the video?

---

### Post by deadflowr on 2017-05-04
I don't think there is anyway to run yahoo view natively in linux anymore, as it requires drm flash.
Somehow they broke the player when they moved it over from hulu to yahoo.
hulu has  it set to use html5 on chrome, but currently it only runs with flash on view.
No drm flash on linux anymore since adobe felt they had to remove that support when they updated flash from the legacy 11.2 version they had to the newest 25.0 version.
(Maybe someday they will re-add that drm support, but don't hold your breath)

Possible workarounds require a windows browser, either firefox or chrome running in some windows environment, maybe as a wine app (unsure how well that works, things change so what may have been working before may not be broken, very true in regards to wine and apps that need to be updated like firefox, imo) or inside windows directly, either through a virtual machine or as a dual-boot.

(I personally have win7 inside a vm which works well, though it is heavier than I would wish it to be)

Hope it helps, though I feel it won't.

---

### Post by sasafrass452 on 2017-05-04
Even firefox doesn't work.... All I see is a black box on the page. You're probably right that it needs the drm support, so there's nothing I can do from my end. Oh well.... Thanx for the info.

> **deadflowr said:**
> I don't think there is anyway to run yahoo view natively in linux anymore, as it requires drm flash.
Somehow they broke the player when they moved it over from hulu to yahoo.
hulu has  it set to use html5 on chrome, but currently it only runs with flash on view.
No drm flash on linux anymore since adobe felt they had to remove that support when they updated flash from the legacy 11.2 version they had to the newest 25.0 version.
(Maybe someday they will re-add that drm support, but don't hold your breath)

Possible workarounds require a windows browser, either firefox or chrome running in some windows environment, maybe as a wine app (unsure how well that works, things change so what may have been working before may not be broken, very true in regards to wine and apps that need to be updated like firefox, imo) or inside windows directly, either through a virtual machine or as a dual-boot.

(I personally have win7 inside a vm which works well, though it is heavier than I would wish it to be)

Hope it helps, though I feel it won't.

---

### Post by deadflowr on 2017-05-04
Sorry, my rather convoluted response seems to have missed mentioning of Firefox for linux and that it, too, also does not work with yahoo view.

As I stated, possible workaround maybe to install wine, then install windows version of Firefox, then install adobe flash from adobe, and then see if it works.
I suggest Firefox in wine rather than chrome as Firefox in wine has a general history of actually working, whereas chrome ,well, I do not know if anyone has ever gotten windows version of chrome installed in wine, ever.

---

### Post by vasa1 on 2017-05-04
Just a note: this question relates to a service available only in the US of A. Even though no specific link was provided, I found [https://view.yahoo.com/show/the-tonight-show-starring-jimmy-fallon/episode/60884706/kaley-cuoco-horatio-sanz-lp](https://view.yahoo.com/show/the-tonight-show-starring-jimmy-fallon/episode/60884706/kaley-cuoco-horatio-sanz-lp) and got this:

---

### Post by sasafrass452 on 2017-05-05
No problem, I understood what you meant. I'd rather not have to use any workarounds if possible, but I'll see if there's an addon that might work. Thanx, anyway....

> **deadflowr said:**
> Sorry, my rather convoluted response seems to have missed mentioning of Firefox for linux and that it, too, also does not work with yahoo view.

As I stated, possible workaround maybe to install wine, then install windows version of Firefox, then install adobe flash from adobe, and then see if it works.
I suggest Firefox in wine rather than chrome as Firefox in wine has a general history of actually working, whereas chrome ,well, I do not know if anyone has ever gotten windows version of chrome installed in wine, ever.

This is not my issue, since I am in the US.

> **vasa1 said:**
> Just a note: this question relates to a service available only in the US of A. Even though no specific link was provided, I found [https://view.yahoo.com/show/the-tonight-show-starring-jimmy-fallon/episode/60884706/kaley-cuoco-horatio-sanz-lp](https://view.yahoo.com/show/the-tonight-show-starring-jimmy-fallon/episode/60884706/kaley-cuoco-horatio-sanz-lp) and got this:

---

### Post by Habitual on 2017-05-05
Chrome = Open / No DRM
Chromium = DRM

---

### Post by deadflowr on 2017-05-05
> **Habitual said:**
> Chrome = Open / No DRM
Chromium = DRM

Seems backwards.

---

### Post by efflandt on 2017-05-05
Strange, [https://view.yahoo.com/show/the-tonight-show-starring-jimmy-fallon/episode/60884706/kaley-cuoco-horatio-sanz-lp](https://view.yahoo.com/show/the-tonight-show-starring-jimmy-fallon/episode/60884706/kaley-cuoco-horatio-sanz-lp) recognizes me in Firefox because I have AT&T DSL which until recently was using yahoo.com as a portal (Verizon might buy Yahoo). I wonder if it needs a Uverse or cable/satellite TV login. It says FEATURING HULU, but only plays a commercial and not the video. I have a Hulu account and have no problem playing anything on hulu.com. At some point in time Hulu implemented DRM and I had to install "hal" for it to work. But I thought that was no longer needed since Adobe resumed normal flash versions for Linux (I never installed "hal" in 16.10 and Hulu works).

I haven't tested it lately, but Firefox currently works for Hulu (just not Yahoo View), but Chrome didn't (because Pepperflash in Linux didn't do DRM). But Chrome currently works for Netflix (HTML5), but last time I tried Firefox did not. I have Hulu and Netflix accounts, but have not had cable TV since 1995. And I have not even watched broadcast TV for years.

---

