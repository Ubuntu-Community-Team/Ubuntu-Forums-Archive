---
title: "Finally fixed no flash video in chrome on certain websites"
date: 2014-01-13
forum: General Help
---

### Post by sdowney717 on 2014-01-13
For several years, I could not watch AbcNews, reuters news videos. All I would get in the flash screen was a mixed up miniature mess of various browser components displaying.
Then today it hit the weather channel videos and cbsnews, on those just got a black screen.

So I started to wonder. I tried removing add block plus, I started removing extensions. Then I noticed when loading a lot of tabs after a restart, chrome would say resolving proxy. So in settings I goto advanced and it says an extension is managing proxy settings, well that was a lie!

So i made a new chrome profile. Restarted and a tab constantly came up  saying redirection then presents a page asking for task authorization, which chrome says does not recommend as it runs locally on my pc. So I delete tasks extension, no help. I start deleting about 5 more extensions, finally it is gone!

Starting chrome no more weird redirect page loads.
Now no more weird resolving proxy, no delays, no failures to load tabs and ABC news videos play, and all the others play fine.

screenshot of the redirect page
What is it!

In the click box for info is this text
> Tasks Extension can run on the Google+ canvas or on the Tasks Extension website. Clicking "Allow Access" will grant Tasks Extension the requested permissions wherever it runs.
Application developer:
128956800042.apps.googleusercontent.com
Clicking "Allow access" will redirect you to:
chrome-extension://dmglolhoplikcoamfgjgammjbgchgjdd/third_party/chromium/chrome_ex_oauth.html?chromeexoauthcallback=true

---

### Post by tgalati4 on 2014-01-13
Perhaps this is a hook for Chrome OS?  Does it allow you to watch the video offline?  Try this, watch a short video from a news sight, disconnect your network connection and see if it plays.

---

