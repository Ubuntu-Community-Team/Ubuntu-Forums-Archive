---
title: "Slideshow Converter for Flash"
date: 2008-01-06
forum: General Help
---

### Post by SuperMike on 2008-01-06
I have OpenOffice in Ubuntu. Is there a way to make a presentation with it, add sound on each slide, animate it into a tutorial, and then convert it into a Flash presentation for the web?

Here's why I ask. My wife is a school math teacher who uses Ubuntu (as do myself and my children) and she wants to create online tutorials.

---

### Post by SuperMike on 2008-01-06
So far I found that OpenOffice Impress has a way to attach sound to a presentation and it will automatically play when you show the slide. As well, it can export the file as SWF (Shockwave Flash). I can then show it in an HTML page if the page is in the same directory as the SWF (in this example) and putting this code inside it:

```
<object
  type="application/x-shockwave-flash"
  width="600"
  height="450"
  data="test.swf">
<param name="movie" value="test.swf/">
</object>
```

Okay, that's great and all, but the slide doesn't play until each slide is clicked, and then it doesn't play any sound at all.

---

### Post by SuperMike on 2008-01-06
I found another route. If you go to [http://www.spresent.com/](http://www.spresent.com/), you can create a web presentation with synchronized audio, although the interface for the audio can be done a couple different ways, and the sychronization tool in the browser is a little confusing. However, for free, you can make a presentation, stick it in the personal public folder and then share it on the web for others to see. I then stuck the embed tag in the browser and sure enough it played a Flash presentation with sound.

I actually think that Google Docs is easier to use, but you can't do auto-play or synchronized sound with it yet.

---

