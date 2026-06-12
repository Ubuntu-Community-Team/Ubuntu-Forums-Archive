---
title: "thunderbird hyperlink issue"
date: 2015-02-28
forum: General Help
---

### Post by maclenin on 2015-02-28
I have been using Firefox to open Thunderbird email hyperlinks (happily) for the past 9 years.

However, sometime this week - after, perhaps, an upgrade to the latest version of Thunderbird (31.4.0), I am starting to experience the following error:

1. Open email in Thunderbird
2. Click hyperlink ("EmaiLink") in the Thunderbird email
3. Firefox (Thunderbird's default http handler) opens - and in a single tab, displays: FirefoxHomePage rather than EmaiLink.

Firefox is version 36.

The process of clicking an email link in Thunderbird seems to open the default browser "properly" - however, the handling of the email link is somehow fumbled....

Thanks for any guidance!

P.S. Perhaps, relatedly, I am also unable to [change the default browser in Thunderbird]("http://kb.mozillazine.org/Default_browser#Setting_the_browser_that_opens_in_Thunderbird_-_Linux") - to /usr/bin/google-chrome via Preferences | Attachments - to suss out possible sources of the link-handling issue....

---

### Post by sam_baker2 on 2015-02-28
I recently updated my Firefox browser to 36.0 and now, when I try
to click on a link in Thunderbird mail , a new browser window comes up,
but the address bar is empy. I also noticed, that when I watch a you-tube 
video, that now I cannot take a screenshot of the video.

---

### Post by kurt18947 on 2015-02-28
> **sam_baker2 said:**
> I recently updated my Firefox browser to 36.0 and now, when I try
to click on a link in Thunderbird mail , a new browser window comes up,
but the address bar is empy. I also noticed, that when I watch a you-tube 
video, that now I cannot take a screenshot of the video.

You are not alone in this, my wife had the same issue. I did not, she's running Xubuntu and I'm running Ubuntu Gnome. I don't know if that's the difference or not. Anyway, the problem is that firefox was not shown to be the default browser even though there was no other browser installed. Here is what worked for me:

> 
In Firefox, select Tools | Options (Windows) or Firefox | Preferences (Mac and Linux). Select the Advanced panel. On the General tab, make sure the "Always check to see if Firefox is the default browser on startup" box is checked, and then click the Check Now button. Restart Firefox and then restart Thunderbird.

[https://support.mozilla.org/en-US/kb/Hyperlinks-in-Messages-Not-Working](https://support.mozilla.org/en-US/kb/Hyperlinks-in-Messages-Not-Working)

---

### Post by sam_baker2 on 2015-02-28
@kurt18947

setting the tab in Firefox to always check if Firefox is the default browser seems to fix being able to
open a link in the browser from Thunderbird, but when I still go and try to make a snapshot of 
a you-tube video, doesn't work.

---

### Post by maclenin on 2015-02-28
**kurt18947!**

Thanks for your reply - it seems the simple solution (with a slight variation) was the "correct" solution - assuming Firefox is and should remain your default browser (for opening hyperlinks via Thunderbird). Though I have never had to toggle this setting before today.

I am using xubuntu 12.04 (32 bit) - but my sense is this issue could affect users across all "flavors", "ages"  and "speeds" of *buntu....

What [SOLVED] it for me:

1. Open Firefox (version 36)
2. Select "Preferences"
3. Click the "General" tab (icon)
4. Under **Startup** if you see **Firefox is not your default browser**, click the "Make Default" button to make Firefox your default browser
4.a. Under **Startup** should now (and forever more) have the "Always check if Firefox is your default browser" box checked and indicate "Firefox is currently your default browser"

I did NOTHING to Thunderbird (other than test a hyperlink - succesfully)....

Thanks, again, **kurt18947!**

---

### Post by coldraven on 2015-02-28
I think that FF had an issue after the upgrade to 36. See my post from 2 days ago, there were no home or default options! It's back to normal now :)
[http://ubuntuforums.org/showthread.php?t=2266892&p=13235266#post13235266](http://ubuntuforums.org/showthread.php?t=2266892&p=13235266#post13235266)

---

### Post by maclenin on 2015-02-28
**coldraven!**

Thanks for closing the loop....

---

### Post by ajgreeny on 2015-03-02
This is a bug on launchpad.
See [https://bugs.launchpad.net/ubuntu/+source/emacs24/+bug/1425972](https://bugs.launchpad.net/ubuntu/+source/emacs24/+bug/1425972)

---

