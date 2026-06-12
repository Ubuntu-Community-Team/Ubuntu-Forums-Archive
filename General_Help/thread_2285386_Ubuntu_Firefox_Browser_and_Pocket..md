---
title: "Ubuntu Firefox Browser and Pocket."
date: 2015-07-05
forum: General Help
---

### Post by warren3 on 2015-07-05
Hi.

I'm running Ubuntu 14.04.2.  For some reason Pocket is not showing in Firefox.  I thought it was now bundled with the browser?

I'm running FF 38.0.

Thanks.

---

### Post by vasa1 on 2015-07-05
What do you see in about:config?
```
browser.pocket.enabled;false
```The default should be **true**.

---

### Post by warren3 on 2015-07-05
> **vasa1 said:**
> What do you see in about:config?
```
browser.pocket.enabled;false
```The default should be **true**.

*browser.pocket.enabled;false* is not in about:config

---

### Post by ajgreeny on 2015-07-05
Perhaps you need to make a new boolean item by using a right click in the about:config page?

I am afraid I had no idea what **pocket** was in FF until I searched on seeing your question, so I'm not sure about any of this.

[https://getpocket.com/firefox/](https://getpocket.com/firefox/) might help you out more.

---

### Post by vasa1 on 2015-07-05
> **warren3 said:**
> *browser.pocket.enabled;false* is not in about:config
Just search for **browser.pocket.enabled**, not the whole string *browser.pocket.enabled;false*. Or just search for **pocket**. You should find several hits.

```
browser.pocket.useLocaleList;true
browser.pocket.site;getpocket.com
browser.pocket.oAuthConsumerKey;40249-e8c401e1b1f2242d9e441c4
browser.pocket.enabledLocales;en-US en-GB en-ZA de es-ES ja ja-JP-mac ru
browser.pocket.api;api.getpocket.com
browser.uiCustomization.state; ... *this one is quite long*!
browser.toolbarbuttons.introduced.pocket-button;true
browser.pocket.enabled;false
```


[http://www.ghacks.net/2015/05/14/how-to-disable-pocket-in-firefox/](http://www.ghacks.net/2015/05/14/how-to-disable-pocket-in-firefox/)
[http://www.ghacks.net/2015/06/23/pro-and-con-of-mozillas-pocket-integration-in-firefox/](http://www.ghacks.net/2015/06/23/pro-and-con-of-mozillas-pocket-integration-in-firefox/)

---

### Post by ajgreeny on 2015-07-06
> **vasa1 said:**
> Just search for **browser.pocket.enabled**, not the whole string *browser.pocket.enabled;false*. Or just search for **pocket**. You should find several hits.

```
browser.pocket.useLocaleList;true
browser.pocket.site;getpocket.com
browser.pocket.oAuthConsumerKey;40249-e8c401e1b1f2242d9e441c4
browser.pocket.enabledLocales;en-US en-GB en-ZA de es-ES ja ja-JP-mac ru
browser.pocket.api;api.getpocket.com
browser.uiCustomization.state; ... *this one is quite long*!
browser.toolbarbuttons.introduced.pocket-button;true
browser.pocket.enabled;false
```


[http://www.ghacks.net/2015/05/14/how-to-disable-pocket-in-firefox/](http://www.ghacks.net/2015/05/14/how-to-disable-pocket-in-firefox/)
[http://www.ghacks.net/2015/06/23/pro-and-con-of-mozillas-pocket-integration-in-firefox/](http://www.ghacks.net/2015/06/23/pro-and-con-of-mozillas-pocket-integration-in-firefox/)
Interesting!
I have no entries at all if I search for **browser.pocket** in about:config so perhaps you have to add pocket to FF and pocket is not either installed or enabled by default?

---

### Post by vasa1 on 2015-07-06
> **ajgreeny said:**
> Interesting!
I have no entries at all if I search for **browser.pocket** in about:config so perhaps you have to add pocket to FF and pocket is not either installed or enabled by default?
The difference could be that my Firefox is direct from Mozilla and not from the software center.  I most certainly didn't install pocket :) Maybe the Mozilla Team who preps Firefox for Ubuntu users has removed pocket?

I seem to recall a launchpad site (?) that had such information.

I looked at [http://www.ubuntuupdates.org/package/ubuntu_mozilla_security/trusty/main/base/firefox](http://www.ubuntuupdates.org/package/ubuntu_mozilla_security/trusty/main/base/firefox) and saw the following link:
[https://launchpadlibrarian.net/210248958/firefox_38.0%2Bbuild3-0ubuntu0.14.04.1_39.0%2Bbuild5-0ubuntu0.14.04.1.diff.gz](https://launchpadlibrarian.net/210248958/firefox_38.0%2Bbuild3-0ubuntu0.14.04.1_39.0%2Bbuild5-0ubuntu0.14.04.1.diff.gz)
This zip expands to about 39 MB.

When I searched for "pocket", I saw this:
```
+pref("browser.pocket.enabled", true);
+pref("browser.pocket.api", "api.getpocket.com");
+pref("browser.pocket.site", "getpocket.com");
+pref("browser.pocket.oAuthConsumerKey", "40249-e88c401e1b1f2242d9e441c4");
+pref("browser.pocket.useLocaleList", true);
+pref("browser.pocket.enabledLocales", "en-US en-GB en-ZA de es-ES ja ja-JP-mac ru");

```There are more pocket-related entries but I don't quite know how to interpret the diffs.

---

### Post by Dennis N on 2015-07-06
The new integrated pocket comes in Firefox 38.0.5. I understand from reading that there was also a plug-in available before that for some time. I have yet to try this new feature, but it is there. Right now, Ubuntu's latest version is 38.0 as of today (Jul 6).

---

### Post by vasa1 on 2015-07-06
> **Dennis N said:**
> The new integrated pocket comes in Firefox 38.0.5. I understand from reading that there was also a plug-in available before that for some time. I have yet to try this new feature, but it is there. Right now, Ubuntu's latest version is 38.0 as of today (Jul 6).
That explains it then. I get updates quicker. But AFAICT, 38.0.5 (the direct version) came out at least a week ago.

I had posted about Firefox and pocket here: [http://ubuntuforums.org/showthread.php?t=2281123](http://ubuntuforums.org/showthread.php?t=2281123)

---

### Post by warren3 on 2015-07-06
Hi.

Thanks for your help.

That's what I mean.  There seems to be some sort of limbo here.  Ubuntu Software Center has not updated FF to 38.0.5 with integrated Pocket and with FF 38  I cannot download the Pocket extension because the Pocket devs seemed to have removed it.  So I'm stuck without a service I use a lot.

Does anyone know when FF will be updated to 38.0.5 for Ubuntu?

Cheers.

---

### Post by Dennis N on 2015-07-06
On my computer with Firefox 38.0, I see **Pocket 3.0.6.1-signed** among the available add-ons. Nothing indicates it could not be installed. I didn't try to install it, however. I may try on a test machine. Quite popular - It has had over 7 million downloads. 

I also recall reading that if you were using the add-on, you would be switched to the integrated pocket when it is available.

---

### Post by ajgreeny on 2015-07-06
> **Dennis N said:**
> On my computer with Firefox 38.0, I see **Pocket 3.0.6.1-signed** among the available add-ons. Nothing indicates it could not be installed. I didn't try to install it, however. I may try on a test machine. Quite popular - It has had over 7 million downloads. 

I also recall reading that if you were using the add-on, you would be switched to the integrated pocket when it is available.
Yes, it's listed but if you try to install it you just get a "Removed by author" message.

---

### Post by Dennis N on 2015-07-06
**"with FF 38 I cannot download the Pocket extension"**
Well, seems you are right about this. I got the message "Error Downloading".

---

### Post by Dennis N on 2015-07-06
As to what to do about it, you can:

1) wait a few more days for the next Firefox upgrade.
2) if that is not acceptable, you would have to download the Firefox tarball from Mozilla and start using that version. I can verify it contains the integrated Pocket, as I have it on still another computer (there are quite a few around here). That is what vasa1 does as well.

Usually it does not take very long to get the newest version in the Ubuntu repository, but only you can decide. I will also add that it is technically possible to install and use two Firefox versions on the same system. So there is that option too.

---

### Post by warren3 on 2015-07-08
Ok thanks.

I can wait for the update I'm in no rush. I just hope it ain't too long.

Cheers.

---

