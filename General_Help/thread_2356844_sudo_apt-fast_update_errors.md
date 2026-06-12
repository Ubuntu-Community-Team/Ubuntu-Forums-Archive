---
title: "sudo apt-fast update errors"
date: 2017-03-27
forum: General Help
---

### Post by arnauldd on 2017-03-27
Hello,

when I run :

sudo apt-fast update or sudo apt-get update I have these errors, I'm not pasting all of them here :

```
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/yakkety-backports/universe/binary-armhf/Packages](http://archive.ubuntu.com/ubuntu/dists/yakkety-backports/universe/binary-armhf/Packages) 404 Not Found [IP: 91.189.88.152 80]
E: Failed to fetch [http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu/dists/wily/main/binary-i386/Packages](http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu/dists/wily/main/binary-i386/Packages) 404 Not Found
E: Failed to fetch [http://ppa.launchpad.net/jonls/redshift-ppa/ubuntu/dists/YOUR_UBUNTU_VERSION_HERE/main/binary-amd64/Packages](http://ppa.launchpad.net/jonls/redshift-ppa/ubuntu/dists/YOUR_UBUNTU_VERSION_HERE/main/binary-amd64/Packages) 404 Not Found
E: Failed to fetch [http://ppa.launchpad.net/jonathonf/vim/Ubuntu/dists/Zesty/x86/source/Sources](http://ppa.launchpad.net/jonathonf/vim/Ubuntu/dists/Zesty/x86/source/Sources) 404 Not Found
E: Failed to fetch [http://ppa.launchpad.net/bovender/bovender/ubuntu/dists/ubuntu/main/source/Sources](http://ppa.launchpad.net/bovender/bovender/ubuntu/dists/ubuntu/main/source/Sources) 404 Not Found
E: Failed to fetch [http://ppa.launchpad.net/musicbrainz-developers/stable/Ubuntu/dists/Zesty/branch)/source/Sources](http://ppa.launchpad.net/musicbrainz-developers/stable/Ubuntu/dists/Zesty/branch)/source/Sources) 404 Not Found
E: Failed to fetch [http://ppa.launchpad.net/aasche/aescrypt/ubuntu/dists/wily/main/binary-armhf/Packages](http://ppa.launchpad.net/aasche/aescrypt/ubuntu/dists/wily/main/binary-armhf/Packages) 404 Not Found
E: Failed to fetch [http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu/dists/wily/main/binary-armhf/Packages](http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu/dists/wily/main/binary-armhf/Packages) 404 Not Found
E: Failed to fetch [http://ppa.launchpad.net/kilian/trimage/ubuntu/dists/yakkety/main/binary-i386/Packages](http://ppa.launchpad.net/kilian/trimage/ubuntu/dists/yakkety/main/binary-i386/Packages) 404 Not Found
E: Failed to fetch [http://ppa.launchpad.net/lyc256/sopcast-player/ubuntu/dists/wily/main/binary-armhf/Packages](http://ppa.launchpad.net/lyc256/sopcast-player/ubuntu/dists/wily/main/binary-armhf/Packages) 404 Not Found
E: Failed to fetch [http://ppa.launchpad.net/purple-vk-plugin/dev/ubuntu/dists/yakkety/main/binary-armhf/Packages](http://ppa.launchpad.net/purple-vk-plugin/dev/ubuntu/dists/yakkety/main/binary-armhf/Packages) 404 Not Found
E: Failed to fetch [http://ppa.launchpad.net/ravefinity-project/ppa/ubuntu/dists/yakkety/main/binary-i386/Packages](http://ppa.launchpad.net/ravefinity-project/ppa/ubuntu/dists/yakkety/main/binary-i386/Packages) 404 Not Found
E: Failed to fetch [http://ppa.launchpad.net/shutter/ppa/ubuntu/dists/yakkety/main/binary-amd64/Packages](http://ppa.launchpad.net/shutter/ppa/ubuntu/dists/yakkety/main/binary-amd64/Packages) 404 Not Found
E: Failed to fetch [http://ppa.launchpad.net/tehtotalpwnage/ppa/ubuntu/dists/yakkety/main/binary-i386/Packages](http://ppa.launchpad.net/tehtotalpwnage/ppa/ubuntu/dists/yakkety/main/binary-i386/Packages) 404 Not Found
E: Failed to fetch [http://ppa.launchpad.net/venerix/pkg/ubuntu/dists/wily/main/binary-amd64/Packages](http://ppa.launchpad.net/venerix/pkg/ubuntu/dists/wily/main/binary-amd64/Packages) 404 Not Found
E: Failed to fetch [http://ppa.launchpad.net/wynter/ppa/ubuntu/dists/wily/main/binary-armhf/Packages](http://ppa.launchpad.net/wynter/ppa/ubuntu/dists/wily/main/binary-armhf/Packages) 404 Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.
W: Target Packages (non-free/binary-armhf/Packages) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list.d/resilio-sync.list:1
W: Target Packages (non-free/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list.d/resilio-sync.list:1
W: Target Translations (non-free/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list.d/resilio-sync.list:1
W: Target Translations (non-free/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list.d/resilio-sync.list:1
W: Target DEP-11 (non-free/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list.d/resilio-sync.list:1
W: Target DEP-11 (non-free/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list.d/resilio-sync.list:1
W: Target DEP-11-icons (non-free/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list.d/resilio-sync.list:1
```

