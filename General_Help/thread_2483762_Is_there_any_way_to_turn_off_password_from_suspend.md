---
title: "Is there any way to turn off password from suspend"
date: 2023-02-08
forum: General Help
---

### Post by lwalper on 2023-02-08
I know it's a security thing, but is there any way to turn off the password requirement when the screen awakens  or returns from suspend mode? It's a aggravation that I don't need every few minutes, and in my setting, I don't need the security.

---

### Post by TheFu on 2023-02-08
If you are using xscreensaver, then the settings for it are available by running 'xscreensaver-settings'.  There's a checkbox to Lock the Screen. Uncheck that. You may want to tweak the other 2 timeout settings, but it isn't needed.

---

### Post by lwalper on 2023-02-08
I don't know anything about xscreensaver. I'm running the standard 22.04 installation, whatever that uses??

---

### Post by TheFu on 2023-02-08
> **lwalper said:**
> I don't know anything about xscreensaver. I'm running the standard 22.04 installation, whatever that uses??

Did you even try the suggestion?

---

### Post by lwalper on 2023-02-08
I wouldn't even know how to try to go about trying the suggestion. As I said, I don't know anything about xscreensaver. Is that a terminal command? I looked in the settings "Help" for xscreensaver with no suggestions offered.

In the terminal I ran xman, used Ctrl-s and searched for xscreensaver with no results shown. Scanning through the manual shows the first entry with "xs" as the first couple of letters in the user commands - "xset" is the first entry - no "xscreensaver"

In the "Miscellaneous" section I see "x25", "x509", "xattr", "xkeyboard-config", but no xscreensaver.

---

### Post by TheFu on 2023-02-08
Different releases use different screen savers.  Since your original post didn't provide that information, I guessed.

[https://help.ubuntu.com/stable/ubuntu-help/](https://help.ubuntu.com/stable/ubuntu-help/) might help.  That's the Ubuntu Desktop Guide, but I assumed you've already looked in it.  Look for "screen lock".  

Those settings, if not separate, can be in the Power Management area.  I suppose that's because many people want their screen to power off, then lock.  For my home office desktop, which is in a locked room, I didn't have automatic password locking for a number of years.  Eventually, I decided that locking every 6+ hrs would be a good idea, so I'd have to unlock after being away or every morning, but the screen still gets turned off after 15 minutes of inactivity. No use wasting power to a monitor if nobody is there looking.

Anyway, hopefully, you can find the answer in the 'activities' area - whatever that is.

---

### Post by lwalper on 2023-02-08
OK ... under the Privacy > Screen area there is an option for Automatic Screen Lock. I turned that off and it all now seems to be peaches and cream. Thanks for the input!

---

