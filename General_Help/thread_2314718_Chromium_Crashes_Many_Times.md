---
title: "Chromium Crashes Many Times"
date: 2016-02-23
forum: General Help
---

### Post by Bryan_Walters on 2016-02-23
Hello Everyone,

I recently started using Ubuntu but the chromium browser crashes many times in a day. What can cause such issue and how can I fix it?

---

### Post by v3.xx on 2016-02-23
Hi Bryan

How much ram do you have?  What are your computer specs?  You could need a video driver.  Are you running Ubuntu 15.10 or something else?  Have you tried other browsers?

---

### Post by Buntu Bunny on 2016-02-23
I have this problem too. No problem with Chrome, but Chromium crashes often (as does Firefox).

---

### Post by dragonfly41 on 2016-02-23
I also have Chromium Web Browser freezing often.

A couple of tips.
First before launching Chromium Web Browser launch System Tools > System Monitor.
When you next experience a freeze look in System Monitor > Processes and look for the chromium process
eating up the most cpu time .. usually named "chromium-browser -type" .. and end that process.
Chromium Web Browser should unlock from freeze.

Second install the add-on OneTab to put your tabs into a single tab.

---

### Post by Buntu Bunny on 2016-02-23
> **dragonfly41 said:**
> A couple of tips.
First before launching Chromium Web Browser launch System Tools > System Monitor.
When you next experience a freeze look in System Monitor > Processes and look for the chromium process
eating up the most cpu time .. usually named "chromium-browser -type" .. and end that process.
Chromium Web Browser should unlock from freeze.

That's a very good tip. Thank you.

---

### Post by yoshii on 2016-02-23
I remember when I was on Puppy Linux, Firefox would crash alot until I DOWNGRADED Flash to a less up to date version.  
I think it's still a good technique.  Not every website needs the most recent version of Flash to run.  
And Flash takes up a lot of RAM.  

Also, if you have some buggy addons, you might need to replace them with more stable ones or don't use them.  
Also, I believe there might be a setting, if I remember correctly, within Firefox that "sandboxes" Flash so if it crashes, it doesn't crash the whole browser.  
But I think modern versions of FireFox have that set by default, so you'll want to make sure you have the most recent version of FireFox if you use that.  

If you are usuing Chromium, it's probably a similar type of issue, but I don't use that browser so I don't know much about it.  Sorry.

---

