---
title: "Gimp problems - convert  RGB -&gt; CMYK"
date: 2005-09-07
forum: General Help
---

### Post by markuman on 2005-09-07
hi everyone.

is it possible to convert a jpg file RGB in a jgp file with CMYK colors and 300dpi ?
how?

---

### Post by coolclassic on 2005-09-07
Try here:
[http://www.blackfiveservices.co.uk/separate.shtml](http://www.blackfiveservices.co.uk/separate.shtml)

---

### Post by ad noiseam on 2005-12-09
[QUOTE=coolclassic]Try here:
[http://www.blackfiveservices.co.uk/separate.shtml](http://www.blackfiveservices.co.uk/separate.shtml)[/QUOTE]

Has anybody been able to install this plug-in and make it work? I tried, and just couldn't get this to show up in The Gimp. :-(

---

### Post by h6w on 2007-02-15
Yeah, the plugin appears to be asking for gimp library 2.0.0 .  Anyone know where the 2.2 version of this is?

Cheers,
Tudor.

---

### Post by stuporglue on 2007-04-23
I just downloaded the plugin here [http://www.blackfiveservices.co.uk/separate.shtml](http://www.blackfiveservices.co.uk/separate.shtml) (same link as above) and then noticed that the plugin is looking for libtiff.so.3, but as of Feisty (Don't know about previous versions), all I've got is libtiff.so.4. Soft linking the libtiff.so.4 library seems to have done the trick. 

```
sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
```

It seems to have separated the colors into layers just fine, but I can't tell if everything is working correctly because I'm still a bit new to CMYK/prepress stuff.

---

