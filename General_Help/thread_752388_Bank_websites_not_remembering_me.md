---
title: "Bank websites not remembering me"
date: 2008-04-11
forum: General Help
---

### Post by thetejon on 2008-04-11
I'm running Gutsy 7.10 and Firefox 2.0.0.13, and I'm having a problem with my bank (ING - [www.ingdirect.com](www.ingdirect.com)) and my credit card (Chase - cardmemberservices.com) not remembering my computer.  

Don't know how familiar everyone is with the actual process they go through to "recognize" the computer, but every time I log in, I have to redo the registration so they don't ask me all the extra security questions.

My understanding from the tech support person is that they store some kind of file on your hard drive, and then check for the file next time you log in.  It seems this file is not being saved between login attempts.

Anyone have any suggestions?

Thanks.

---

### Post by CyberBob on 2008-04-11
In Firefox click on Tools - Options...   then click on the Security icon at the top.  About half-way down there is a check box next to "Remember passwords for sites"

Be sure this check box is "checked" and everything should work as expected.  I also use both of those financial institutions and have no issues with my computer being "recognized."

Good Luck!

---

### Post by thetejon on 2008-04-11
Thanks for the reply, but that's not the issue.  I have that checked, and it works for other sites - I have plenty of passwords stored in Firefox.

---

### Post by bingoUV on 2008-04-11
I see that the website pages end with asp. Not a good sign. They might be doing some file storing using activex. In windows when you login using Internet Explorer, does it ask you to enable some activex control? If yes, it will not be possible in firefox. 

Anyway, try ies4linux ([http://www.tatanka.com.br/](http://www.tatanka.com.br/)).  It will run Internet Explorer on linux. The website might remember you then.

---

### Post by cdenley on 2008-04-11
I'm pretty sure they store a cookie on your computer. If you delete your cookies (tools>clear private data), then they won't be able to verify it is still you. Firefox may be configured to clear your cookies every time you close it.

---

