---
title: "renamed cryptkeeper folder now can't open. Uh oh!"
date: 2012-10-21
forum: General Help
---

### Post by Advait on 2012-10-21
Hi All,

I just downloaded the latest version of CryptKeeper. I then created a CryptKeeper folder and copied some files into it. I tested it yesterday and it was working fine. Today I renamed the folder and now CryptKeeper says it can't find it. Uh Oh! Bad news! Does simply renaming a CryptKeeper folder make it un-openable? Any way to fix this? Thanks,

Advait

---

### Post by Advait on 2012-10-21
OK, looks like I fixed it. I had misspelled when I renamed. I finally remembered the original name and entered that and then it opened with CryptKeeper. Now I can open it.

Whew!

Lesson learned: Never rename a CryptKeeper folder!! :shock:

Out of curiosity, if a CryptKeeper folder does get renamed and I forget the original name, is there a way to fix? Or impossible to fix without original name?

Thanks,

Advait

---

### Post by varunendra on 2012-10-21
> **Advait said:**
> Out of curiosity, if a CryptKeeper folder does get renamed and I forget the original name, is there a way to fix? Or impossible to fix without original name?

Not familiar with cryptkeeper, but almost all the applications store the 'absolute paths' to the directories where they have to work. They store this info in their configuration files which are usually stored in the '.config' directory of the user (if the application & its scope is user specific), or in the /etc directory if the settings are system-wide. Some apps also store their settings in /opt or /usr/local, or even a few other places, but ~/.config and /etc are the first place to look for configuration files.

Once the configuration file is found, you can simply edit it on a text editor to make desired changes.

---

### Post by Advait on 2012-10-22
> **varunendra said:**
> Not familiar with cryptkeeper, but almost all the applications store the 'absolute paths' to the directories where they have to work. They store this info in their configuration files which are usually stored in the '.config' directory of the user (if the application & its scope is user specific), or in the /etc directory if the settings are system-wide. Some apps also store their settings in /opt or /usr/local, or even a few other places, but ~/.config and /etc are the first place to look for configuration files. Once the configuration file is found, you can simply edit it on a text editor to make desired changes.

Ahhh... This is excellent info! I'm still pretty new to Linux and little tips like this help me a lot. :)  Thanks! I'll save this and keep in mind when I have any problems in the future.

Cheers,

Advait

---

### Post by varunendra on 2012-10-22
You're welcome buddy !:)
Glad you found it helpful.

---

