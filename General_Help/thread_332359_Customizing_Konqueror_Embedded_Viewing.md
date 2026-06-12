---
title: "Customizing Konqueror Embedded Viewing"
date: 2007-01-05
forum: General Help
---

### Post by ImSneakinAround on 2007-01-05
I want to set Konqueror to open image files with a custom View Profile but it doesn't seem to actually work. For example, I set .jpg files to open with Konqueror in my custom "Image" view profile with the following command: ```
kfmclient openProfile Image
``` Konqueror opens the image, but it doesn't load the view profile. Is there a specific way to do this? Or is it impossible? Any feedback would be really appreciated. :)

---

### Post by mexlinux on 2007-01-06
To open a specific profile you must use the --profile option:
```

konqueror --profile Image

```

---

### Post by ImSneakinAround on 2007-01-06
I tried setting up that command for image files and it still yields the same result. The image opens in konqueror, but it doesn't apply the View Profile I want. :neutral:

---

### Post by mexlinux on 2007-01-07
run
```

konqueror --profiles

```
to get a list of the available profiles you can use, and
then use
```

konqueror --profile theExactNameYouGot

```

---

### Post by ImSneakinAround on 2007-01-08
This is [what I get.](http://img458.imageshack.us/img458/416/whatigetvd5.png) This is [what I want.](http://img458.imageshack.us/img458/8031/whatiwantdb7.png) The first screenshot shows my standard Konqueror File Manager view profile simply with the pictures displayed inside. The second picture show my custom Image view profile which is simply a maximized window with the Image view mode enabled.

I have checked, double checked, and triple checked the launch settings for .jpeg and .jpg images and they are both set to: ```
konqueror %U --profile Image
``` As noted, it is opening the pictures in Konqueror, but it isn't applying the view profile. Perhaps i'm going about this the wrong way? Maybe it can't apply the Image View viewmode because that only works for folders? Is there a way then to open the embedded viewer with an image selection box to side as pictured? Thanks again! :)

---

