---
title: "Translations for Wubi 8.04 are now up in Rosetta"
date: 2008-03-05
forum: General Help
---

### Post by ago on 2008-03-05
Wubi now uses rosetta for translations. Please use the following link to contribute:

[https://translations.launchpad.net/wubi](https://translations.launchpad.net/wubi)

We need translations for the 8.04 version where a few strings were changed. So I would encourage all translators to review their previous work. You can use the web interface directly or upload a po file in rosetta. I will take care of periodically downloading the files and merging them within Wubi. 

Please note that Ubuntu 8.04 deadlines apply. Which means there isn't that much time. 

Please also note that the sister project "umenu" also needs some love. Umenu is the Ubuntu CD menu, i.e. the very first page that is dispalyed when you launch the CD within Windows.  The rosetta page for it will be setup soon. I will give a notification here.

I have unstuck the old thread since it contained outdated info. The link, for reference, is: [http://ubuntuforums.org/showthread.php?t=457362](http://ubuntuforums.org/showthread.php?t=457362)


Thanks a lot to all,

Ago

---

### Post by rmzelle on 2008-03-06
> **ago said:**
> We need translations for the 8.04 version where a few strings were changed. So I would encourage all translators to review their previous work.

...

Please note that Ubuntu 8.04 deadlines apply. Which means there isn't that much time.

Do you know what the deadlines are?

As an aside, I was translating wubi and came across a typo in the English strings:

/home/src/wubi/hardy/src/wubi/english.nsh:55
Writting configuration files... > Writing

---

### Post by ago on 2008-03-06
Thanks will fix them, we are evaluating using some of your text in umenu by the way. The changes are already in bzr but unfortunately wubi string is a bit too long. I was thinking of removing the dual boot stuff and, hopefully, the lack of suspend (which may work after all).

For the schedule see: [https://wiki.ubuntu.com/HardyReleaseSchedule](https://wiki.ubuntu.com/HardyReleaseSchedule)
Note that I will require final translation slightly before that, so that I can have confirmation that the translations are good.

---

### Post by ago on 2008-03-07
This might also be relevant:

[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2008-March/003481.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2008-March/003481.html)

Umenu/Wubi will from now on adhere to string freeze and require a feature exception if any change is needed.

---

### Post by v1cho on 2008-03-08
Hi, can you tell me where I can find the English  version of Wubi that we are currently translating?:confused:
I'm having some problems with understanding the purpose of some strings :/
EDIT: I found it on sourceforge, tanks anyway :)

---

### Post by ago on 2008-03-10
I have been discussing about translations on #ubuntu-translator, the suggestion was made to tighten up translations by allowing access only to ubuntu translator team. I.E. using the same policy that holds for Ubuntu.

I am inclined to follow said suggestion, hence please note that in the future in order to contribute translations to Wubi/Umenu you will need to be a member of [https://translations.launchpad.net/+groups/ubuntu-translators](https://translations.launchpad.net/+groups/ubuntu-translators)

Lupin-translation-team will be dismantled and I encourage members to adhere to the above.

---

### Post by mrv on 2008-03-17
Can we have both umenu and wubi translations synced from Rosetta for the 8.04 beta release? It'd be a good way to receive any possible feedback on translations. Currently umenu seems to lack translations altogether in the code tree.

---

### Post by ago on 2008-03-17
> **mrv said:**
> Can we have both umenu and wubi translations synced from Rosetta for the 8.04 beta release? It'd be a good way to receive any possible feedback on translations. Currently umenu seems to lack translations altogether in the code tree.

Yes, I was about to do that today.

---

### Post by ago on 2008-03-17
> **mrv said:**
> Currently umenu seems to lack translations altogether in the code tree.
A few strings are localized directly within nsis and there shouldn't be any need to change that.

---

### Post by ago on 2008-03-18
Translated wubi is available in: [http://www.wubi-installer.org/devel/minefield](http://www.wubi-installer.org/devel/minefield) rev455+

---

### Post by ago on 2008-03-18
In fact it is unlikely that new translations will land in the beta. But they are in the new builds and will be set as default on wubi main page... So we should have good testing coverage at least for wubi. I will provide stand-alone umenu builds.

---

### Post by mrv on 2008-03-19
> **ago said:**
> Translated wubi is available in: [http://www.wubi-installer.org/devel/minefield](http://www.wubi-installer.org/devel/minefield) rev455+

Hi. It seems at least Finnish (fi) lacks all the tooltip body text translations, with only few exceptions. The title of the tooltip is always translated, but most body texts lack translations. The translation in Rosetta is complete and includes also those text parts.

Accessibility dialog is correctly translated, as seems also with the actual installation stuff as far as I see during short Wine experiment.

---

### Post by ago on 2008-03-19
> **mrv said:**
> Hi. It seems at least Finnish (fi) lacks all the tooltip body text translations, with only few exceptions. The title of the tooltip is always translated, but most body texts lack translations. The translation in Rosetta is complete and includes also those text parts.
Ok I will check and sync that, but I will only be able to release in a few days.

---

### Post by mrv on 2008-03-26
> **ago said:**
> Ok I will check and sync that, but I will only be able to release in a few days.

Has a few days already passed? :) It'd be nice to be able to test with the application fully translated, to see if there are any more issues with the translations etc. (eg. the lenght of translated strings)

---

### Post by ago on 2008-03-26
You can download wubi rev457 from the main download button in wubi-installer.org
I synced translations yesterday
Hopefully everything should be there.

---

### Post by mrv on 2008-03-26
> **ago said:**
> You can download wubi rev457 from the main download button in wubi-installer.org
I synced translations yesterday
Hopefully everything should be there.

Hi, thanks. Unfortunately the same strings are broken as before - almost all tooltip descriptions are not translated, the only exception is the language selection. So, it might be a problem of the code not using the translations that are there (since everything is translated in Rosetta).

Also, please tell when/where umenu translations are testable.

---

### Post by ago on 2008-03-26
> **mrv said:**
> Hi, thanks. Unfortunately the same strings are broken as before - almost all tooltip descriptions are not translated, the only exception is the language selection. So, it might be a problem of the code not using the translations that are there (since everything is translated in Rosetta).

Can you please double check the relevant po files within wubi source code and compare with the ones downloaded from rosetta?

[https://code.launchpad.net/~ubuntu-installer/wubi/hardy](https://code.launchpad.net/~ubuntu-installer/wubi/hardy)

> Also, please tell when/where umenu translations are testable.
Probably tonight/tomorrow.

---

### Post by ago on 2008-03-26
To test umenu download the following file and run with the argument "--debug"
Ignore the message boxes.

[http://wubi-installer.org/devel/test/umenu-8.04-rev24.exe](http://wubi-installer.org/devel/test/umenu-8.04-rev24.exe)

---

### Post by mrv on 2008-03-27
wubi: the fi.po in the bzr is identical with Rosetta's PO file, with the exception of filenames/line numbers. That is, all 87 messages are translated.

umenu: Untranslated strings also here. On the front page, button texts are translated but none of the descriptions. On the full instalation page (reboot choices), the title and the selectable items are translated, but not the three-line description text.

---

### Post by ago on 2008-03-27
It's probably a bug in the helper scripts I will look at it tonight

---

### Post by ago on 2008-03-27
> **mrv said:**
> wubi: the fi.po in the bzr is identical with Rosetta's PO file, with the exception of filenames/line numbers. That is, all 87 messages are translated.

umenu: Untranslated strings also here. On the front page, button texts are translated but none of the descriptions. On the full instalation page (reboot choices), the title and the selectable items are translated, but not the three-line description text.

Should have been fixed. Thanks for pointing it out.

Please see wubi rev 458 (minefield) and umenu rev 25 (/devel/test)

---

### Post by mrv on 2008-03-28
> **ago said:**
> Should have been fixed. Thanks for pointing it out.

Please see wubi rev 458 (minefield) and umenu rev 25 (/devel/test)

Thanks a lot! I tested 458 and 459 of Wubi, and both worked now fluently. I couldn't find umenu rev 25 ([http://wubi-installer.org/devel/test/](http://wubi-installer.org/devel/test/)), but probably if it was the same bug it's indeed fixed there already.

Thank you for your great work with these programs.

---

### Post by ago on 2008-03-28
umenu is up now

---

### Post by mrv on 2008-03-28
> **ago said:**
> umenu is up now

...and works great regarding translations. Thanks.

---

### Post by ago on 2008-04-15
I have noticed now that NSIS only has support for a subset of lanuguages. I am getting Rosetta translations for languages that are not in the NSIS list. It is too late now for me to change NSIS behaviour and make it support the extra languages. So some work from translators unfortunately will not be available, I am really sorry about that and I will try to improve support after final for the stand-alone product so that all translations can be used.

---

