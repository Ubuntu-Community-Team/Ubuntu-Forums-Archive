---
title: "After Swiftfox upgraded to 3.0, cannot switch default browser back to Firefox"
date: 2007-12-08
forum: General Help
---

### Post by tak1150 on 2007-12-08
My swiftfox upgraded to 3.0b, which is allright, but the add-ons / plugins I need are not yet working in 3.0b. So now I would rather use Firefox 2.0. However, I cannot switch the default browser to Firefox for some reason.

I have already tried "Preferred Application" thing to choose Firefox. I have also uninstalled swiftfox. Yet other apps don't recognize Firefox as the default browser. I have also deleted ~/.mozilla/firefox-3.0/.

Any helps is appreciated.

---

### Post by crimesaucer on 2007-12-08
> **tak1150 said:**
> My swiftfox upgraded to 3.0b, which is allright, but the add-ons / plugins I need are not yet working in 3.0b. So now I would rather use Firefox 2.0. However, I cannot switch the default browser to Firefox for some reason.

I have already tried "Preferred Application" thing to choose Firefox. I have also uninstalled swiftfox. Yet other apps don't recognize Firefox as the default browser. I have also deleted ~/.mozilla/firefox-3.0/.

Any helps is appreciated.

Have you tried the Firefox "Nighty Tester" tools extension?

download/install: [http://www.oxymoronical.com/web/firefox/nightly](http://www.oxymoronical.com/web/firefox/nightly)

After you add this, and then restart... you will see an option in your Add-ons app that says, "Make all extensions compatible", (or something like that)... click it, and restart. Most add-ons will work now, some won't. (like the Ubuntu Forums Menu)

---

### Post by tak1150 on 2007-12-08
> **crimesaucer said:**
> Have you tried the Firefox "Nighty Tester" tools extension?

download/install: [http://www.oxymoronical.com/web/firefox/nightly](http://www.oxymoronical.com/web/firefox/nightly)

After you add this, and then restart... you will see an option in your Add-ons app that says, "Make all extensions compatible", (or something like that)... click it, and restart. Most add-ons will work now, some won't. (like the Ubuntu Forums Menu)

Thanks for replying. The add-ons that I really need but are not supported for 3.0b are 1) Greasemonkey 2) FEBE 3) Ubuntu Forums Menu. And 3.0b seems unstable when it comes to JAVA sites that I need to use for my work.
So I'm leaning towards going back to Firefox 2.0 rather than trying to make things work in 3.0b.
But I'll keep your suggestion in mind if I decide to go with 3.0b. Thanks.

Tak

---

### Post by crimesaucer on 2007-12-08
> **tak1150 said:**
> Thanks for replying. The add-ons that I really need but are not supported for 3.0b are 1) Greasemonkey 2) FEBE 3) Ubuntu Forums Menu. And 3.0b seems unstable when it comes to JAVA sites that I need to use for my work.
So I'm leaning towards going back to Firefox 2.0 rather than trying to make things work in 3.0b.
But I'll keep your suggestion in mind if I decide to go with 3.0b. Thanks.

Tak

Well, I know that the Ubuntu Forums Menu won't work. As for the other 2, I'm not sure. 


I do know that the "Stylish" add-on works with the "Nightly Tester Tools", and Stylish and GreaseMonkey pretty much use a lot of the same scripts. 


And FEBE should only matter if you're changing to a new Firefox profile and need your backed up extensions... (bookmarks can be backed imported through the old "bookmarks.bak" file in your default profile, or with the html file in the bookmarkbackups folder in your profile.) Same thing with cookies and pref.js...



Also, you said that you upgraded your "Swiftfox"... I don't know how it is on your computer, but for me, Swiftfox installs in my **[COLOR="Red"]/opt[/COLOR]** folder, and it always keeps a copy of my **[COLOR="Red"]Swiftfox.old[/COLOR]** in there, and that should be your old version of **[COLOR="Red"]Swiftfox.old[/COLOR]**.... and that means that your **[COLOR="Red"]~/.mozilla/firefox/qwe4rtyu.default[/COLOR]** profile will still have all of your save extensions from before, the same bookmarks, the same cookies, and the same userChrome.css prefernces as well as all of your about:config settings in your pref.js

---

