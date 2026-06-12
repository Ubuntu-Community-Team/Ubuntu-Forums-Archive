---
title: "Issue with refresh rates"
date: 2016-07-08
forum: General Help
---

### Post by infernouk on 2016-07-08
Hi guys

I am new and trying ot get my hardware working nice with Ubuntu

I have a 4K screen and wanted to be sure im running at 40hz.

I believe i should be using this xrandr command, however its listing my resolution and refresh rate, when i select it, it gives me errors.

I have included an attached screen shot of the console for you to see.

Am i missing something here?

---

### Post by grahammechanical on 2016-07-08
The asterisk indicates the current setting which in your case is a resolution of 3840 x 2160 at 60 Hz refresh rate. The screen does not have a 40Hz refresh rate.

> I have a 4K screen and wanted to be sure im running at 40hz.

And Wikipedia informs me that 3840 x 2160 is what to expect from a 4K Ultra High Definition (UHD) TV. 

[https://en.wikipedia.org/wiki/Display_resolution](https://en.wikipedia.org/wiki/Display_resolution)

Furthermore, I do not think that the * and + sign should be part of any xrandr command. You seem to be trying to set a resolution and refresh rate that the OS is already running the screen at.

```
xrandr --help
```

Regards

---

### Post by infernouk on 2016-07-08
> **grahammechanical said:**
> The asterisk indicates the current setting which in your case is a resolution of 3840 x 2160 at 60 Hz refresh rate. The screen does not have a 40Hz refresh rate.



And Wikipedia informs me that 3840 x 2160 is what to expect from a 4K Ultra High Definition (UHD) TV. 

[https://en.wikipedia.org/wiki/Display_resolution](https://en.wikipedia.org/wiki/Display_resolution)

Furthermore, I do not think that the * and + sign should be part of any xrandr command. You seem to be trying to set a resolution and refresh rate that the OS is already running the screen at.

```
xrandr --help
```

Regards

sorry 40 was a typo, thanks for confirming  its running at 60!

---

