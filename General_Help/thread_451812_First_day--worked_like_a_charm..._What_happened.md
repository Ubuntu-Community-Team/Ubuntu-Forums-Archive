---
title: "First day--worked like a charm... What happened?"
date: 2007-05-22
forum: General Help
---

### Post by mwilley on 2007-05-22
This has happened to me twice... before with an earlier minefield, and now with test 2.
The first day of installation, Ubuntu worked fine!  It was great (except for boot down issues and me not knowing how to install anything :P) as my first Ubuntu experience.  But the next day, when I boot up Ubuntu, after only about 15 minutes, it will shut down my laptop for random reasons (it seems).  Some of the errors are about my computer reaching a critical temperature, although I know that's not the case.  Any help would be appreciated...

---

### Post by ago on 2007-05-22
is it due to ntfs activation?

[http://ubuntuforums.org/showthread.php?t=451525](http://ubuntuforums.org/showthread.php?t=451525)

---

### Post by tuxcantfly on 2007-05-22
> Some of the errors are about my computer reaching a critical temperature

Are you sure that's not the case? Perhaps the laptop's power management system isn't supported by Ubuntu, I don't see why it would be printing out error messages related to temperature if that weren't the issue, and laptops tend to turn themselves off or otherwise behave unpredictably when they begin overheating... Or maybe it's reading the temperature wrong, and the power management is causing it to shut itself down... Perhaps try disabling ACPI and some other related kernel power management modules, that might fix it...

---