and : 

[IMG]https://dl.dropboxusercontent.com/1/view/pudlux0s8ztqbk4/Apps/Shutter/Selection_125.png[/IMG]

thank you for any advice.

---

### Post by #&amp;thj^% on 2017-03-27
Seems things might be a bit mucked up in "/etc/apt/sources.list"
Paste back the output of this, using code tags _Please._
```
inxi -r
```

---

### Post by deadflowr on 2017-03-27
Click on settings to open the software sources, and then go through all the ppas that are listed in Other Software and disable them one by one.
Several are not applicable to 16.10. (Some are extremely old; such as redshift and jason-scheunemann(not sure if I spelled it right) ppas.
And I see the jonathonf ppa only builds for LTS releases such as 14.04 and 16.04.

Therefor, I'd recommend flushing all the ppas out and starting over.

Once you do that you can then re-add only those that are built for the 16.10 release.
(To find out which are supported by 16.10, go to each ones home page at launchpad.net; easy to get to by searching the ppa name in a web search, or use launchpads search engine.)

Once all that is done, then you can see about the not found errors, and what might be going on.

---

### Post by arnauldd on 2017-03-27
> **1fallen said:**
> Seems things might be a bit mucked up in "/etc/apt/sources.list"
Paste back the output of this, using code tags _Please._
```
inxi -r
```

here it is : 

```
Repos:     Active apt sources in file: /etc/apt/sources.list
           deb-src http://archive.ubuntu.com/ubuntu yakkety main multiverse restricted universe #Added by software-properties
           deb http://archive.ubuntu.com/ubuntu yakkety main universe restricted multiverse
           deb http://archive.ubuntu.com/ubuntu yakkety-updates main universe restricted multiverse
           deb-src http://archive.ubuntu.com/ubuntu yakkety-updates universe multiverse main restricted #Added by software-properties
           deb http://archive.canonical.com/ubuntu yakkety partner
           deb http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu wily main # disabled on upgrade to yakkety
           deb http://archive.ubuntu.com/ubuntu yakkety-backports universe multiverse main restricted
           deb http://security.ubuntu.com/ubuntu/ yakkety-security multiverse restricted universe main
           deb [arch=armhf] http://linux-packages.resilio.com/resilio-sync/deb resilio-sync non-free
           deb http://ppa.launchpad.net/jonls/redshift-ppa/ubuntu YOUR_UBUNTU_VERSION_HERE main
           deb http://ppa.launchpad.net/dawidd0811/neofetch/ubuntu yakkety main
           deb http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu yakkety main
           deb http://ppa.launchpad.net/adilson/experimental/ubuntu yakkety main
           deb-src http://ppa.launchpad.net/adilson/experimental/ubuntu yakkety main
           deb http://ppa.launchpad.net/thp/gpodder/ubuntu yakkety main
           deb-src http://ppa.launchpad.net/thp/gpodder/ubuntu yakkety main
           deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu yakkety main
           deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu yakkety main
           deb http://ppa.launchpad.net/jonathonf/vim/Ubuntu Zesty Zapus (development branch) x86
           deb-src http://ppa.launchpad.net/jonathonf/vim/Ubuntu Zesty Zapus (development branch) x86
           deb http://ppa.launchpad.net/bovender/bovender/ubuntu yakkety main
           deb-src http://ppa.launchpad.net/bovender/bovender/ubuntu ubuntu yakkety main
           deb http://ppa.launchpad.net/musicbrainz-developers/stable/Ubuntu Zesty Zapus (development branch) x86
           deb-src http://ppa.launchpad.net/musicbrainz-developers/stable/Ubuntu Zesty Zapus (development branch) x86
           deb http://ppa.launchpad.net/haecker-felix/gradio-daily/ubuntu yakkety main
           deb-src http://ppa.launchpad.net/haecker-felix/gradio-daily/ubuntu yakkety main
           deb http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu yakkety main
           deb-src http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu yakkety main
           deb http://ppa.launchpad.net/micahflee/ppa/ubuntu yakkety main
           deb-src http://ppa.launchpad.net/micahflee/ppa/ubuntu yakkety main
           deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu yakkety main
           deb-src http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu yakkety main
           Active apt sources in file: /etc/apt/sources.list.d/aasche-ubuntu-aescrypt-wily.list
           deb http://ppa.launchpad.net/aasche/aescrypt/ubuntu wily main # disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/atareao-ubuntu-atareao-wily.list
           deb http://ppa.launchpad.net/atareao/atareao/ubuntu yakkety main # disabled on upgrade to xenial disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/atareao-ubuntu-nautilus-extensions-wily.list
           deb http://ppa.launchpad.net/atareao/nautilus-extensions/ubuntu wily main # disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/atareao-ubuntu-nautilus-extensions-xenial.list
           deb http://ppa.launchpad.net/atareao/nautilus-extensions/ubuntu yakkety main # disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/atareao-ubuntu-pushbullet-wily.list
           deb http://ppa.launchpad.net/atareao/pushbullet/ubuntu yakkety main # disabled on upgrade to xenial disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/audio-recorder-ubuntu-ppa-wily.list
           deb http://ppa.launchpad.net/audio-recorder/ppa/ubuntu wily main # disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/bit-team-ubuntu-stable-wily.list
           deb http://ppa.launchpad.net/bit-team/stable/ubuntu yakkety main # disabled on upgrade to xenial disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/cyberduck.list
           deb https://s3.amazonaws.com/repo.deb.cyberduck.io stable main # disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/dlech-ubuntu-keepass2-plugins-wily.list
           deb http://ppa.launchpad.net/dlech/keepass2-plugins/ubuntu yakkety main # disabled on upgrade to xenial disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/dropbox.list
           deb [arch=i386,amd64] http://linux.dropbox.com/ubuntu yakkety main # disabled on upgrade to xenial disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/eosrei-ubuntu-fonts-wily.list
           deb http://ppa.launchpad.net/eosrei/fonts/ubuntu yakkety main # disabled on upgrade to xenial disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/ferramroberto-ubuntu-sopcast-wily.list
           deb http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu wily main # disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/hsoft-ubuntu-ppa-wily.list
           deb http://ppa.launchpad.net/hsoft/ppa/ubuntu wily main # disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/jcfp-ubuntu-nobetas-wily.list
           deb http://ppa.launchpad.net/jcfp/nobetas/ubuntu yakkety main # disabled on upgrade to xenial disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/jcfp-ubuntu-ppa-wily.list
           deb http://ppa.launchpad.net/jcfp/ppa/ubuntu wily main # disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/jitsi-unstable.list
           deb https://download.jitsi.org unstable/ # disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/jtaylor-ubuntu-keepass-wily.list
           deb http://ppa.launchpad.net/jtaylor/keepass/ubuntu yakkety main # disabled on upgrade to xenial disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/kilian-ubuntu-trimage-xenial.list
           deb http://ppa.launchpad.net/kilian/trimage/ubuntu yakkety main # disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/lyc256-ubuntu-sopcast-player-wily.list
           deb http://ppa.launchpad.net/lyc256/sopcast-player/ubuntu wily main # disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/mono-xamarin.list
           deb http://download.mono-project.com/repo/debian wheezy main # disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/mopidy.list
           deb http://apt.mopidy.com/ jessie main contrib non-free # disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/namecoin-gui.list
           deb http://download.opensuse.org/repositories/home:/p_conrad:/coins/xUbuntu_16.04/ /
           Active apt sources in file: /etc/apt/sources.list.d/nathan-renniewaldock-ubuntu-flux-wily.list
           deb http://ppa.launchpad.net/nathan-renniewaldock/flux/ubuntu wily main # disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/nilarimogard-ubuntu-webupd8-wily.list
           deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu wily main # disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/noobslab-ubuntu-icons-wily.list
           deb http://ppa.launchpad.net/noobslab/icons/ubuntu yakkety main # disabled on upgrade to xenial disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/notepadqq-team-ubuntu-notepadqq-wily.list
           deb http://ppa.launchpad.net/notepadqq-team/notepadqq/ubuntu wily main # disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/numix-ubuntu-ppa-wily.list
           deb http://ppa.launchpad.net/numix/ppa/ubuntu wily main # disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/obsproject-ubuntu-obs-studio-wily.list
           deb http://ppa.launchpad.net/obsproject/obs-studio/ubuntu wily main # disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/openshot_developers-ubuntu-ppa-wily.list
           deb http://ppa.launchpad.net/openshot.developers/ppa/ubuntu wily main # disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/owncloud-client.list
           deb http://download.opensuse.org/repositories/isv:/ownCloud:/desktop/Ubuntu_16.04/ / # disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/purple-vk-plugin-ubuntu-dev-wily.list
           deb http://ppa.launchpad.net/purple-vk-plugin/dev/ubuntu yakkety main # disabled on upgrade to xenial disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/ravefinity-project-ubuntu-ppa-wily.list
           deb http://ppa.launchpad.net/ravefinity-project/ppa/ubuntu yakkety main # disabled on upgrade to xenial disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/resilio-sync.list
           deb http://linux-packages.resilio.com/resilio-sync/deb resilio-sync non-free
           Active apt sources in file: /etc/apt/sources.list.d/saiarcot895-ubuntu-myppa-wily.list
           deb http://ppa.launchpad.net/saiarcot895/myppa/ubuntu yakkety main # disabled on upgrade to xenial disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/shutter-ubuntu-ppa-wily.list
           deb http://ppa.launchpad.net/shutter/ppa/ubuntu yakkety main # disabled on upgrade to xenial disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/skype-stable.list
           deb [arch=amd64] https://repo.skype.com/deb stable main
           Active apt sources in file: /etc/apt/sources.list.d/snwh-ubuntu-pulp-wily.list
           deb http://ppa.launchpad.net/snwh/pulp/ubuntu wily main # disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/spotify.list
           deb http://repository.spotify.com stable non-free # disabled on upgrade to xenial disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/teejee2008-ubuntu-ppa-wily.list
           deb http://ppa.launchpad.net/teejee2008/ppa/ubuntu wily main # disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/tehtotalpwnage-ubuntu-ppa-xenial.list
           deb http://ppa.launchpad.net/tehtotalpwnage/ppa/ubuntu yakkety main # disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/tor.list
           deb http://deb.torproject.org/torproject.org jessie main # disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/tox.list
           deb https://pkg.tox.chat/debian nightly wily # disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/ubuntu-sdk-team-ubuntu-ppa-wily.list
           deb http://ppa.launchpad.net/ubuntu-sdk-team/ppa/ubuntu yakkety main # disabled on upgrade to xenial disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/ubuntu-toolchain-r-ubuntu-test-wily.list
           deb http://ppa.launchpad.net/ubuntu-toolchain-r/test/ubuntu yakkety main # disabled on upgrade to xenial disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/unit193-ubuntu-encryption-wily.list
           deb http://ppa.launchpad.net/unit193/encryption/ubuntu wily main # disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/venerix-ubuntu-pkg-wily.list
           deb http://ppa.launchpad.net/venerix/pkg/ubuntu wily main # disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/vincent-vandevyvre-ubuntu-vvv-wily.list
           deb http://ppa.launchpad.net/vincent-vandevyvre/vvv/ubuntu wily main # disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/vlijm-ubuntu-nonotifs-wily.list
           deb http://ppa.launchpad.net/vlijm/nonotifs/ubuntu yakkety main # disabled on upgrade to xenial disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/webupd8team-ubuntu-y-ppa-manager-wily.list
           deb http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu yakkety main # disabled on upgrade to xenial disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/wynter-ubuntu-ppa-wily.list
           deb http://ppa.launchpad.net/wynter/ppa/ubuntu wily main # disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/ys-ubuntu-emojione-picker-wily.list
           deb http://ppa.launchpad.net/ys/emojione-picker/ubuntu wily main # disabled on upgrade to yakkety
           Active apt sources in file: /etc/apt/sources.list.d/zanchey-ubuntu-asciinema-wily.list
           deb http://ppa.launchpad.net/zanchey/asciinema/ubuntu wily main # disabled on upgrade to yakkety



```

---

### Post by #&amp;thj^% on 2017-03-27
Holy Cow...LOL you use a few PPAs I see.:o
Not going to say anything more on this, "PPA's";)
You need to change** or **remove the outside your Distro PPAs Yours is yakkety...
```
IE: http://ppa.launchpad.net/audio-recorder/ppa/ubuntu wily main
vincent-vandevyvre-ubuntu-vvv-wily.list
ppa.launchpad.net/jonathonf/vim/Ubuntu Zesty Zapus (development branch) x86
deb-src http://ppa.launchpad.net/jonathonf/vim/Ubuntu Zesty Zapus (development branch) x86
```
So I think you now know what I mean.
EDIT: You also have some that are shown as listed multiple times,  Like these:
```

W: Target Packages (non-free/binary-armhf/Packages) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list.d/resilio-sync.list:1 W: Target Packages (non-free/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list.d/resilio-sync.list:1
W: Target Translations (non-free/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list.d/resilio-sync.list:1
W: Target Translations (non-free/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list.d/resilio-sync.list:1
W: Target DEP-11 (non-free/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list.d/resilio-sync.list:1
W: Target DEP-11 (non-free/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list.d/resilio-sync.list:1
W: Target DEP-11-icons (non-free/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list.d/resilio-sync.list:1

```
You certainly have been adventurous...LOL:D

