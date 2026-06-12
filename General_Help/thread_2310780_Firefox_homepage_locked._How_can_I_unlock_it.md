---
title: "Firefox homepage locked. How can I unlock it?"
date: 2016-01-21
forum: General Help
---

### Post by Jack_Dickerson on 2016-01-21
browser.startup.homepage (about:config)  is Locked. How can I unlock it?            
Firefox 43.0.4.  Peach-OSI. (Ubuntu 14.04 based distro.)

I've uninstalled & reinstalled.  The OS apparently has this locked to: 
locked. to: [http://www.peachosi.com/Doors/GoogleSearchT.html](http://www.peachosi.com/Doors/GoogleSearchT.html). 
How can I unlock it?  Ubuntu.  Thanks in advance

---

### Post by sandyd on 2016-01-22
Firefox stores all your data in what is called a "profile".

The profile is not removed or reinstalled when firefox is.

From the looks of it, it could be that an extension or plugin has caused this.

What we can do is to rename the current firefox profile so that firefox will generate a new one. After generating a new profile, your home page should be back to normal.

To rename the current firefox profile, close firefox and run
```

mv ~/.mozilla ~/.mozilla-old

```

---

### Post by Jack_Dickerson on 2016-01-22
Thank you Sandyd, 
 But it wasn't a profile issue.  Apparently the distro (Peach-OSI) had changed things so you were locked into their homepage and couldn't change it. 
 Here is the solution I found.
         There was a file named: syspref.js in /etc/firefox/,  contents listed below:
"// This file can be used to configure global preferences for Firefox // Example: Homepage //pref("browser.startup.homepage", "[http://www.weebls-stuff.com/wab/](http://www.weebls-stuff.com/wab/)"); //user_pref("browser.startup.homepage", "[http://www.peachosi.com/Doors/GoogleSearchT.html](http://www.peachosi.com/Doors/GoogleSearchT.html)"); lockPref("browser.startup.homepage", "[http://www.peachosi.com/Doors/GoogleSearchT.html](http://www.peachosi.com/Doors/GoogleSearchT.html)"); I  commented out the last two lines with //,  and everything works fine.
         This also fixed three other problems as well.   
1. "Undo Closed Tab" did not work.  
2. Add "New Tab" only opened blank- did not show recent sites.
  3. Saved passwords did not auto fill. 
After making the above change these problems disappeared as well. 
Thank you for your help.

---

