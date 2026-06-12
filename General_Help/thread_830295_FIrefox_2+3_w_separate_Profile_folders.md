---
title: "FIrefox 2+3 w/ separate Profile folders"
date: 2008-06-15
forum: General Help
---

### Post by swegner on 2008-06-15
Hi,

With Firefox 3 so new, many of my extensions aren't compatible yet.  Rather than "hacking" the extensions to force compatibility, I prefer to install firefox 2 side-by-side with Firefox 3, and run Firefox 2 when I need these essential extensions.

To separate the two versions, I've created different Firefox profiles for each.  My "default" profile is the one I used for Firefox 3, and I also have a "ff2" profile for Firefox 2.  The "ff2'"profile contains all of my essential extensions, and never loads Firefox 3.

When I switch back-and-forth between FF2 and FF3, I need to launch it with the command
```
firefox -ProfileManager
```and select the correct profile.  However, sometimes I will forget to use this when I switch back to Firefox 3, and as a result, Firefox 3 performs an automatic upgrade on the "ff2" profile.  It checks each of the extensions for compatibility, and disables the ones that aren't compatible with Firefox 3.  Moreover, when I open the profile again in Firefox 2, the extensions are disabled, and can't be re-enabled.

I'm looking for some way to avoid this issue.  Is there any way to completely separate the Firefox directories for the two versions-- perhaps ~./mozilla/firefox and ~/mozilla/firefox-2.  I think this would cause the profile list to be different and not overlap.  Note that I'd also like to accomplish something like this without installing from source or any other "hack" that might cause conflicts down the road.

Scott

---

### Post by UNOwen on 2008-06-15
This is what I did when I found myself in the same situation.

I first created a launcher for Firefox 2 and one for Firefox 3. I Right clicked on one of the launchers and selected **Properties** and added the following to the "Command" line.

```
-P "name of profile"
```

In your case the "Command" lines should look like the following.

For Firefox 2:

```
firefox-2 %u -P "ff2"
```

For Firefox3:

```
 firefox %u -P "default"
```

Clicking on one of the launchers will invoke the profile manager and tell it to use the specific profile that you have indicated on the command line. (If the profile manager still pops up make sure the "Don't ask at startup" item is checked.)

Hope this helps.

---

### Post by swegner on 2008-06-15
Hi UNOwen,

Thanks for the response.  This sounds like it'll work pretty well-- I can just edit the entries already present in the main menu.  Although, when Firefox receives updates, will the menu entries been overwritten?

Also, I sometimes launch Firefox from the command line, which this won't quite help.  I guess I'll just need to remember to use the profile parameters on the command line.

Thanks again,

Scott

---

