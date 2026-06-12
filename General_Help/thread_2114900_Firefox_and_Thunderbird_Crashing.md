---
title: "Firefox and Thunderbird Crashing"
date: 2013-02-11
forum: General Help
---

### Post by lakerssuperman on 2013-02-11
I have an Asus Zenbook Prime running Ubuntu Gnome Remix 12.10.  Everything had been working fine until yesterday.  Now Firefox 18, Thunderbird and Firefox Nightly all crash within a few seconds of starting up follow quickly by the Mozilla error report dialog.  No other programs crash randomly.  I deleted the config files, purged the packages and did and reinstalled, but the problems persists.  Clearly something is wrong with another package that they all rely on, but I am at a loss.  The only major thing I did from when it was working to when it was not was purge Libre Office and then manually download and install Libre Office 4.0 using the debs from the website.  However, I did this on two other machines and have not had an issue with them.

Anyone have any general stuff I might try to before getting into the nitty gritty details?

---

### Post by QIII on 2013-02-11
You might try opening them from the terminal and taking a look at what is reported when they crash.

If you post that back here, someone might see some clues.

Cheers!

---

### Post by vanadium on 2013-02-11
Even though you are not using Unity, the "Unity Desktop Integration" plugin may be installed and active. If that is the case, disabling it will solve the issue. I do not anymore have these crashes since disabling this plugin.

---

### Post by lakerssuperman on 2013-02-11
After several attempts to start it in safe mode, I finally got it working.  Not sure what I did, but Firefox and Thunderbird are both running fine again.  I did disable the Unity plugins.  Also, opening from the terminal didn't give a single error, which I found weird.  Thanks for the help.

---

