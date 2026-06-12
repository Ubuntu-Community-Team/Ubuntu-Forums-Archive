---
title: "Snaps bloating out my / partition"
date: 2022-01-04
forum: General Help
---

### Post by DuckHook on 2022-01-04
I'm not trying to start another snap war, but it's creating the following issue for me:

Problem:

For years, I've set aside 30 GB for each / on my main multiboot box, which has always been more than enough. But, to my consternation, I've discovered that I'm running out of space on one of them. A quick scan shows the following:
```
duckhook@Zeus:~$  sudo du -cha --max-depth=1 /snap | grep -E "M|G"
[sudo] password for duckhook: 
1.6G	/snap/makemkv
868M	/snap/kde-frameworks-5-core18
395M	/snap/core20
486M	/snap/lxd
4.0K	/snap/README
846M	/snap/signal-desktop
1.1G	/snap/gnome-3-38-2004
678M	/snap/gtk-common-themes
1.7G	/snap/gnome-3-34-1804
312M	/snap/snap-store
338M	/snap/core18
1.3G	/snap/gnome-3-28-1804
1.8G	/snap/telegram-desktop
596M	/snap/core
12G	/snap
12G	total
```This is nuts. &#8776;2 GB for an app like Telegram??? I can't get rid of snap entirely because I rely on LXD which only comes as a snap these days, but I will delete my Telegram, Signal and MakeMKV snaps and reinstall them as PPAs instead (though it grates on me to add PPAs), so those are solvable. But the following questions remain:

[list=1]
[*]Why do I have (?): ```
kde-frameworks-5-core18
```The description reads: ```
duckhook@Zeus:~$  snap info kde-frameworks-5-core18
name:      kde-frameworks-5-core18
summary:   KDE Frameworks 5
publisher: KDE&#10003;
store-url: https://snapcraft.io/kde-frameworks-5-core18
contact:   https://www.kde.org/support/
license:   unset
description: |
  KDE Frameworks are addons and useful extensions to Qt
snap-id:      GeIofQKAwadB4OEM8lOzdSMAc56sCNdL
tracking:     latest/stable
refresh-date: 2020-04-24
channels:
  latest/stable:    5.61.0                         2019-08-27 (32) 273MB -
  latest/candidate: 5.67.0                         2020-02-17 (35) 303MB -
  latest/beta:      &#8593;                                                    
  latest/edge:      5.54.0+p18.04+git20190115.0202 2019-01-16 (25) 250MB -
installed:          5.61.0                                    (32) 273MB -
```..but I don't run KDE. I run vanilla Ubuntu with Gnome, so why do I need this? Can it be safely removed?
[*]Likewise, why (?): ```
gnome-3-28-1804
gnome-3-34-1804
gnome-3-38-2004
```Are all of these needed? Are *any* needed? The descriptions are singularly unhelpful and it seems that my websearch-fu has gone AWOL: ```
duckhook@Zeus:~$  snap info gnome-3-28-1804
name:      gnome-3-28-1804
summary:   Shared GNOME 3.28 runtime for Ubuntu 18.04
publisher: Canonical&#10003;
store-url: https://snapcraft.io/gnome-3-28-1804
contact:   https://gitlab.gnome.org/Community/Ubuntu/gnome-3-28-1804/issues
license:   unset
description: |
  This snap includes a GNOME 3.28 stack (the base libraries and desktop
  integration components) and shares it through the content interface.
snap-id:      TKv5Fm000l4XiUYJW9pjWHLkCPlDbIg1
tracking:     latest/stable
refresh-date: 2021-07-16
channels:
  latest/stable:    3.28.0-19-g98f9e67.98f9e67 2021-07-08 (161) 172MB -
  latest/candidate: 3.28.0-19-g98f9e67.98f9e67 2021-10-26 (166) 172MB -
  latest/beta:      &#8593;                                                 
  latest/edge:      &#8593;                                                 
installed:          3.28.0-19-g98f9e67.98f9e67            (161) 172MB -
duckhook@Zeus:~$  snap info gnome-3-34-1804
name:      gnome-3-34-1804
summary:   Shared GNOME 3.34 Ubuntu stack
publisher: Canonical&#10003;
store-url: https://snapcraft.io/gnome-3-34-1804
license:   unset
description: |
  This snap includes a GNOME 3.34 stack (the base libraries and desktop
  integration components) and shares it through the content interface.
snap-id:      TIM9dBBJEceEjMpwaB3fiuZ3AdSykgDO
tracking:     latest/stable/ubuntu-21.10
refresh-date: 36 days ago, at 16:27 MST
channels:
  latest/stable:    0+git.3556cb3 2021-11-22 (77) 229MB -
  latest/candidate: 0+git.3556cb3 2021-10-26 (77) 229MB -
  latest/beta:      &#8593;                                   
  latest/edge:      &#8593;                                   
installed:          0+git.3556cb3            (77) 229MB -
duckhook@Zeus:~$  snap info gnome-3-38-2004
name:      gnome-3-38-2004
summary:   Shared GNOME 3.38 Ubuntu stack
publisher: Canonical&#10003;
store-url: https://snapcraft.io/gnome-3-38-2004
license:   unset
description: |
  This snap includes a GNOME 3.38 stack (the base libraries and desktop
  integration components) and shares it through the content interface.
snap-id:      rw36mkAjdIKl13dzfwyxP87cejpyIcct
tracking:     latest/stable
refresh-date: 36 days ago, at 16:27 MST
channels:
  latest/stable:    0+git.cd626d1 2021-11-22 (87) 259MB -
  latest/candidate: 0+git.cd626d1 2021-12-17 (90) 260MB -
  latest/beta:      &#8593;                                   
  latest/edge:      &#8593;                                   
installed:          0+git.cd626d1            (87) 259MB -

```I've moved on from 18.04 years ago. I'm guessing that at least two of these are redundant and have been superseded by their newer replacements, but cannot be sure&#8213;it's a wild guess. If so, why have such bloated stubs been left hanging around? Wouldn't the network upgrade process have cleaned them up?
[*]Canonical's move to snaps has left guys like me stranded high and dry. I don't want the hassle of having to grow all of my / partitions which, as a result of past shortsightedness, are packed cheek by jowl next to each other. Yet, I know that as more and more basic apps are shuffled off to snaps, this will just become a growing [s]pain[/s] problem. So, can I relocate /snap to another partition post install? If any of you have done this, can you point me to a decent tutorial?
[*]Do I need both: ```
core18
core20
```Is one of them also redundant/obsolete? Can core18 be safely removed?
[/list]
I would normally tinker away on my own, but since this is my production box, I don't want to mess it up.

