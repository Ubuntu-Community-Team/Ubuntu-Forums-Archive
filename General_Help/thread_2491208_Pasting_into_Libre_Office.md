---
title: "Pasting into Libre Office"
date: 2023-09-29
forum: General Help
---

### Post by Autodave on 2023-09-29
Weird thing has just recently started.  Trying to create a document.   When copying something from one document into another, the part that is  copied will then be pasted 2,3 4, or even 5 times into the new document.   Sometimes it is one right after the other, sometimes it seems to  randomly split one of the copies and insert another in the middle.  Any  ideas?

---

### Post by Holger_Gehrke on 2023-09-29
Sounds a bit like a bouncing key switch (or mouse button if you're pasting using X-selection and middle mouse button). Have you tried whether pasting in other programs misbehaves too ? If yes, then I'd suspect the 'v' key (or middle mouse button). On XUbuntu there is a setting in "Accessibility" to reduce effects like this called 'Bounce keys' which stops multiple rapid keystrokes from registering.

Holger

---

### Post by Autodave on 2023-09-29
LO is the only one that exhibits the problem.  I have also tried using the CTRL V instead of the mouse button, but no difference.

---

### Post by SeijiSensei on 2023-09-30
How about Shift+Ins?

---

### Post by Autodave on 2023-09-30
Never heard of that before.....will try next time.

---

### Post by Holger_Gehrke on 2023-09-30
Only in LO ... there goes my "bouncing key switch" theory. Next step would be determining if it's specific to your settings or if it's a general problem. Easiest way to test that would be to create a second user account, log in with that and test whether the problem occurs. If it doesn't then it's either a setting (~/.config/libreoffice/4/user/) or an extension to LO you installed for your normal user account.

Holger

---

### Post by Autodave on 2023-09-30
I will try the second user and see what happens.  As for extensions, I have not installed any.

---

### Post by tea for one on 2023-10-01
LibreOffice has a safe mode for trouble shooting.
[https://help.libreoffice.org/latest/en-US/text/shared/01/profile_safe_mode.html](https://help.libreoffice.org/latest/en-US/text/shared/01/profile_safe_mode.html)

---

### Post by Autodave on 2023-10-15
> **SeijiSensei said:**
> How about Shift+Ins?

Just got back to this thread........ the Shift+Ins worked great!  Why?  What makes that work and not the normal ways?

Thanks!  I will try a couple of the other ways suggested next time and let you all know what happens.

---

