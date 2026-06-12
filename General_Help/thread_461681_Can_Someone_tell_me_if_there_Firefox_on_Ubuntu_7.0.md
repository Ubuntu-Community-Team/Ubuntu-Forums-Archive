---
title: "Can Someone tell me if there Firefox on Ubuntu 7.04 shows them this?"
date: 2007-06-01
forum: General Help
---

### Post by mmilitia9 on 2007-06-01
Hey all,

I have a little problem with my firefox! I can't set any settings for any external players or anything when I go to edit, preferences, content, Manage.  All I see is 1 setting for shockwave.  Does anyone see the same thing in there File Type Manager?  What is a few ways to troubleshoot something like this?

Heres a screenshot: [http://img370.imageshack.us/img370/6134/screenshotpx2.png](http://img370.imageshack.us/img370/6134/screenshotpx2.png)


Thanks, 

Dominick




(I apologize for posting multiple times.  I just need this resolved ASAP because I installed Ubuntu on a few of my friends and now there complaining and now that I just noticed myself.. I'm boggled as well.)

---

### Post by dave-5B on 2007-06-02
i get the same thing, and i was wonerdin why the other day

dunno why, one would assume theres a config file somewhere where you can do it manually

---

### Post by Lord Illidan on 2007-06-02
Did you install the restricted codecs? I get all this:

---

### Post by dave-5B on 2007-06-02
I found the answer!

> 

Type about:config in address bar
Type plugin in search bar
Right click on "browser.download.hide_plugins_without_extensi ons"
and Toggle to "false"
Edit>Preferences>Content>Manage and you will see all your file types revealed for adjustment


thanks to this thread: [http://ubuntuforums.org/showthread.php?t=288048](http://ubuntuforums.org/showthread.php?t=288048)

---

### Post by NilsE on 2007-06-02
Enter  about:config  on the location line

Change: browser.download.hide_plugins_without_extensions from true to false.

Somehow when Flash player plugin is installed it makes all the extensions disappear.   Bug I think.

**[COLOR="Blue"]ALSO, look in Synaptic and see if you get the updated Firefox 2.0.0.4+1-0Ubuntu1 since I believe it fixes the problem.[/COLOR]**

---

