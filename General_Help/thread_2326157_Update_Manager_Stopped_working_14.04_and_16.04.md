---
title: "Update Manager Stopped working 14.04 and 16.04"
date: 2016-05-28
forum: General Help
---

### Post by ash24 on 2016-05-28
Hi Everyone,

I hope this is in the right forum, about 3 hours ago I tried to check for updates on my Kubuntu 16.04 system and the Update manager opened (plasma-discover-updater) looked like it was working but then the centre pane went blank and then it closed. I tried the usual opening it again a few times and restarting my machine but still no luck. Thinking It was possibly a recent update that dorked it I reinstalled all the Plasma-discover and muon-updater packages but still no luck. Then to double check if it was possibly an update I started up a virtual machine copy of Kubuntu 16.04 that was about a week of updates behind and the same happened the Update manager would open briefly then close. Now I'm getting quite concerned so I check that I can still update via command-line apt and that works absolutely fine and so does Muon Package Manager. I even tried rebooting my Router a couple of times just to make sure it wasn't a network issue and tried using a different internet connection but no luck.

Then I booted my Kubuntu 14.04 Laptop and tried the Update manager (muon-updater) on that and a similar issue happens but instead of it closing it just hangs with the spinning dots in the centre pane as if its checking for updates. This was the same for my Wife's business computer running Kubuntu 14.04.

But here is where it gets slightly weird, I tried the Muon update manager on my VM of Elementery OS and it is working fine and I just installed plasma-discover-updater on my netbook running Lubuntu 16.04 and they both work without issue.

when I run plasma-discover-updater on my Kubuntu 16.04 install and VM install it throws the following

[HTML]
log_attica_plugin: Loaded paths from config: (QUrl("http://download.kde.org/ocs/providers.xml"))
knewstuff: Initializing KNS3::Engine from ' "/etc/xdg/comic.knsrc" '
knewstuff: Loading KNewStuff3 config:  "/etc/xdg/comic.knsrc"
knewstuff: Categories:  ("Plasma Comic")
knewstuff: Using registry file:  "/home/ash/.local/share/knewstuff3/.knsregistry"
knewstuff: Loading KNS2 registry of files for the component:  ""
knewstuff: Cache read... entries:  0
knewstuff: loading providers from  "http://download.kde.org/ocs/providers.xml"
knewstuff: XmlLoader::load(): url:  QUrl("http://download.kde.org/ocs/providers.xml")
log_attica_plugin: Loaded paths from config: (QUrl("http://download.kde.org/ocs/providers.xml"))
knewstuff: Initializing KNS3::Engine from ' "/etc/xdg/plasmoids.knsrc" '
knewstuff: Loading KNewStuff3 config:  "/etc/xdg/plasmoids.knsrc"
knewstuff: Categories:  ("Plasma 5 Plasmoid")
knewstuff: Loading KNS2 registry of files for the component:  ""
knewstuff: Cache read... entries:  0
knewstuff: loading providers from  "http://download.kde.org/ocs/providers.xml"
knewstuff: XmlLoader::load(): url:  QUrl("http://download.kde.org/ocs/providers.xml")
log_attica_plugin: Loaded paths from config: (QUrl("http://download.kde.org/ocs/providers.xml"))
knewstuff: XmlLoader::slotJobData()
knewstuff: XmlLoader::slotJobData()
knewstuff: XmlLoader::slotJobData()
knewstuff: XmlLoader::slotJobData()
knewstuff: --Xml Loader-START--
knewstuff: "<providers>\n\n<provider>\n <id>kde-look</id>\n <location>http://api.kde-look.org/v1/</location>\n <name>kde-look.org</name>\n <termsofuse>http://kde-look.or
g/terms/</termsofuse>\n <services>\n   <person ocsversion=\"1.3\" />\n   <friend ocsversion=\"1.3\" />\n   <message ocsversion=\"1.3\" />\n   <activity ocsversion=\"1.3\
" />\n   <content ocsversion=\"1.3\" />\n   <fan ocsversion=\"1.3\" />\n   <knowledgebase ocsversion=\"1.3\" />\n   <event ocsversion=\"1.3\" />\n </services>\n</provide
r>\n\n</providers>\n"
knewstuff: --Xml Loader-END--
knewstuff: slotProvidersLoaded
knewstuff: Provider attributes:  ""
log_attica_plugin: No credentials found
knewstuff: Engine addProvider called with provider with id  "http://api.kde-look.org/v1/"
knewstuff: --Xml Loader-START--
knewstuff: "<providers>\n\n<provider>\n <id>kde-look</id>\n <location>http://api.kde-look.org/v1/</location>\n <name>kde-look.org</name>\n <termsofuse>http://kde-look.or
g/terms/</termsofuse>\n <services>\n   <person ocsversion=\"1.3\" />\n   <friend ocsversion=\"1.3\" />\n   <message ocsversion=\"1.3\" />\n   <activity ocsversion=\"1.3\
" />\n   <content ocsversion=\"1.3\" />\n   <fan ocsversion=\"1.3\" />\n   <knowledgebase ocsversion=\"1.3\" />\n   <event ocsversion=\"1.3\" />\n </services>\n</provide
r>\n\n</providers>\n"
knewstuff: --Xml Loader-END--
knewstuff: slotProvidersLoaded
knewstuff: Provider attributes:  ""
log_attica_plugin: No credentials found
knewstuff: Engine addProvider called with provider with id  "http://api.kde-look.org/v1/"
log_attica_plugin: No credentials found
Found invalid category "Plasma Comic"
invalid kns backend!
Discarding invalid backend "knscomics-backend"
knewstuff: Write registry
knewstuff: providerInitialized "kde-look.org"
knewstuff: providers loaded
knewstuff: loaded page  0 current page 0
knewstuff: "0,,,0,100"  add:  39  keys:  ("0,,,0,100")
knewstuff: loaded page  1 current page 1
knewstuff: "0,,,1,100"  add:  0  keys:  ("0,,,1,100", "0,,,0,100")
Segmentation fault (core dumped)
[/HTML]

