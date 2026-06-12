---
title: "No filetype association after firefox update"
date: 2005-07-22
forum: General Help
---

### Post by RikoW on 2005-07-22
Hi everybody,

this morning I upgraded firefox with the Ubuntu Update Manager to Ubuntu package 1.0.2 MFSA2005-56. I read already many complains in the forum, that certain things don't work properly or that firefox crashes all the time.

Well, that problem I don't have. However, after the upgrade, all the file type association usually listed under Preferences -> Downloads -> File Types have disappeared. As a result, the browser does not open pdf, media files etc anymore.

Usually, if encountering an unknown filetype, firefox would pop up a window asking you what to do with it (save, open with application). But that does not happen anymore with the type already defined. Firefox loads, claims it's done loading but nothing happens. Unfortunately, you cannot enter applications by hand in the File Types list under Preferences. So I have no idea, how to get it back. I already removed the mimeTypes.rft in the profile directory and started firefox again, but no change.

Does anybody have any idea to get the file type association back or at least force firefox to ask what to do with it?

Thanks and cheers,

     Riko

---

### Post by RikoW on 2005-07-22
ok, I actually planned to downgrade firefox back to the previous.
Thinking to do it in a clean way, removed the upgraded version, which also removed ubuntu-desktop .... wanting the desktop back, forced me to install firefox back ... not quiet what I had in mind :)

Anyway, after doing this cycle things seems to work as usual again, even though I still don't see the file types in the preferences anymore, the correct application is opened.

Let's hope it stays like that :)

Just thought, I let you know about this development for the record.

Cheers,

     Riko

---

### Post by bpilgrim1979 on 2005-07-22
Riko, how did you install the older version (before the recent update) of firefox?

I see that apt-get -s remove mozilla-firefox also removes the ubuntu-desktop package.

Could you give explicit commands?  Thanks!!

---

### Post by RikoW on 2005-07-23
Hi!

I in fact did not remove firefox. I deinstalled and reinstalled because of the ubundu desktop dependency. But you should be able to downgrade by overwriting the currebntly installed version. Check this post for example:

[http://www.ubuntuforums.org/showpost.php?p=265471&postcount=11](http://www.ubuntuforums.org/showpost.php?p=265471&postcount=11)

Also, you might be able to force the firefox version in synaptics. Select the firefox package, go to the Package Menue and click on 'Force Version'. Now you can select the old firefox versiob as well from the Hoary repository while the most recent one is in Security.

Cheers,

          Riko

---

