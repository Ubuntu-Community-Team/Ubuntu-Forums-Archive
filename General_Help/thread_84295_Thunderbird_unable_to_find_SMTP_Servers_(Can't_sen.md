---
title: "Thunderbird unable to find SMTP Servers (Can't send mail)"
date: 2005-10-30
forum: General Help
---

### Post by Doc.Caliban on 2005-10-30
Hello,

I have Thunderbird up and running with a profile copied over from my XP Install.  Everything works except sending mail.

I have several accounts in this profile and each has it's own SMTP server.

No matter which account I try to send from, the process never gets past "Looking up <server name>".

I can ping every SMTP server by name, so it's not a network issue.

I have deleted and redefined the SMTP server entries in the profile.

Any further ideas other than recreating the entire profile from scratch (Thing don't work!  Hit thing with hammer!), I'd appreciate the input.

-Doc

---

### Post by kperkins on 2005-10-30
Copying profiles in Thunderbird always seems to cause problems, esp. between OSs. 2 ideas:
1) I assume that you don't use secure authentication--make sure that isn't checked under sever settings.
2)Check your password cache (Edit > Preferences > Advanced > Saved Paswords > View Saved Passwords) and try removing them all and reentering them.

---

### Post by Doc.Caliban on 2005-10-30
[QUOTE=kperkins]Copying profiles in Thunderbird always seems to cause problems, esp. between OSs. 2 ideas:
1) I assume that you don't use secure authentication--make sure that isn't checked under sever settings.
2)Check your password cache (Edit > Preferences > Advanced > Saved Paswords > View Saved Passwords) and try removing them all and reentering them.[/QUOTE]


kperkins, thanks for the tips.

I deleted all saved passwords as per your instructions which resolved the issue!  Many thanks!

Getting Thunderbird working was obviously a big milstone in my 48-hour old migration from XP to linux; thank you for helping me along.

The last hurdle is Skype, and then I'll be where I need to be for exclusive daily use of Ubuntu instead of XP.

-Doc

---

### Post by kingsidy on 2005-10-30
One idea is to reconfigure the settings for the email accounts from scratch. 
Some of those email accounts do not support pop3 unless you pay for them or use programs like ypops. 

I also think that thunderbird uses one smtp server to send mail no matter how many email accounts you have cofigured. It only uses one at a time.

---

### Post by Doc.Caliban on 2005-10-30
[QUOTE=kingsidy]One idea is to reconfigure the settings for the email accounts from scratch. 
Some of those email accounts do not support pop3 unless you pay for them or use programs like ypops. 

I also think that thunderbird uses one smtp server to send mail no matter how many email accounts you have cofigured. It only uses one at a time.[/QUOTE]


Hi kingsidy,

This is a profile that was working "as-is" in XP:  all the server settings are known good.

As an FYI if you're interested, you can define multiple SMTP servers in Thunderbird and set each account to use it's own.  In the server properties for the account, click the "Advanced..." button at the lower right and then click the SMTP tab in the resulting window.  (I always thought that was a bad place for the "Advanced..." button because it looks like it will give you advanced settings for the "Empty trash folder on exit" option.

-Doc

---

