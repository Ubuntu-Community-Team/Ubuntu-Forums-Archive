---
title: "Firefox locks up over so many sites"
date: 2006-12-07
forum: General Help
---

### Post by scuzzo84 on 2006-12-07
Man firefox has been really pissing me off on dapper for a while. I have 1.5.0.8 and here and there I have 5 tabs open, I open a 6th site and it will lock up and I have to kill FF and then re open all my sites. Its such a damn pain. Its been doing it mainly on trendy sites with ads, flash stuff and maybe java crap. Im guessing it due to one of those causing FF to act lame. 

Anyone have this similar issue? And does anyone know if FF has a plugin to allow it to act like opera, how opera closes with its tabs, you reopen opera and it loads that tabs up?

thanks

---

### Post by wpshooter on 2006-12-07
I don't know, but is it possible that this is a problem with lack of memory and/or no swap partition ?

Is it possible that you need to change a parameter in the tab section of FF preferences ?

---

### Post by rpkehoe on 2006-12-07
I would suggest opening up your system monitor, and take a look at your ram and swap usage when you have 5 tabs open, and see what happens when you open the sixth.  I agree with wpshooter that this is most likely a ram or swap issue.  How much ram do you have, and what size is your swap partition?

---

### Post by drphilngood on 2006-12-07
> **scuzzo84 said:**
> Man firefox has been really pissing me off on dapper for a while. I have 1.5.0.8 and here and there I have 5 tabs open, I open a 6th site and it will lock up and I have to kill FF and then re open all my sites. Its such a damn pain. Its been doing it mainly on trendy sites with ads, flash stuff and maybe java crap. Im guessing it due to one of those causing FF to act lame....

Install this FF extension and it will allow you to block all Java and Flash until you want to enable it for a site with one click:
[NoScript]("https://addons.mozilla.org/firefox/722/")

> **scuzzo84 said:**
> ...Anyone have this similar issue? And does anyone know if FF has a plugin to allow it to act like opera, how opera closes with its tabs, you reopen opera and it loads that tabs up?...

This extension allows you to select an option to have it reload all tabs upon opening or even have it ask you if you want it to reopen your tabs.  ¨It also includes a full-featured session manager with crash recovery that can save and restore combinations of opened tabs and windows.¨


[Tab Mix Plus]("https://addons.mozilla.org/firefox/1122/")

Hope this is what you were looking for.

---

### Post by rrwo on 2006-12-07
Is it due to a bad plugin?   Try disabling all of your plugins and visit those sites.  Then one by one enable a plugin and check the sites to see if one of them is causing the problem.

I used to have that problem with Adblock (though the latest version of Adblock seems to work fine on FF 2.0).

---

### Post by strabes on 2006-12-07
You can also install the firefox extension called [Session Manager](https://addons.mozilla.org/firefox/2324/) which will give you the option to restore all your tabs on startup. I would also recommend installing extensions like [adblock plus](https://addons.mozilla.org/firefox/1865/) and an [adblock filterset blacklist](https://addons.mozilla.org/firefox/1136/). You should also consider installing the firefox flash 9 plugin [here](http://labs.adobe.com/technologies/flashplayer9/). Unzip the file and put the .so in your /usr/lib/firefox/plugins directory to install it globally for all users.

---

### Post by hadiriazi on 2006-12-07
> **scuzzo84 said:**
> Man firefox has been really pissing me off on dapper for a while. I have 1.5.0.8 and here and there I have 5 tabs open, I open a 6th site and it will lock up and I have to kill FF and then re open all my sites. Its such a damn pain. Its been doing it mainly on trendy sites with ads, flash stuff and maybe java crap. Im guessing it due to one of those causing FF to act lame. 

Anyone have this similar issue? And does anyone know if FF has a plugin to allow it to act like opera, how opera closes with its tabs, you reopen opera and it loads that tabs up?

thanks
I do have the same problem with FF2 but the good thing is that the option your looking for is set by default on FF2. It asks you wither you want to resume sessions or start a new session, if you choose resume session you will have all your tabs again,

I suggest you to download and install FF2 :)

---

### Post by odzx on 2007-01-12
does anyone know if FF has a plugin to allow it to act like opera, how opera closes with its tabs, you reopen opera and it loads that tabs up?

thanks[/QUOTE]

to make FF open last session automatically (like opera):
type "about:config" in the address bar. then change "browser.startup.page" to 3.
have a look here for more tweaks:
[http://pansapiens.blogspot.com/2006/10/firefox-20-installation-and-tweaks.html]("http://pansapiens.blogspot.com/2006/10/firefox-20-installation-and-tweaks.html")

---

