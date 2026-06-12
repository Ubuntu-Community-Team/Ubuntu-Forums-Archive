---
title: "Migrate Passwordmaker to Passwordmaker pro for Firefox 57"
date: 2017-11-17
forum: General Help
---

### Post by cscj01 on 2017-11-17
I have been using the original Passwordmaker add-on for Firefox under Ubuntu for years.  All my passwords are there.  I am now on Ubuntu Xenial.  Yesterday, my Firefox 56 was upgraded to Firefox 57.  Unfortunately (or not), Passwordmaker is no longer supported.  So I installed Passwordmaker Pro.  I have my .rdf file from Passwordmaker.  The information I have is that one can import a passwordmaker.rdf file into Passwordmaker Pro. I imported my passwordmaker.rdf file into Passwordmaker Pro.  I got numerous profiles (257) that seem to be for my individual web sites for which I had created an account in Passwordmaker.  Then I exported the imported profiles using the export function.  The problem is, when I exit Firefox and restart, the saved (or so I thought) profiles are not loaded.  The same 2 profiles (Default and Alphanumeric) are there.  If I import the exported profiles, I have to start over again at each web site, because the master password has to be re-entered.  If I don't remember the exact password length and hashing algorithm I used, I get a different password.  I cannot make heads or tails of this.  Since I no longer have Firefox 56, I cannot see what any of my current passwords are.  Can anyone help?

I might add that when I export the profiles, a new Passwordmaker Pro Profile Data.rdf file is created.  Where is this file supposed to be.  I put it in my current Firefox profile folder.  Maybe it should reside somewhere else in order to be loaded at Firefox startup.

---

### Post by cscj01 on 2017-11-18
I need someone who has used this add-on to give me some help.

---

### Post by sudodus on 2017-11-19
I wish and hope that you will get help with Passwordmaker soon :-)

Otherwise I think you should look for another tool, that can do something similar, and replace it. Have you tried some other password manager?

---

### Post by cscj01 on 2017-11-21
> **sudodus said:**
> I wish and hope that you will get help with Passwordmaker soon :-)

Otherwise I think you should look for another tool, that can do something similar, and replace it. Have you tried some other password manager?

I think I have resolved many of the issues through trial and error.  The part about having my profiles available when I start FF is resolved because it is a bug in the add-on.  You cannot clear history.  If you do the data is wiped and the 2 useless profiles are loaded.  So I had to change my setting.  I am not too happy about that, but the author of the add-on says he is trying to fix that.  We shall see.

I have started looking at Keepass 2.x, but I'm not sure how burdensome it will be to move my 255 web sites into that.  The folks there are saying they will look at the old .rdf file and see if it can be imported.  We'll see where that goes.

In the meantime, I am making it with PasswordMaker Pro, albeit not in a way that was as easy as passswordmaker.  What would be great is for some dear soul to bring passwordmaker up to spec for FF57.  That was a really useful add-on.  Too bad Eric Jung grew weary of supporting it.

Thank you for your comment.  At least I know some folks are listening.

---

### Post by cscj01 on 2017-11-26
I now have PasswordMaker Pro working correctly thanks to the maintainer Peter.  All is well.  I will close this issue.

---

### Post by sudodus on 2017-11-27
Thanks for sharing your solution :-)

---

