---
title: "Google services refuse to play nice with chrome/chromium in Ubuntu 12.10 64-bit"
date: 2013-04-14
forum: General Help
---

### Post by trikster_x on 2013-04-14
Ubuntu 12.10 64 bit
Fresh install
Processor: Intel® Core&#8482; i5-2500K CPU @ 3.30GHz × 4 
Graphics: GeForce GTX 550 Ti/PCIe/SSE2 using nvidia-current driver

I'm having an issue getting Google services to work properly in chrome/chromium on Ubuntu 12.10 64 bit. If I am logged into a Google service, any Google based HTTPS page doesn't want to fully load, if at all. If I bring up a search using the omnibar then try to use the search bar on the results page, it causes the tab the search was conducted in to become unresponsive and any subsequent Google searches in other tabs get stuck "waiting for www.google.com". I have to close every currently running instance of chrome/chromium and open a new instance to search again. Youtube won't load videos or thumbnails. Any Google links accessed from the "new tab" page cause the same behavior as a search does. The Chrome web store page will not load. Gmail gets stuck while processing requests, and pops up the small window giving me the option to use the low network speed version of gmail. The issues are present in incognito mode as well, if I log into a google account.

I've tried purging and reinstalling chrome/chromium, as well as wiping and reinstalling Ubuntu itself. The problems happen even with no extensions installed. If I log out of my google account, or use a non-HTTPS version of a google service (such as google.com.au), the issues go away. Firefox is not affected. My other computer with 32-bit 12.10 has none of these issues. Windows 7 64-bit does not have any of these issues. I've tried disabling third-party cookies, to no effect. My network speed is not an issue, as I can run the exact same search/request in firefox and the page instantly loads while chrome waits for a response from google.com. Running chrome/chromium through a terminal yields no errors that would point to a problem. The only errors I get are 

```
[2785:2806:0414/164119:ERROR:object_proxy.cc(624)] Failed to get name owner. Got org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'org.chromium.Mtpd': no such name

[2785:2806:0414/164119:ERROR:object_proxy.cc(624)] Failed to get name owner. Got org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'org.chromium.Mtpd': no such name

[2785:2785:0414/164119:ERROR:object_proxy.cc(529)] Failed to call method: org.chromium.Mtpd.EnumerateStorages: object_path= /org/chromium/Mtpd: org.freedesktop.DBus.Error.ServiceUnknown: The name org.chromium.Mtpd was not provided by any .service files
```

at startup and 

```
[2785:2785:0414/164253:ERROR:omnibox_view_gtk.cc(431)] Not implemented reached in virtual void OmniboxViewGtk::ApplyCaretVisibility()
```

whenever I click in the omnibox to give it focus. Chrome and chromium both display the same errors.

I have been unable to find any fixes for this in a search and using google's problem resolution channels has been unfruitful. If someone knows how to make this stop, I would be extremely grateful.

---

