---
title: "email interaction in Firefox"
date: 2008-06-20
forum: General Help
---

### Post by jaimedavila on 2008-06-20
Hello all,

The beginning of the description of this problem might sound familiar, and I do know that there are other threads dealing with what sounds to be the same problem, but read on for some strange details.

Probably since I switched to ubuntu several years ago I have had problems with mailto links and the "Send Page" option in firefox. If I click on a mailto link, or select "send page," nothing happens. I would like thunderbird to handle both of those. I have network.protocol-handler.app-mailto set to /usr/bin/thunderbird, which is where my thunderbird executable lives. network.protocol-handler.external.mailto is set to true. In an effort to debug the problem, I have set network.protocol-handler.warn-external.mailto to true, but when I click on a mailto link no warning comes up. My prefs.js file confirms that these settings are stored. 

I am using KDE, and thunderbird is set as the default email client. Just for good measure, I edited the gnome setting with gconf-editor, and /desktop/gnome/url-handlers/mailto is set to thunderbird. I have had this problem under both gnome and kde. I just ran firefox with all extensions removed, and still have the same problem.

Now, here comes probably the cutest thing. When I installed ubuntu 8.04, it was working just fine. "Excellent!" I said; the problem was solved with the distro update. Well, just recently, when I updated to Firefox 3, the problem came back. So, strangely enough, things were OK with firefox 3 candidate beta 5, or whatever was the default before version 3. 

I have searched, long, deep, and broad for a solution, with no luck. 

Any thoughts?

Thanks in advance,

Jaime

---

### Post by manfer on 2008-06-20
Mine works perfectly. I checked my about:config to tell you if I see some differences. This is what I can tell you:

[LIST]
[*]No network.protocol-handler.app-mailto. Maybe this is just handle by configured system default mail application. In ubuntu that can be configured in:
[/LIST]

[INDENT]System->Preferences->Preferred Applications

or if you configure it with gconf-editor as you say the entrie /desktop/gnome/url-handlers/mailto must look like:

command -> thunderbird %s
enabled -> on
needs_terminal -> off[/INDENT]

[LIST]
[*]network.protocol-handler.expose.mailto -> false

[*]network.protocol-handler.external.mailto -> true

[*]network.protocol-handler.warn-external.mailto -> false
[/LIST]

Don't know if more things are needed.

---

### Post by jaimedavila on 2008-06-20
Thanks for the reply. I checked all of those variables, and they are all set as in your system. I even erased the entry for the mailto handler, and still no luck.

The mystery continues...

---

### Post by manfer on 2008-06-21
Could you look if something appears on error console on firefox when you click on a mailto link? You can open error console under tool menu.

You can try this one too. Close all firefox windows opened and run it from terminal:

prompt:~$ **firefox**

now click on a mailto link and look what appears on terminal.

Maybe one of those reports some useful information to track what is going wrong.

---

### Post by jaimedavila on 2008-06-21
I don't get any error messages on a terminal when I start firefox from there. 

On the error console, when I right-click and select "send link" I get 

Error: uncaught exception: [Exception... "Component returned failure code: 0x80004005 (NS_ERROR_FAILURE) [nsIExternalProtocolService.loadUrl]"  nsresult: "0x80004005 (NS_ERROR_FAILURE)"  location: "JS frame :: chrome://browser/content/browser.js :: anonymous :: line 5304"  data: no]

I don't get any error messages on the error console when I click on a mailto link.

I'm googling that error message, and will post back anything I find.
Thanks,

Jaime

---

### Post by jaimedavila on 2008-06-21
OK. Success. Here is what I found.

Googling nsIExternalProtocolService.loadUrl pointed me to this thread:
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/222944](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/222944)

A lot of the advice there I had already tried, but the one I hadn't, which did the trick, was erasing the mimeTypes.rdf file from the firefox preference directory. Upon restarting firefox, when I clicked on a mailto link, firefox asked me which program I wanted to open. Be warned, though, that as far as I can tell firefox lost other "definitions" of what helper applications to use. For example, I had to re-tell it how to open pdf files.

Still, success as far as I'm concerned. Thanks for pointing me to the error console output.

---

### Post by manfer on 2008-06-21
Nice you solved it.

Now that you pointed what was going wrong, I just wonder if you had to delete that file (erasing all mimeTypes as you mention) or it would be just enough to try to configure it on preferences.

Under firefox preferences (edit->preferences) in the programs tab all those mimeTypes can be configured. There's one for mailto and maybe that was the only thing you needed to change, pointing it to thunderbird.

But as you said you have just tried some solutions with no luck, maybe you had tried that already. It would be nice if you can confirm if you tried this before going with the more drastic solution implying deletion. I suggest someone with same problem try first to solve it in the preferences and not deleting that file (probably it works and no need to reconfigure the other mimeTypes).

---

### Post by jaimedavila on 2008-06-21
My Edit/preferences/application did not have anything listed in it when the problem began, and still doesn't, even after telling it how to open mailto's and pdf files, even though both are working. Media files do play correctly, playing with mplayer and its plugin. I do recall that it used to have stuff listed in previous versions of firefox/ubuntu combinations. Go figure.

---

### Post by manfer on 2008-06-21
Sorry for that Programs tab in previous message. For what you say it must be Applications tab ( guessing english names from spanish version :-) )

It is incredible so many differences. Probably the update from version 2 to version 3 is not working so fine. If I were you and if you have time to do it, maybe it wouldn't be a bad idea to do a totally fresh installation of firefox 3, uninstalling and even deleting profile (doing the backup of bookmarks before) and then installing again.

---

