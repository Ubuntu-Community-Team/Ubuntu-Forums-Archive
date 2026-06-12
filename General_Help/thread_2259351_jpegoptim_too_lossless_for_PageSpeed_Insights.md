---
title: "jpegoptim too lossless for PageSpeed Insights?"
date: 2015-01-03
forum: General Help
---

### Post by cobras on 2015-01-03
Hey Folks,

I have an image-heavy website for which I've been relying on jpegoptim  to keep the load times down.  The problem is that Google's PageSpeed Insights keeps telling me to to "[Optimize the following images]("https://developers.google.com/speed/docs/insights/OptimizeImages") to reduce their size by 1MiB (62% reduction)".  It offers details such as "Losslessly compressing [http://www.drumdr.com/Images/megans3-djembe-5-thumb2.jpg](http://www.drumdr.com/Images/megans3-djembe-5-thumb2.jpg) could save 9.5KiB (33% reduction)."

Is jpegoptim the wrong tool for the job?

I'll appreciate any suggestions.

---

### Post by gordintoronto on 2015-01-04
Depending on what version of Ubuntu you are using, you might be getting a very old version of jpegoptim from the software centre. (I'm offered 1.2.3-2, when the current version is 1.4.1, found here: [http://freecode.com/projects/jpegoptim](http://freecode.com/projects/jpegoptim))

The latest version supports setting a "quality factor" to further reduce the file sizes.

Or you could try GIMP.

---

### Post by cobras on 2015-01-05
Thanks.  I'll figure out what version of jpegoptim I'm currently using.

I've been using GIMP to format my images but didn't know it offered lossless compression.  When I format (crop, resize, quality) my images does reducing the quality involve compression?  Is that what you are referring to?

---

### Post by gordintoronto on 2015-01-05
To the best of my knowledge, GIMP compression is lossy. There are severe limits to how much you can compress images losslessly. Life is a trade-off.


> **cobras said:**
> Thanks.  I'll figure out what version of jpegoptim I'm currently using.

I've been using GIMP to format my images but didn't know it offered lossless compression.  When I format (crop, resize, quality) my images does reducing the quality involve compression?  Is that what you are referring to?

---

### Post by cobras on 2015-01-19
So it turns out jpegoptim is exactly what I needed - I just wasn't taking advantage of its full potential.  In particular, I wasn't using it to strip the metadata with the -strip option.  I imagine someone will find this useful.

Thanks for all the useful feedback.  Great forum.

---

