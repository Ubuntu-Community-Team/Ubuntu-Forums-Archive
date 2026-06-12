---
title: "© ASCII Characters in Ubuntu/Linux? ®"
date: 2007-07-24
forum: General Help
---

### Post by OzzyFrank on 2007-07-24
How do I get ascii character working in Ubuntu? In Windows I can hit alt+0169 and get © (copyright) and alt+0174 to get ® (registered) etc, but this doesn't seem to work in Linux (or Ubuntu in particular?).

---

### Post by nick_h on 2007-07-24
Ctrl+Shft+U lets you enter a unicode character. A "_u_" will appear, then enter the unicode code, then press enter.

00A9 = ©
00AE = ®

---

### Post by OzzyFrank on 2007-07-25
Thanks for that. Now that I know I should be looking for "unicode", it made googling for a list of codes easier. Trouble is there's apparently hundreds of thousands of characters, but this site breaks them down into PDFs according to category:

[http://www.unicode.org/charts/](http://www.unicode.org/charts/)

In case anyone is interested, the specific PDF for the characters mentioned above is the "Latin-1" set:

[http://www.unicode.org/charts/PDF/U0080.pdf](http://www.unicode.org/charts/PDF/U0080.pdf)

---

### Post by briandotcom0 on 2008-01-09
The unicode worked for me, but is there any way to get ascii? because I am familiar with the ascii keys more than unicode.

---

### Post by shirilover on 2008-01-09
The other option is to use the compose key -> [https://help.ubuntu.com/community/ComposeKey](https://help.ubuntu.com/community/ComposeKey).
Compose key + c + O = ©
Compose key + R + O = ®

---

### Post by LaRoza on 2008-01-09
> **briandotcom0 said:**
> The unicode worked for me, but is there any way to get ascii? because I am familiar with the ascii keys more than unicode.

The ascii cods are the same as the unicode codes.

---

### Post by yurimxpxman on 2008-01-10
> **nick_h said:**
> Ctrl+Shft+U lets you enter a unicode character. A "_u_" will appear, then enter the unicode code, then press enter.

00A9 = ©
00AE = ®

What about in KDE? Ctrl+Shift+U only works with GTK+ applications.

---

### Post by digisus on 2008-02-19
Thanks for this thread, I just found out about the CTRL-SHIFT-U combination... Now, I realized that in the app where it would be most useful - OpenOffice.org - that key combo does not produce anything! :(
Even here in the browser window I can enter C-S-U 2020 to obtain the small cross: †. But in OO.org Writer I get nothing. 

Is that because OO.org is not a GNOME app? Or can I switch it on somehow? Does it make snese to file a bug (outside GNOME)?

Thanks a lot for your comments/help!
digisus

---

