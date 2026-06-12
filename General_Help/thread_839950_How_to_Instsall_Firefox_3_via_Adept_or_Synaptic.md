---
title: "How to Instsall Firefox 3 via Adept or Synaptic?"
date: 2008-06-24
forum: General Help
---

### Post by o_swas on 2008-06-24
Hello,

I'm fairly new to Linux so please bear with me.

I'm running Kubuntu 7.10 (KDE).  I have Firefox 2 installed, but now that Firefox 3 is available I want to upgrade.

I originally installed Firefox via Adept.  When I return to Adept (or Synaptic, for that matter) and search for Firefox, I don't see an installation for Firefox 3 "final."  I see:

firefox (it says it's 2.0.0.6)
firefox-3.0 (it says 3.0 alpha 8)
firefox-3.0-dev (it says 3.0 alpha 8)

And some others that don't appear correct.  I haven't (to my knowledge) messed with the repositories list.

How do I go about upgrading to Firefox 3?

Related to that, on Winblows Firefox would automatically upgrade itself to minor versions, like 2.0.0.6 to 2.0.0.7.  This seems to be disabled on Linux.  How do I upgrade Firefox bug/security fixes when they become available, if Firefox doesn't do it automatically?

Thank you!!

-Ryan

---

### Post by omegamike3 on 2008-06-24
afaik, FF3 isn't going to be in the repositories for 7.10, at least, not anytime soon. For now it's going to be available in the 8.04 repositories. However, you can just download and install it manually if you so choose. There shouldn't be anything stopping you from doing that as I had been running the beta's on 7.10 for quite a while before 8.04 came out.

---

### Post by jaygo on 2008-06-29
You can download a Linux ff3 installer directly from mozilla.com. Once that's installed, I believe it will manage its own micro-updates *and* it should run fine on 7.10. BTW, 8.04 >>> 7.10  ;)

---

### Post by amilak on 2008-07-22
> **o_swas said:**
> Hello,

I'm fairly new to Linux so please bear with me.

I'm running Kubuntu 7.10 (KDE).  I have Firefox 2 installed, but now that Firefox 3 is available I want to upgrade.

I originally installed Firefox via Adept.  When I return to Adept (or Synaptic, for that matter) and search for Firefox, I don't see an installation for Firefox 3 "final."  I see:

firefox (it says it's 2.0.0.6)
firefox-3.0 (it says 3.0 alpha 8)
firefox-3.0-dev (it says 3.0 alpha 8)

And some others that don't appear correct.  I haven't (to my knowledge) messed with the repositories list.

How do I go about upgrading to Firefox 3?

Related to that, on Winblows Firefox would automatically upgrade itself to minor versions, like 2.0.0.6 to 2.0.0.7.  This seems to be disabled on Linux.  How do I upgrade Firefox bug/security fixes when they become available, if Firefox doesn't do it automatically?

Thank you!!

-Ryan

I'm also running kubuntu 7.10 and ran in to the problem you described. I've downloaded firefox 3 final from mozilla web site
[http://download.mozilla.org/?product=firefox-3.0.1&os=linux&lang=en-US]("http://download.mozilla.org/?product=firefox-3.0.1&os=linux&lang=en-US")
and installed it manually, It worked.

I followed this
[http://support.mozilla.com/en-US/kb/Installing+Firefox+on+Linux]("http://support.mozilla.com/en-US/kb/Installing+Firefox+on+Linux") 

Refer to the "Installing outside of a package manager" section. 
You don't need to remove Firefox 2.0 as this will install to your home directory. Just change your shortcut. 
But downside is you won't be able to update it from your package manager, for me it's not a problem since my Adept still showing Firefox 3.0 beta 4.
Now what I have is Firefox 3.0.1

Later on I found this much detailed instructions
[https://help.ubuntu.com/community/FirefoxNewVersion]("https://help.ubuntu.com/community/FirefoxNewVersion")

What I followed is in the "Installing Firefox (Quick and Dirty)" section.

After I installed during first run Firefox 3 detect & updated my Google Toolbar plugin by itself.

Hope this will help :)

---

