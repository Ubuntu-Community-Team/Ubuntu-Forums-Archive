---
title: "Speakers Noise"
date: 2016-09-06
forum: General Help
---

### Post by dracoborg on 2016-09-06
Hi Guys.
I have strange problem with my fresh Ubuntu installation. After startup, just after login screen showed up. Screen goes black for a while, then I can hear series of speakers noises. This last for a short while, then login form shows again and I can log in. Sometimes I can see single short noise just before any music or video starts. This must be something with speakers, but I have no idea what.

My Laptop is:
MSI GL62 6QF ([http://www.x-kom.pl/p/310381-notebook-laptop-156-msi-gl62-i7-6700hq-8gb-1tb-gtx960m-fhd.html](http://www.x-kom.pl/p/310381-notebook-laptop-156-msi-gl62-i7-6700hq-8gb-1tb-gtx960m-fhd.html))

But I've replace default HDD with SSD (Crucial MX200), and DVD Writer with additional HDD. I'm also using NVIDIA proprietary drivers, Because Nouveau does not support my Graphic card (I had huge problem with this, constant vomit of errors in terminals, lspci command does not work - just freeze - etc.). I've installed Cinnamon desktop, because Ubuntu sometimes freeze (both on this and my sister ASUS laptop) and I thought it may be Unity fault, but I'm still researching that. This is fresh installation (2 days) and brand new Laptop. I hate to say that, but I don't hear this noises on Windows so it's propably not hardware problem. I've checked syslog and found a lot of logs like that:

```
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2020/cmdline: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:.font-unix: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2021/stat: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2021/cmdline: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2022/stat: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2022/cmdline: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2032/stat: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2032/cmdline: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2033/stat: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2033/cmdline: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2073/stat: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2073/cmdline: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2084/stat: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2084/cmdline: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2091/stat: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2091/cmdline: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2102/stat: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2102/cmdline: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2111/stat: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2111/cmdline: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2163/stat: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2163/cmdline: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2259/stat: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2259/cmdline: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2326/stat: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2326/cmdline: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2330/stat: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2330/cmdline: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2340/stat: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2340/cmdline: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2342/stat: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2342/cmdline: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2351/stat: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2351/cmdline: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2356/stat: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2356/cmdline: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2358/stat: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2358/cmdline: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2363/stat: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2363/cmdline: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2367/stat: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2367/cmdline: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2368/stat: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2368/cmdline: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2379/stat: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2379/cmdline: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2380/stat: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2380/cmdline: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2382/stat: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2382/cmdline: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2383/stat: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2383/cmdline: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2386/stat: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2386/cmdline: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2388/stat: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2388/cmdline: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2389/stat: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2389/cmdline: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2390/stat: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2390/cmdline: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2392/stat: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:2392/cmdline: Ignoruj wzgl&#281;dne &#347;cie&#380;ki
Sep  7 00:16:13 dracoborg-GL62-6QF ureadahead[1066]: ureadahead:.: Ignoruj wzgl&#281;dne &#347;cie&#380;ki

```

Log time match startup time. Any Idea what can cause that?

---