---

### Post by HermanAB on 2022-01-04
There is a simple solution.  You can create a partition on another disk and mount it on /snap

---

### Post by tea for one on 2022-01-04
> **DuckHook said:**
> 
Do I need both: ```
core18
core20
```Is one of them also redundant/obsolete? Can core18 be safely removed?


I tried to remove core18 with the following result:-

```
edited@edited:~$ snap list
Name               Version                     Rev    Tracking       Publisher     Notes
bare               1.0                         5      latest/stable  canonical&#10003;    base
core               16-2.52.1                   11993  latest/stable  canonical&#10003;    core
core18             20211028                    2253   latest/stable  canonical&#10003;    base
core20             20211129                    1270   latest/stable  canonical&#10003;    base
get-iplayer        3.27                        315    latest/stable  snapcrafters  -
gnome-3-28-1804    3.28.0-19-g98f9e67.98f9e67  161    latest/stable  canonical&#10003;    -
gnome-3-34-1804    0+git.3556cb3               77     latest/stable  canonical&#10003;    -
gnome-3-38-2004    0+git.cd626d1               87     latest/stable  canonical&#10003;    -
gnome-characters   41.0-6-g3387c148db          761    latest/stable  canonical&#10003;    -
gtk-common-themes  0.1-59-g7bca6ae             1519   latest/stable  canonical&#10003;    -
snap-store         3.38.0-66-gbd5b8f7          558    latest/stable  canonical&#10003;    -
snapd              2.53.4                      14295  latest/stable  canonical&#10003;    snapd
vimix-themes       2020-02-24-15-g426d7e0      2      latest/stable  gantonayde    -
edited@edited:~$ sudo snap remove core18
[sudo] password for edited: 
error: [COLOR="#0000FF"]cannot remove "core18": snap "core18" is not removable: snap is being used by snaps
       get-iplayer, gnome-3-28-1804, gnome-3-34-1804, gnome-characters, gtk-common-themes and 2
       more.[/COLOR]
edited@edited:~$ 

```

