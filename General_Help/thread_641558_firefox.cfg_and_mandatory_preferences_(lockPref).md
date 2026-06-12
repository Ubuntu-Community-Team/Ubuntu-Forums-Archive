---
title: "firefox.cfg and mandatory preferences (lockPref)"
date: 2007-12-15
forum: General Help
---

### Post by ekimus on 2007-12-15
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/19033](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/19033) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi,

trying to get mandatory preferences to work. Apart from the firefox.cfg below I also placed a file in /usr/lib/firefox/firefox.cfg (the original was some binary file, no idea what to use to create this format).

However none of the settings get applied. Upon deleting the user.prefs file from my profile the settings in all.js get copied over but I really need some mandatory settings.

I'm on 7.10 and found [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/19033](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/19033) it may be related but I'm not quite sure about that.

Any hints are welcome.

thanks
martin

```

#
$ pwd
/usr/share/firefox/greprefs

$ grep general.config *
all.js:pref("general.config.obscure_value", 13); // for MCD .cfg files
firefox.ubuntu-prefs.js:pref("general.config.filename", "firefox.cfg");
mozilla.txt://lockPref("general.config.filename", "firefox.cfg");

$ cat firefox.cfg
//
ybpxCers("argjbex.cebkl.glcr", 4);
ybpxCers("oebjfre.fgneghc.ubzrcntr", "uggc://sbbone.pbz");

PLAINTEXT:

lockPref("network.proxy.type", 4);
lockPref("browser.startup.homepage", "http://foobar.com");

# pwd
/usr/lib/firefox

file firefox.cfg*
firefox.cfg:      ASCII C++ program text
firefox.cfg.dist: data


```

---

### Post by ekimus on 2007-12-17
[https://help.ubuntu.com/community/FirefoxMandatoryPreferences](https://help.ubuntu.com/community/FirefoxMandatoryPreferences)

---

