---
title: "Weird problems with Flash and Ubuntu"
date: 2007-05-02
forum: General Help
---

### Post by dpmccoy on 2007-05-02
I upgraded from Kubuntu Edgy to Kubuntu Feisty last month.  I initially upgraded to Kubuntu after my initial Edgy install last year  I had a lot of trouble with Knetworkmanager and my wireless connection [using Ndiswrapper & Netgear WGV311v3 card], so I switched over to Ubuntu yesterday.  My wireless worked fine in Edgy.
I'm running into a problem with Firefox and Flash that I did not experience under Kubuntu.  For example, when I visit [http://chicago.whitesox.mlb.com/](http://chicago.whitesox.mlb.com/), the main Flash portion on the left side is covered in white, along with the video highlights immediately to the right of that window.  At [http://mlb.mlb.com](http://mlb.mlb.com), the main Flash portion of the screen that cycles through the games and results doesn't display the linescore.  Gameday won't load past 40% either.  I can watch the MLB.TV games using the Mplayer-plugin, however, with no problem.
I went to [http://www.huffingtonpost.com](http://www.huffingtonpost.com) to read a story, and when I select "Share/Comment", the browser hangs on loading an.tacoda.net.  This problem didn't happen when using Firefox under Kubuntu.  [Http://www.cnn.com](Http://www.cnn.com) took a long time to load this morning, but it finally showed up.
I have the latest Flash-nonfree plugin loaded, and it shows up under about:plugins.  

I am at work right now, but I can enclose screen shots at lunchtime.  

Does anyone have a fix?  Thanks for any help.

---

### Post by Efwis on 2007-05-02
a screenshot would be helpful, Also what version of FF is it using? I'm using FF 2.0.0.3 from Mozilla and nothing wrong is showing up at the links you posted. It may be related to using the default installed FF in ubuntu instead of using the one from Mozilla.

If I recall correctly, the default Ubuntu installs of FF have had nothing but problems. Thats why the first thing I do is install the version from Mozilla.

---

### Post by dpmccoy on 2007-05-02
Thanks for the reply.  I'll enclose the screenshots when i go home for lunch, and will verify the version of Firefox as well.

My biggest question is why would I have problems simply from switching from KDE to Gnome, when Firefox remains the constant?  

Will follow up...

---

### Post by Efwis on 2007-05-02
The difference is because by default KDE doesn't install or use FF. Where Gnome does. When you installed FF in KDE did you get it from Mozilla or from the repos?

---

### Post by dpmccoy on 2007-05-02
I found the problem, and I give thanks to you for jogging my memory.

I can't remember specifics, but after I installed Edgy last year [clean install], I *think* that I downloaded the new version of Firefox from Mozilla.  This left me with the following directories: /usr/lib/firefox and /usr/lib/mozilla-firefox.  I don't know which one is the one I installed.

I examined the link to Firefox in Gnome [in the quicklaunch bar], and changed it to point to the /usr/lib/mozilla-firefox/firefox file.  Voila!  Now the problems are fixed.

Thanks for pointing me in the right direction!

---

### Post by Efwis on 2007-05-02
glad I could help.

---

