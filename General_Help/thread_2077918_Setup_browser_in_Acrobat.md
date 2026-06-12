---
title: "Setup browser in Acrobat"
date: 2012-10-29
forum: General Help
---

### Post by dreamquartz on 2012-10-29
Realized the hyperlinks in my PDF-files do not open an internet link.
I used Acrobat to set the links and they work fine, but opening the file in Ubuntu 12.04 and Acrobat 9, they do not what they supposed to do.

I think it has to do with Edit->Preference->Internet->Set Browser.
I use firefox.
What do I need to do to get the links showing in my browser?

Thx,

Dream

---

### Post by Ms. Daisy on 2012-10-29
Apparmor comes in Ubuntu by default. I believe it's the default setting for AppArmor to block a hyperlink from a pdf.  

This link will tell you how to disable AppArmor if you want to allow it:
[https://help.ubuntu.com/community/AppArmor#Disable_AppArmor_framework](https://help.ubuntu.com/community/AppArmor#Disable_AppArmor_framework)

It would be much better for your personal security if you could use that same link to determine how to allow a hyperlink from a pdf within AppArmor instead of disabling it entirely.  Many internet attacks take advantage of pdfs.

---

### Post by dreamquartz on 2012-10-29
> **Ms. Daisy said:**
> Apparmor comes in Ubuntu by default. I believe it's the default setting for AppArmor to block a hyperlink from a pdf.  

This link will tell you how to disable AppArmor if you want to allow it:
[https://help.ubuntu.com/community/AppArmor#Disable_AppArmor_framework](https://help.ubuntu.com/community/AppArmor#Disable_AppArmor_framework)

It would be much better for your personal security if you could use that same link to determine how to allow a hyperlink from a pdf within AppArmor instead of disabling it entirely.  Many internet attacks take advantage of pdfs.

Thanks for your response,

However trying to open the same pdf-file with Okular, Okular opens KompoZer, which opens the website link.
It does however open it not as a website, but in design mode.
Trying to do a preview, does not open Firefox.

This appears to be an issue of not having Firefox as standard browser, but it is.

I do not quite understand the AppArmor, so I have to look into it more closely.

Thx,

Dream

---