On Kubuntu 14.04 it has a few lines of errors but nothing like that.

Eventualy after some googling I managed to find a work around

On Kubuntu 16.04 if you run the update manager via the command-line using "plasma-discover-updater --backends qapt-backend" it works perfectly in fact it works slightly better as the "last checked" times are accurate.

On Kubuntu 14.04 if you run the update manager via the command-line using "muon-updater --backends muon-appsbackend" it works perfectly although it still seems to throw the same errors on the command line.

TL;DR

Kubuntu Update Manager has suddenly stopped working on all my Kubuntu installs and it seems to be due to the comics and plasmoids backends and to work again you need to force it to use the "basic" backend. Is anyone else having this issue or is it just me?

Thanks for reading,


Edit reason: [B]Solved

[/B]Just started working again today I think whatever on kde-look.org that as misbehaving has been sorted?!

---

### Post by Der_Da on 2016-05-29
I have the same problem :(

---

### Post by Deniz_Can_Cigsar on 2016-05-29
With 16.04 same here..

---

### Post by ash24 on 2016-05-30
I'm still having this problem in both 16.04 and 14.04 and still can't find an answer to why its happening or how to stop it without a workaround. I have even done a fresh install of 16.04 onto a VM and it displays the same behaviour. I have now even tried changing my DNS servers from my ISP ones to the Google DNS servers and that didn't help. I think it has something to do with the knewstuff provider "kde-look.org" I took a look at the site and other than looking like a refugee from the 90's internet the forum is stuffed with offers for fake passports and other fake Identification, which is more than slightly worrying.

On 16.04 I can get plasma-discover-updater to stay open if i open it while disconnected from the internet then if I reconnect it will check for updates as it should when I open while disconnected from the command line It shows the following output:

[HTML]
log_attica_plugin: Loaded paths from config: (QUrl("http://download.kde.org/ocs/providers.xml"))
knewstuff: Initializing KNS3::Engine from ' "/etc/xdg/comic.knsrc" '
knewstuff: Loading KNewStuff3 config:  "/etc/xdg/comic.knsrc"
knewstuff: Categories:  ("Plasma Comic")
knewstuff: Using registry file:  "/home/ash/.local/share/knewstuff3/.knsregistry"
knewstuff: Loading KNS2 registry of files for the component:  ""
knewstuff: Cache read... entries:  0
knewstuff: loading providers from  "http://download.kde.org/ocs/providers.xml"
knewstuff: XmlLoader::load(): url:  QUrl("http://download.kde.org/ocs/providers.xml")
log_attica_plugin: Loaded paths from config: (QUrl("http://download.kde.org/ocs/providers.xml"))
knewstuff: Initializing KNS3::Engine from ' "/etc/xdg/plasmoids.knsrc" '
knewstuff: Loading KNewStuff3 config:  "/etc/xdg/plasmoids.knsrc"
knewstuff: Categories:  ("Plasma 5 Plasmoid")
knewstuff: Loading KNS2 registry of files for the component:  ""
knewstuff: Cache read... entries:  0
knewstuff: loading providers from  "http://download.kde.org/ocs/providers.xml"
knewstuff: XmlLoader::load(): url:  QUrl("http://download.kde.org/ocs/providers.xml")
log_attica_plugin: Loaded paths from config: (QUrl("http://download.kde.org/ocs/providers.xml"))
no providers for "/etc/xdg/comic.knsrc"
invalid kns backend!
no providers for "/etc/xdg/plasmoids.knsrc"
invalid kns backend!
Couldn't fetch the ratings "Unknown host reviews.ubuntu.com: Host not found"
errors! "illegal value"

[/HTML][FONT=monospace]

Is this happening to everyone on Kubuntu or just the few of us here?

edit:

I'm also getting errors like the following one in the kernel log when it crashes on 16.04 not checked the 14.04 kernel log

[/FONT]> 30/05/2016 14:13        plasma-discover[8902]: segfault at f000000b1 ip 00007ff65ed42fda sp 00007fff3911a160 error 4 in libDiscoverCommon.so[7ff65ed11000+53000]

---

