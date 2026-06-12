---
title: "Chrome keeps logging me out"
date: 2016-10-04
forum: General Help
---

### Post by dimmaz88 on 2016-10-04
Hi all, I hope someone can help with this as it's driving me crazy.

A few days ago I was trying to figure out how to get all4 to stream (UK channel 4 web service). I followed a few guides, installed HAL. I also did        rm ~/.adobe -rf^C

And also

rm ~/.config/google-chrome/Default/Cookies

Since then, chrome logs me out of each site every time I log off. 

I removed chrome, and reinstalled. Still no joy.

Anyone had similar issues?

TIA

---

### Post by deadflowr on 2016-10-04
Not sure, but HAL is ineffective with Chrome.
Chrome's flash-plugin(aka pepperflash) on linux does not support DRM, which is why you install HAL.
It also has no ties to the adobe folder. It's built entirely different from standard flash.
And standard flash does not run on Chrome anymore.
(Chrome uses PPAPI, or pepper plugin API, as oppose to the older NPAPI or netscape plugin API)

For what it's worth.

To invoke HAL for flash DRM support, you must run flash on Firefox, or any other browser that still supports the NPAPI plugin standards.

---

### Post by ajgreeny on 2016-10-04
In spite of the fact that Channel-4 says it does support Linux on its web-site I have not managed to get their catch-up service All4 to work at all on either chromium (I don't use Chrome) or Firefox, both using flash 23.0.0.162.

It used to work fine as long as you had flash and hal installed, but probably about 3 or 4 years ago it stopped and now totally refuses to work for me, just telling me that I need to install flash plugin, which I have always had on the machine.  The page at [http://www.adobe.com/uk/software/flash/about/](http://www.adobe.com/uk/software/flash/about/) proves that I have version 23.0.0.162, which is the most recent version.

I can not get Channel-5 catch-up to work either.  At least that shows that I have flash installed but the buffering circulating ocin never stops no matter how long I leave it trying.
Can you view Channel-5, or Demand-5 as it's now known, to work for you or is that also failing?

It is slightly annoying, but now having a smart TV with all catch-up services available, I do not watch TV on my computer, so I don't try too hard to get it to work any more.

---

### Post by dimmaz88 on 2016-10-04
Thanks guys, however I'm not bothered about the streaming issue at this point. I'm trying to solve why chrome keeps logging me out of every site.

Scott

---

### Post by deadflowr on 2016-10-04
Try removing the whole chrome profile folder, instead of just the cookies folder.
Then when you re load/launch chrome go to the settings page then advanced settings then content settings and see what the Cookie setting is set at.

---

### Post by dimmaz88 on 2016-10-04
Would I do that through terminal or file browser?

---

### Post by ajgreeny on 2016-10-04
Do it in chrome itself, not the file browser or terminal.

---

