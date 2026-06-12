---
title: "Is Netflix really working on Mozilla Firefox? Please help!"
date: 2017-05-08
forum: General Help
---

### Post by agentfortyseven on 2017-05-08
Hey everyone,
Few days ago, I came across an article that said that Netflix is now Firefox compatible on Linux. However, when I tried running it on my Firefox 53.0 (which I believe is the latest version), I came up with the following error message:
[B]
Whoops, something went wrong...[/B]

**Unexpected Error**

There was an unexpected error. Please reload the page and try again.

**Error Code: F7363-1260**

I was wondering if anyone would be able to help me out. I have a 14.04 Ubuntu on a 32 bit laptop.
Thanks in advance.

---

### Post by Perfect Storm on 2017-05-08
Try: [https://support.mozilla.org/en-US/kb/refresh-firefox-reset-add-ons-and-settings?cache=no](https://support.mozilla.org/en-US/kb/refresh-firefox-reset-add-ons-and-settings?cache=no)

---

### Post by agentfortyseven on 2017-05-09
Hey there Artificial Intelligence. Thanks for the reply. I tried your suggestion but it didn't help. Disabling my only extension didn't help either.

---

### Post by oldos2er on 2017-05-09
Which version of Firefox are you using?

---

### Post by efflandt on 2017-05-09
Netflix works in Linux with Google Chrome (using HTML5) from google.com. Before that I used that I used some netflix ppa package that used wine with gecko as an IE substitute to use Microsoft Silverlight. But I have not used that since Ubuntu 12.04. Note that Chrome is 64-bit only now. I have not tried Chromium which is an open source 32 or 64-bit version of Chrome.

Firefox works for Hulu using flash. Hulu uses some sort of DRM which I don't think Linux Chrome supports.

---

### Post by deadflowr on 2017-05-10
Firefox can run Netflix, however, the error output means there is an add-on causing troubles.
Netflix's own recommendation is to open Firefox's add-on -extension section and disable all add-ons.
[https://help.netflix.com/en/node/57681]("https://help.netflix.com/en/node/57681")

Unfortunately, Firefox on Ubuntu requires a user-agent-switcher, or did last i checked; (using a known user string that works with Netflix)
If you don't have a user agent switcher or have one but still have problems, perhaps look into trying a different switcher.
You can use Chrome's agent string for Firefox if you want,
current string is:
```
Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/58.0.3029.110 Safari/537.36
```

---

### Post by agentfortyseven on 2017-05-10
> **oldos2er said:**
> Which version of Firefox are you using?
I'm using Firefox 53.0 on a 32 bit system

> **deadflowr said:**
> Firefox can run Netflix, however, the error output means there is an add-on causing troubles.
Netflix's own recommendation is to open Firefox's add-on -extension section and disable all add-ons.
[https://help.netflix.com/en/node/57681](https://help.netflix.com/en/node/57681)

Unfortunately, Firefox on Ubuntu requires a user-agent-switcher, or did last i checked; (using a known user string that works with Netflix)

I was hoping to use Netflix on Firefox without depending on any user-agent-switcher. I tried user-agent-overrider addon for firefox in the past but it was more of a temporary solution.

Here's an [article]("http://www.omgubuntu.co.uk/2017/03/netflix-finally-adds-support-firefox-linux") that says it's now possible to watch Netflix without using user-agent-switcher, silverlight, etc

---

### Post by deadflowr on 2017-05-10
Netflix itself says it supports Firefox on Linux directly from Firefox.
But I've not had any reason to install Firefox directly to try.
From [https://help.netflix.com/en/node/23742]("https://help.netflix.com/en/node/23742")
> Mozilla Firefox version 47 or later on Windows Vista or later, Mac OS X 10.7 or later, or Linux*
Supported on stable, official release builds from Mozilla. Non-Mozilla builds are not supported.
I would assume Ubuntu's Firefox is a non-Mozilla build.

My wording was wrong, also.
I should have said Ubuntu's Firefox and not Firefox on Ubuntu.
Made it seem like any ole Firefox build, instead of Ubuntu's specific build of Firefox.
Which is what I was really trying to get at.

But see if that works.

Edit:
I should also add that if you do install Mozilla-built firefox, it'll use whatever the default profile you have for the regular Firefox from Ubuntu.
So perhaps start totally fresh with a new profile.
Either create a new one with
```
firefox --ProfileManager
```
or delete your ~/.mozilla folder and start totally fresh.

---

### Post by agentfortyseven on 2017-05-10
Thanks. I'll give it a try and let you know.

---

### Post by monkeybrain20122 on 2017-05-10
It works totally here without user switching agent  (and I have many addons)  You get the error probably because you forgot to go to Edit > Preference > Content and check the box "Play DRM" Without checking the box netflix won't play because Firefox blocks the playback.

---

### Post by agentfortyseven on 2017-05-10
I tried everything you said, but I still get the same error message. I believe Widevine isn't fully functional on a 32-bit system even though it is listed as a Firefox plugin.

---

### Post by Habitual on 2017-05-10
Google ***Chrome*** plays netflix out of the box.

---

### Post by deadflowr on 2017-05-10
There is no 32-bit Chrome anymore.
(Not sure about chromium and 32-bit, I guess they finally fixed it's updating issue on 14.04, I think it's possible to install widevine on it, not sure though)

Is the system fully up-to-date?
(Now we throw pasta at the wall and see what sticks...)

---

### Post by agentfortyseven on 2017-05-11
> **monkeybrain20122 said:**
> It works totally here without user switching agent  (and I have many addons)  You get the error probably because you forgot to go to Edit > Preference > Content and check the box "Play DRM" Without checking the box netflix won't play because Firefox blocks the playback.
I do have DRM enabled on my Firefox. You're probably using a 64-bit system which is why it's flawless for you unlike me. I read somewhere people on a 32-bit Firefox are having trouble playing DRM content even after enabling it in the browser settings and installing Google Widevine plugin.

---

### Post by agentfortyseven on 2017-05-11
> **deadflowr said:**
> There is no 32-bit Chrome anymore.
(Not sure about chromium and 32-bit, I guess they finally fixed it's updating issue on 14.04, I think it's possible to install widevine on it, not sure though)

Is the system fully up-to-date?
(Now we throw pasta at the wall and see what sticks...)

Yes you're right. Google has killed Chrome for 32-bit users. However Chromium is very much alive and still supported by Google. It sure is possible to install Widevine on Chromium with a bit of workaround, but I find it tedious and haven't tried it either.
My system is up to date. I think my best bet would be to wait until the Widevine plugin for Firefox is fully functional for 32-bit users, or if someone comes up with an alternate solution.

---

### Post by agentfortyseven on 2017-05-14
**UPDATE:** Just as I expected, it was really a waiting game. I can finally run Netflix now without any glitch. I'm gonna go ahead and mark this thread as solved. Once again thanks everyone for your help.

---