---

### Post by deadflowr on 2017-03-27
> **1fallen said:**
> Holy Cow...LOL you use a few PPAs I see.:o
Not going to say anything more on this, "PPA's";)
You need to change** or **remove the outside your Distro PPAs Yours is yakkety...
```
IE: http://ppa.launchpad.net/audio-recorder/ppa/ubuntu wily main
vincent-vandevyvre-ubuntu-vvv-wily.list
ppa.launchpad.net/jonathonf/vim/Ubuntu Zesty Zapus (development branch) x86
deb-src http://ppa.launchpad.net/jonathonf/vim/Ubuntu Zesty Zapus (development branch) x86
```
So I think you now know what I mean.
You certainly have been adventurous...LOL:D

As well as this ppa, for instance,
```
ppa.launchpad.net/jonathonf/vim/Ubuntu Zesty Zapus (development branch) x86
deb-src http://ppa.launchpad.net/jonathonf/vim/Ubuntu Zesty Zapus (development branch) x86
```
doesn't even exist. (zesty version that is)
I'm sure there will be others in a similar state.

---

### Post by arnauldd on 2017-03-28
thank you all for your replies, I don't have time now to follow your advice because of work, I'll get back in a few days.

---

### Post by arnauldd on 2017-03-29
thank you deadflowr & 1fallen , I cleaned my ppas and it's working fine now...

---

