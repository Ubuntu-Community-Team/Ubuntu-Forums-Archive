---
title: "Firefox/Thunderbird use OS &quot;Open with&quot; dialog"
date: 2015-07-28
forum: General Help
---

### Post by Tim_Drub on 2015-07-28
I am usign Xubuntu 15.04 but this is more a general Firefox/Thunderbird issue than OS related. Still, since I need a Xubuntu specific solution I thought I try my luck here.

Whenever I right-click a file in Xubuntu and choose to "Open with other application..." the following dialog is presented by the OS:

[ATTACH=CONFIG]263432[/ATTACH]

This is nice and I would like Firefox/Thunderbird to behave the same. But if those apps do not have a default application assigned to the MIME type the following dialog is presented:

[ATTACH=CONFIG]263433[/ATTACH]

Is it possible to tell that the default "Open with" dialog of the operating system should be used?
Thanks.

Regards
Tim

---

### Post by kerry_s on 2015-07-28
save the file, right click file-> properties
assign the "open with" to the program you want
that should create the mime type.

---

### Post by Tim_Drub on 2015-07-28
> **kerry_s said:**
> ...
that should create the mime type.

Thanks for the reply but I know how to add MIME types to Firefox. I am not looking for MIME type assignment but changing the default dialog that opens when no MIME type is assigned.

---

### Post by SeijiSensei on 2015-07-29
I don't believe so unless you actually rewrite the Firefox code.  Otherwise it's going to use its own dialog boxes.

I suspect it's because Mozilla is more concerned with having the same look-and-feel across multiple platforms.

---

