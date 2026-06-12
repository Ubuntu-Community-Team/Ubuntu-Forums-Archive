---
title: "Thunderbird upgrade loses email"
date: 2008-04-26
forum: General Help
---

### Post by pablo88 on 2008-04-26
Hi -

I upgraded recently to 8.04. Everything went fine except some of the apps, including Thunderbird, ended up with changed, crappy fonts. I decided to upgrade Thunderbird hoping that would solve the font problem.

Using synaptic I searched for Thunderbird and found it, albeit without it being shown as already installed, which it was. So I ticked the box, applied the upgrade and got it.

Then, when I open up Thunderbird, I see that the font situation is better but, all my email account settings are lost (except oddly for one or two accounts) but much more irksome, my entire address book(s) have vanbished.

Could anyone kindly point me in the right direction as to where I may be able to track down where the files containing the address book in particular can be found?

Also, whilst I'm at it, I still find that the fonts on Opera and Skype have reverted back to something crappy. Prior to upgrading to 8.04 I had installed Tahoma and had it working on all apps. Any answers on that one?

Pablo

---

### Post by ludovicc on 2008-04-26
I hope that you did a backup of your home/ folder before upgrading... 

Thunderbird should store your email contacts in a file called abook.map. Look in ~/.mozilla-thunderbird, there should be a folder called [random chars].default, your file should be there. But it's possible that the upgrade of thunderbird erased your old data. You may be able to recover your contacts if you did before a copy of the thunderbird folder, or if you have a backup of your home folder somewhere.

If you want to avoid such problems in the future, software is never perfect, so the best solution is to have backups, and to duplicate your information. For my contacts, I use the plaxo.com Thunderbird add-on which synchronises all my contacts beween Plaxo and Thunderbird.

---

### Post by pablo88 on 2008-04-26
Hi ludovicc -

Thks for your help. Guess I'm stuffed. I can't be bothered with backups, so I pays the price. Anyway, I didn't like most of the people in my address book anyway. Time to get some new friends.

Pablo

---

### Post by ludovicc on 2008-04-26
:lolflag:

---

