---
title: "Anti-spam in Evolution"
date: 2007-10-23
forum: General Help
---

### Post by val67 on 2007-10-23
Combing the forums, but still not clear:

using Gutsy, how do I enable anti-spam filtering?

Already installed spamassassin plugin, enabled the plugin in Evolution, but still receiving spam.

I think this is a major issue and has to be addressed urgently, unless I am missing something obivous here ...

---

### Post by yostral on 2007-10-23
I enabled and use bogofilter and it works very well.

---

### Post by val67 on 2007-10-23
please detail how did you setup bogofilter.

I did install it, checked the plugin in Evolution and set the Junk option to use bogofilter.

Still does not filter out messages that I marekd as Junk. 

How do i train bogofilter? Does it train by itself?

My test was:

mark one mail as junk, and then i expected all other mails coming from the same source to be marked as junk automatically. But it does not happen so.

Thanks

---

### Post by yostral on 2007-10-24
Bogofilter doesn't work with address.

I installed bogofilter, told Evolution to use it and unchecked Spamassasin in the plugin window.

At the beginning it doesn't really filter... You have to "teach" it. But after few days, no more problem. It filters everything better and better.

But at the beginning  too, you have to verify the junk folder, to see if it didn't filter a non-junk email... it has to learn.

I reinstalled Gutsy one not even one week ago, and now it filters hundreds of mails every day with only very few errors.

---

### Post by tassoman on 2007-10-25
After upgrading to Gutsy spam checks are not parsed by bogofilter while being in Feisty it did with bogofilter

---

### Post by val67 on 2007-10-25
So does bogofilter actually work or not in Evolution?

To me it seems to not filter nay spam after ~ 4days of using it.:confused:

---

### Post by yostral on 2007-10-25
To me it works perfectly...

---

### Post by val67 on 2007-10-25
did you have to define any filters?

---

### Post by yostral on 2007-10-25
As I told you, nothing special. I choosed bogofilter in the combobox as spam filter. I unchecked spamassassin in the plugin window... and that's all.

---

### Post by tassoman on 2007-10-26
Yepp there are new configs to do in the Preferences panel must be selected because for Fiesty upgraders all settings are empty.

---

