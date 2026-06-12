---
title: "Firefox/Swiftfox"
date: 2007-03-10
forum: General Help
---

### Post by penkin on 2007-03-10
This would be my first post but a long time Ubuntu user :) 

I have the strangest problem with my Firefox and Swiftfox browsers.  For some reason there is a huge open gap at the bottom with a little red arrow on the left (see image below).

Unfortunately it's practically impossible to remvove the browser and reinstall it without breaking my system.

Has anyone seen this before or some insight of where to look?

[http://img169.imageshack.us/my.php?image=screenshothr9.png](http://img169.imageshack.us/my.php?image=screenshothr9.png)
[IMG]http://img169.imageshack.us/my.php?image=screenshothr9.png[/IMG]

---

### Post by cmost on 2007-03-10
I don't see the image you attached!  Nevertheless, I'm using Swiftfox and I don't seem to have any odd display anomalies.

---

### Post by penkin on 2007-03-10
Sorry about that, seems like the image tags are not working :(

Here is the URL:
[http://img169.imageshack.us/my.php?image=screenshothr9.png](http://img169.imageshack.us/my.php?image=screenshothr9.png)

Thanks

---

### Post by cmost on 2007-03-10
Ok, now I see.  This happens when you have a misconfigured extension.  In order to revert back to normal and clear up the problem, you'll have to delete your firefox / Swiftfox profile.  Since you have more than one Mozilla browser installed, you may have more than one profile active at a time.  You can find the profiles by going here:

/home/username/.mozilla/firefox/xxxxxxxxx.default (where xxxxxxxx is some random string.)

The folder containing the extension information is located within these *.default folders in a folder named "chrome".  Delete the "chrome" folders from the profile corresponding the Firefox / Swiftfox and restart the browser.  You'll have to reinstall any extensions you already had.

Good luck!

P.S.  I would export your bookmarks for safekeeping before you do anything.

---

