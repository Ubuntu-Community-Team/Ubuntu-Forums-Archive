---
title: "wine question..."
date: 2005-06-02
forum: General Help
---

### Post by dbloom on 2005-06-02
i'm new to wine and i've tried searching winehq and google, but couldn't find what i'm looking for....

i'm dual booting ubuntu and windows 2000.  there's an application that i'm content launching from the windows drive with wine.  but i was also thinking of installing some programs into a fake windows folder within ubuntu so i could run them directly. 

is this possible?  based on the config files, it doesn't appear so... it seems i can only do one or the other.

thx.

---

### Post by az on 2005-06-02
The only way I could get some apps to work was by installing the recent version of wine, libwine, wine-utils and winetools.

Winetools does a lot of configuring for you and makes a lot of stuff happen that you could not do by yourslef (like installing Internet Explorer)

Winetools does not support (as far as I know) using an existing windows installation.

So, it would seem that you are correct.  Perhaps try installing your software in a fake windows directory?

---

### Post by shof2k on 2005-06-03
[QUOTE=dbloom]i'm new to wine and i've tried searching winehq and google, but couldn't find what i'm looking for....

i'm dual booting ubuntu and windows 2000.  there's an application that i'm content launching from the windows drive with wine.  but i was also thinking of installing some programs into a fake windows folder within ubuntu so i could run them directly. 

is this possible?  based on the config files, it doesn't appear so... it seems i can only do one or the other.

thx.[/QUOTE]
 If your windows program is a simple *.exe file (like notepad or calc), then you can run it using 
**wine *path to *.exe***.
Anything that needs libraries or an API call won't work like this.

Wine and winetools will setup a fake c: drive with thier own dll versions in them.  This should allow you to install SOME windows programs and use them from wine, similar to above (notably office 2000).

You can also swap the builtin dlls for native ones (licencing permitting) to get more functionality but wine don't recommend this anymore.

hope this helps

---

### Post by dbloom on 2005-06-06
ah, thx guys.

---

