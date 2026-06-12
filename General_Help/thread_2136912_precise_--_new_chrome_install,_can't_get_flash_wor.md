---
title: "precise -- new chrome install, can't get flash working"
date: 2013-04-19
forum: General Help
---

### Post by oospill on 2013-04-19
hello -- I've got a fresh install of google chrome 26.0.1410.63 and I see flash 11.2r202 in chrome:plugins -- which doesn't work .. I thought the new chrome was supposed to come with pepper!  maybe the lubuntu repos are different?  ..  

I tried downloading the latest pepper flash build from [https://launchpad.net/~skunk/+archive/pepper-flash](https://launchpad.net/~skunk/+archive/pepper-flash) (I got the build for precise).  I had to install libgtk2-perl for the pepper flash installer to work completely .. however, there's no pepper flash listed in chrome:plugins ..

when I run google-chrome:
[4808:4831:0419/010702:ERROR:object_proxy.cc(624)] Failed to get name owner. Got org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'org.chromium.Mtpd': no such name
[4808:4831:0419/010702:ERROR:object_proxy.cc(624)] Failed to get name owner. Got org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'org.chromium.Mtpd': no such name
[4808:4808:0419/010703:ERROR:object_proxy.cc(529)] Failed to call method: org.chromium.Mtpd.EnumerateStorages: object_path= /org/chromium/Mtpd: org.freedesktop.DBus.Error.ServiceUnknown: The name org.chromium.Mtpd was not provided by any .service files

I dono if that's even related .. that says chromium! arg

so that's what I *did* .. uhm, what should I do?  ultimately I want to use chromium and be able to listen to internet radio and youtube on this ageing machine, which I was doing last week, but went to heck after I installed 189 updates -- so I did a fresh install of lubuntu precise and then did the above..

after what seems like tons of googling, I feel lost.

much thanks for any help!

oospill

---

