---
title: "Tomboy Reminder addin"
date: 2007-12-30
forum: General Help
---

### Post by cairnsww on 2007-12-30
This is a strange one. Reading the latest Full Circle i was inspired by the article by Sudev Barar to retry Tomboy. It is certainly more useful than I thought. However, the article suggests a plugin called "Reminder" that certainly looks useful. The trouble is that the article seems to have hit a discontinuity at this point because the instructions for installation are either missing or meaningless. It suggests using a menu option for a plug-in folder that simply does not exist.

So I Googled it and found other suggestion like simply moving the downloaded dll into the /.tomcat/Plugin folder. The trouble with that advice is that the folder does not exist either. I tried creating one, but that did not help. I tried putting it in the addin folder but that doesn't help either.

No other advice. Some poor guy sent a message with the same problem  to the development forum in September, but there are no replies.

How do I add a plug-in to Tomboy under Ubuntu 7.10?

Thanks

---

### Post by ubukool on 2007-12-30
Hi,

You might find this useful:

[http://raphael.slinckx.net/blog/projects/tomboy-reminder-plugin](http://raphael.slinckx.net/blog/projects/tomboy-reminder-plugin)

:)

Also, .dll implies a windows operability.  I understand that Tomboy is also available on windows which probably explains that instruction.  The plugin folder can be found in the .tomboy folder in your /home directory.  Maybe you don't have a folder because you haven't installed any plugins.  You can rectify that by going to 'edit/preferences' and then clicking the 'add-ins' tab.  You can then select what add-ins you want to install.

---

### Post by cairnsww on 2007-12-30
Not particularly - been there already. Does not answer my question of how to install the plug in.

---

### Post by ubukool on 2007-12-30
okay, I'll try and install the plugin and let you know how I get on.  I could do with a few reminders myself! :)

---

### Post by ubukool on 2007-12-30
Hi,

This took me a while because I first tried to compile it and got all kinds of errors.

What I did in the end was go to:

[http://flukkost.nu/blog/tomboy-reminder/](http://flukkost.nu/blog/tomboy-reminder/)

Download the binary and put it in ~/.tomboy/addins/  folder

restart tomboy, go to Edit>Preferences and click the Add-ins tab. Under 'Tools' you see  Reminder.  Enable it and it should work.

Good luck!

---

### Post by cairnsww on 2007-12-30
Thanks very much for your trouble. I did what you suggested and it worked perfectly.

Of course, I had already placed the dll in that folder. My problem isd that I had downloaded the dll from http:raphael.slinkx.net/files/tomboy-reminder.dll as suggested in the Full Circle article - that is obviously a bad dll or it is designed for Windows or something. (It is a different size on downloading).  When I used the url that you suggested it all works like a charm.

Thanks again.

---

### Post by lanzen on 2008-01-17
Oh well, I'm lucky google landed me here. ;)

I tried moving the dll in ~/.tomboy/addins/ folder, but it didn't work. So I tried /usr/lib/tomboy/addins and this time I could find it in the preferences and enable it.

Thanks

---

