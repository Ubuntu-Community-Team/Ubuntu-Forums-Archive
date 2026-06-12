---
title: "Google Chrome ppa updates faster than expected?"
date: 2014-10-07
forum: General Help
---

### Post by vasa1 on 2014-10-07
Has anyone with a nominal download speed << 1 MB/s noticed that apt-get updates have recently been appearing to occur at rates faster than your nominal download speed?

For example, I have a broadband connection which is supposed to be 600 kB/s but my terminal shows me this:```
92% [1 google-chrome-stable 43.6 MB/47.6 MB 92%]                  2,321 kB/
94% [1 google-chrome-stable 44.9 MB/47.6 MB 94%]                  2,321 kB/
97% [1 google-chrome-stable 46.0 MB/47.6 MB 97%]                  2,321 kB/
99% [1 google-chrome-stable 47.1 MB/47.6 MB 99%]                  2,321 kB/
100% [Working]                                                    2,321 kB/


Fetched **47.6 MB in 20s (2,338 kB/s)**
(Reading database ... 199133 files and directories currently installed.)
Preparing to unpack .../google-chrome-stable_38.0.2125.101-1_amd64.deb ...
Unpacking google-chrome-stable (38.0.2125.101-1) over (37.0.2062.120-1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1) ...
Setting up google-chrome-stable (38.0.2125.101-1) ...
04:59 AM ~ $ 
```I'd say I've been seeing these "faster than what I'd expect based on my nominal broadband speed" speeds during apt-get over the last 2-3 few months. It's particularly clear with the updates of google-chrome.

Can anyone else with a slower net speed confirm seeing something similar?

I guess those with fast connections won't see this improvement.

---