I wish that I understood snaps completely, but sadly, I do not.................

---

### Post by deadflowr on 2022-01-04
The /snap directory holds nothing in the hard drive.
snaps on disk are inside the /var/lib/snapd/snaps directory.
if they were in /snap then i'd have run out of space by a couple dozen gigabytes by now.
Interestingly the /snap/README file actually tries to explain this.

As far as core versions are concerned I think certain snaps can only run with certain cores.
Same applies to the varying gnome/gtk frameworks.
Not sure what the kde framework is for, none of the snaps listed seem to have any use for it.
though I didn't dig too deep on that.

Also, I would think the /snap directory is showing all within the directory which also includes any other revisions for the mount for a particular snap.
Look at
```
snap list --all
```
for the full snap listing, which will include any extra revisions.

You can then proceed to remove any older revisions you may want by either doing so piecemeal like
```
snap remove snap-package-name-here --revision ##
```
(replace snap-package-name-here with the snap name and replace ## with the rev number that is listed for the revision you want to remove.)

Or you can run a simple script like this:
```
#!/bin/sh
set -eu

snap list --all | awk '/disabled/{print $1, $3}' |
    while read snapname revision; do
        snap remove "$snapname" --revision="$revision"
    done
```
Which will remove all extra revisions of all snaps.

I not sure what the default is now but I think it's set to keep up to 2 revisions
(meaning you can have 3 versions of a snaps on disk, but can be set to only keep 2.
(2 is the absolute minimal)
See this on how to set those: [https://snapcraft.io/docs/keeping-snaps-up-to-date#heading--refresh-retain]("https://snapcraft.io/docs/keeping-snaps-up-to-date#heading--refresh-retain")

---

### Post by ajgreeny on 2022-01-04
If you do not even use any KDE applications I can see little reason for a need for that kde-frameworks-5-core18 snap package to be needed.

I run Xubuntu and have done so for the past 12 years or so and I had a similar uncertainty when I removed all snaps including several gnome packages from 20.04 which I think appeared when I installed chromium before realising it dragged in the whole snap infrastructure.
I went ahead and  removed all snap packages and snapd from the system, installed chromium using a PPA, and as far as I can see it has caused absolutely no problems of any sort, even though I do run a few more standard gnome applications eg, gthumb.

And if you do remove the snap system completely then find it causes a problem you can just restore snapd and the kde-frameworks package again, as well as all the other snaps you currently have.

---

### Post by dragonfly41 on 2022-01-04
[COLOR=#000000]> I wish that I understood snaps completely, but sadly, I do not.................

I can offer an idea for easier visibility of snaps (although you can list them via command line).

I have Stacer installed (PPA) and I can see all snaps under Processes (search snap) and Uninstaller windows.[/COLOR]

---

### Post by Holger_Gehrke on 2022-01-04
The core, gnome and kde snaps are for other snaps to plug into. They are dependencies. You need Gnome in snap because Applications that come as snaps can't "see" the Gnome that's already on your system. You need different core and gnome snaps because various snaps might depend on different version of the core libraries. Welcome to dependency-hell, snap-style: few dependencies but really big ones which are then kept in multiple revisions (see 'snap list --all', snap keeps at least one old revision so you can roll back updates which don't work right).

And putting /snap on a different partition won't help. that's just the mount point for the squashfs inside the snap-packages. The directory you want to put somewhere else is /var/lib/snapd/snaps/, which is the place where the actual snap packages sit.

Holger

---

### Post by DuckHook on 2022-01-04
Thanks to all for the veritable avalanche of help.

@ajgreeny

I can't just get rid of snaps because LXD depends on it, and I have come to depend on LXD.

@deadflowr & Holger_Gehrke

Thanks for the insights into the guts of this monster. All I can say is: Wow.

I might just shift my whole /var partition someplace else. The new journald logs are also pigs, so it would help there too. I've shifted system partitions post&#8209;install in the past but it's always a fraught exercise. I'll sleep on that one first.

My problem is exacerbated by the fact that I have *three* / partitions for which I must duplicate this strategy. <sigh>

I might just empty my install of all but critical snaps and keep it at bare minimum. Don't know what I will do when must&#8209;have apps like Firefox get snapped. Will cross that bridge when I come to it I suppose.

---

### Post by Holger_Gehrke on 2022-01-04
> **DuckHook said:**
> The new journald logs are also pigs, so it would help there too.

That's one very tame-able pig: read 'man 5 journald.conf' and configure SystemMaxUse, RunTimeMaxUse, and MaxRetentionSec to your taste. Because of its binary format (basically the id of a catalogue, the id of a message from the catalogue and values for placeholders in the message) the journal is actually more compact then an (uncompressed) clear text log. You could also run journalctl with one of '--vacuum-time=...', '--vacuum-size=...' or '--vacuum-files' to cut the journal down to size. A big journal usually means you're keeping multiple years worth of messages on the system.

Holger

---

### Post by DuckHook on 2022-01-04
> **Holger_Gehrke said:**
> That's one very tame-able pig: read 'man 5 journald.conf' and configure SystemMaxUse, RunTimeMaxUse, and MaxRetentionSec to your taste. Because of its binary format (basically the id of a catalogue, the id of a message from the catalogue and values for placeholders in the message) the journal is actually more compact then an (uncompressed) clear text log. You could also run journalctl with one of '--vacuum-time=...', '--vacuum-size=...' or '--vacuum-files' to cut the journal down to size. A big journal usually means you're keeping multiple years worth of messages on the system.

Holger
Thanks Holger.

I've set these parameters in the past. It's hard on my aging brain to remember to do such housekeeping on new installs. Release upgrades also tend to replace config files.

I've had to help out new users with such bloat by using exactly these methods so you would think I would remember. Why do these workarounds have to be so obscure? (Please pardon the rant.)

There's still something to be said for relocating /var. That directory tends to grow with lots of funny oddities hiding in the dark, like a hidden ecosystem of mould or mushrooms. Example: I wasn't aware that it held all that snap stuff. But I gotta weigh taking on that project against my sloth.

Thanks to all for your input.

---

### Post by sgage on 2022-01-04
I use Ubuntu MATE. I am fortunate in that there is nothing that I 'need' a snap for. So I removed all the snaps and then 'apt remove snapd', and that's that. Snaps are an attempt to address a real issue, I guess, but there's got to be a better way.

---

### Post by DuckHook on 2022-01-04
I consider this matter solved.

Solution summary:

Through a combo of crash dieting for the logs (thanks for reminder Holger) but mainly just eliminating the three snap apps, I've whacked the install down by almost 9 GB. The snap apps will need elapse time of 31 days before they surrender reserved data and configs, but that's all right. I can wait it out as long as I know what to expect.

5.5 GB for 3 pretty insignificant snap apps. [-(

UPDATE

As a point of reference: installation of the same three apps via PPA/3rd party repos is just over 500 MB, or 9% of snap footprint.

---

### Post by KBar on 2022-01-05
I'd like to thank everyone who posted in this informative thread. I certainly learnt a thing or two. 

Take care.

---

### Post by schragge on 2022-01-05
> **DuckHook said:**
> 5.5 GB for 3 pretty insignificant snap apps. [-(
There was a recent rant about it: [Flatpak is Not the Future](https://ludocode.com/blog/flatpak-is-not-the-future).

---

### Post by DuckHook on 2022-01-05
> **sgage said:**
> …Snaps are an attempt to address a real issue, I guess, but there's got to be a better way.
> **schragge said:**
> There was a recent rant about it: [Flatpak is Not the Future](https://ludocode.com/blog/flatpak-is-not-the-future).
I'm coming around to agreement with these sentiments.

---

### Post by DuckHook on 2022-01-05
A further update for posterity:

Default Firefox is only available as a snap in Jammy. Given my latest adventures with snaps, I really, really don't want this.

I was able to work around this in my development Jammy install by:

[LIST=1]
[*]Purging the snap version
[*]Adding the following PPA: ppa:mozillateam/ppa
[*]Installing firefox-esr
[/LIST]
Some considerations with this strategy:

[LIST]
[*]Need to add a PPA. Not ideal, but snaps are forcing me back to using them. In this particular case, the PPA is maintained by members of the Mozilla team so it doesn't get much better. Other PPAs will be more dicey.
[*]Need to be okay with the ESR version of FF. This has both advantages and disadvantages, but I feel it to be a small concession (if even that) for the large benefit of not having to deal with a snap version of FF.
[*]Has the not&#8209;so&#8209;fringe benefit of keeping T-Bird right up to date as well. This is an unexpected but welcome plus in my books.
[/LIST]

---

### Post by ajgreeny on 2022-01-06
You could also, if you wish, simply download the latest tar.gz archive and run the executable directly from that as I do in a Debian unstable (Bookmark) version.
That is a self-updating application much like the .deb repository version.

I have seen no problems running FF this way in Debian for the past two Debian versions.

---

### Post by DuckHook on 2022-01-07
> **ajgreeny said:**
> You could also, if you wish, simply download the latest tar.gz archive and run the executable directly from that as I do in a Debian unstable (Bookmark) version.
That is a self-updating application much like the .deb repository version.

I have seen no problems running FF this way in Debian for the past two Debian versions.
I considered that option, but it would involve upgrading FF as a separate step from my regular system upgrades (yes, I *am* that lazy :redface:). Granted, it's not that hard to do and might have been my choice. What finally swung me over to the PPA option was the ability to keep T-Bird up to date as well: [https://www.omgubuntu.co.uk/2021/11/thunderbird-91-backport-ubuntu-18-04-20-04-lts](https://www.omgubuntu.co.uk/2021/11/thunderbird-91-backport-ubuntu-18-04-20-04-lts)

It's been over two months and yet, for some reason, Canonical has not updated T-Bird. I just decided to kill two birds with one stone (ooops, did a pun sneak in there?).

---

### Post by ajgreeny on 2022-01-11
> **DuckHook said:**
> I considered that option, but it would involve upgrading FF as a separate step from my regular system upgrades (yes, I *am* that lazy :redface:). Granted, it's not that hard to do and might have been my choice. What finally swung me over to the PPA option was the ability to keep T-Bird up to date as well: [https://www.omgubuntu.co.uk/2021/11/thunderbird-91-backport-ubuntu-18-04-20-04-lts](https://www.omgubuntu.co.uk/2021/11/thunderbird-91-backport-ubuntu-18-04-20-04-lts)

It's been over two months and yet, for some reason, Canonical has not updated T-Bird. I just decided to kill two birds with one stone (ooops, did a pun sneak in there?).
Just so you know,DuckHook, Firefox used as a direct download of the .tar.gz archive which I use only in a VM of Debian 11 updates itself automatically if set to do so in the Preferences, which I assume is the default setting as I changed nothing in the Preferences.
Then a restart of firefox brings up the newer version; you do not have to manually ask for it to be upgraded, it happens automatically.

---

### Post by DuckHook on 2022-01-11
> **ajgreeny said:**
> …you do not have to manually ask for it to be upgraded, it happens automatically.
Ah. Okay.

It's like how TOR Browser updates itself. Gotcha.

I may very well try that in a container or a VM.

Thanks for the added info.

---

### Post by ajgreeny on 2022-01-11
Don't know tor so can't really answer that.

PS:
There are two other FF PPAs that allow you to use the "real" FF rather than the ESR version, unless of course, that is the version you prefer!
[https://launchpad.net/~mozillateam/+archive/ubuntu/firefox-next](https://launchpad.net/~mozillateam/+archive/ubuntu/firefox-next)  #This is a beta version.
[https://launchpad.net/~ubuntu-mozilla-security/+archive/ubuntu/ppa?field.series_filter=focal](https://launchpad.net/~ubuntu-mozilla-security/+archive/ubuntu/ppa?field.series_filter=focal)

---

### Post by DuckHook on 2022-01-11
> **ajgreeny said:**
> …
There are two other FF PPAs that allow you to use the "real" FF rather than the ESR version, unless of course, that is the version you prefer!
[https://launchpad.net/~mozillateam/+archive/ubuntu/firefox-next](https://launchpad.net/~mozillateam/+archive/ubuntu/firefox-next)  #This is a beta version.
[https://launchpad.net/~ubuntu-mozilla-security/+archive/ubuntu/ppa?field.series_filter=focal](https://launchpad.net/~ubuntu-mozilla-security/+archive/ubuntu/ppa?field.series_filter=focal)
Thanks.

One is Staging and the other is Beta, so probably best not to temp fate that way.

ESR is okay with me, but for those who want the latest stable, I think your self&#8209;maintaining/updating pkg is the best strategy.

I just wish Canonical had not decided to hive FF off to a snap, but what's done is done and these are all good workarounds.

---

### Post by ajgreeny on 2022-01-11
As I understand things it is Ubuntu only, not Xubuntu, Ubuntu-Mate or any other of the family of DE versions that will be using the snap version.
Have I got that wrong?

If that is the way that the different OSs are going to do things with firefox, then there will still be repos with the .deb version available, though how you choose that over the snap I have no idea unless they have different package names.
Do you know if using apt or synaptic to install firefox will do what used to happen with chromium when it moved to snap only and use a shell script to install the snap version.

That was my first (and last) use of any snap packages and it took me some time to realise that is what happened when I installed chromium in 20.04 or whichever was the version where it first did things that way. It did not stay installed that way for long as I quickly realised that I could not use chromium in the way I want, ie, it was not possible to save files where I wanted to, or open any files from my filesystem, even some folders in my home, and certainly nothing in a USB mounted as normal in /media/user.
I now use the chromium version from the PPA at [https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev) which for me has been totally problem free and I can use exactly as I want, not how the snap system tells me I should.

Rant over; sorry about that!

---

### Post by DuckHook on 2022-01-11
> **ajgreeny said:**
> As I understand things it is Ubuntu only, not Xubuntu, Ubuntu-Mate or any other of the family of DE versions that will be using the snap version.
Have I got that wrong?
If that is the way that the different OSs are going to do things with firefox, then there will still be repos with the .deb version available, though how you choose that over the snap I have no idea unless they have different package names.
I don't believe this is how it will work. If I recall, the flames were fuelled by the decision to impose snaps on the other versions too (if one wanted FF), but I'm the last thing from knowledgeable about this topic, so it's only a vague memory. I didn't pay much attention to it at the time because I thought I would just go with the flow when the transition happened. My intentions have only changed very recently with the incidents leading to this thread.
> Do you know if using apt or synaptic to install firefox will do what used to happen with chromium when it moved to snap only and use a shell script to install the snap version.
I don't actually know, but I imagine it will be something of the sort. I intend to remove FF and reinstall it either standalone or through the PPA before I upgrade to Jammy.
> That was my first (and last) use of any snap packages and it took me some time to realise that is what happened when I installed chromium in 20.04 or whichever was the version where it first did things that way. It did not stay installed that way for long as I quickly realised that I could not use chromium in the way I want, ie, it was not possible to save files where I wanted to, or open any files from my filesystem, even some folders in my home, and certainly nothing in a USB mounted as normal in /media/user.
I now use the chromium version from the PPA at [https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev) which for me has been totally problem free and I can use exactly as I want, not how the snap system tells me I should.
My solution was slightly different: this was the impetus I needed to rid myself of the whole Google/quasi&#8209;Google addiction. Yes, I realize that Chromium isn't Google, but there are too many stubs just waiting for Google to plug into. I didn't feel quite right about that. Thus, welcome Brave. It's Chromium&#8209;based but with all (or most) of the Google stubs deleted. With its native ad blocking, script filtering and high security settings, I haven't looked back since. Between these two browsers, I haven't needed anything else for the last two years.

I believe that snap Chromium has since worked out some of its newborn bugs, but now that I've been bitten by the bloat issue, why would I want to install it even if it's workable?
> Rant over; sorry about that!
No apologies needed here. Some would consider my whole thread a rant. :)

---

### Post by oygle on 2022-01-15
Interesting thread, thank you. My experiences with SNAP (now _completely_ **removed**) - [https://ubuntuforums.org/showthread.php?t=2470821](https://ubuntuforums.org/showthread.php?t=2470821)

---

