---
title: "How can I get proper Chromium back?"
date: 2019-10-25
forum: General Help
---

### Post by The Cog on 2019-10-25
19.10 seems to have a snap chromium rather than the proper one. I can go and make a cuppa while it's starting, and it's lost all my stored passwords.
Is there any way to get the proper chromium browser back again?

---

### Post by PaulW2U on 2019-10-25
No, the move to a snap is permanent and will eventually extend to all supported releases.
See: [https://discourse.ubuntu.com/t/call-for-testing-chromium-browser-deb-to-snap-transition/11179](https://discourse.ubuntu.com/t/call-for-testing-chromium-browser-deb-to-snap-transition/11179)

The password problem has been fixed in focal but not yet in eoan: [https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1849160](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1849160)

That bug report recommends running the following command
```
snap connect chromium:password-manager-service
```
Does it work for you after restarting Chromium?

---

### Post by The Cog on 2019-10-25
> Does it work for you after restarting Chromium?
I tried it, and I think it may have done. 
Not that it matters - I'm going to start using Firefox instead.
I'll take chromium-browser out of my ansible playbok.

Thanks for the info and links - I wasn't aware of that going on.

---

### Post by mörgæs on 2019-10-25
I noticed that you are using Xubuntu. Is snap-Chromium also the 'mandatory option' there or is it only for Ubuntu?

---

### Post by The Cog on 2019-10-25
Well, I guess that since I asked for "chromium-browser" to be installed and I ended up with the snap version, I assume that only the snap version is available. "apt search chromium browser" doesn't seem to offer a choice.

On the plus side, Firefox feels faster than I remember and it feels like a bit of a homecoming.

---

### Post by PaulW2U on 2019-10-25
The deb package 'chromium-browser' is a transitional package in 19.04 which installs snapd, if not already installed, the chromium snap and any other snaps that Chromium needs in order to function. It should also copy settings over from the deb version but there are a number of outstanding bugs.

The change affects all flavours of Ubuntu, starting with the eoan release, as there is only one 'chromium-browser' package.

---

### Post by mörgæs on 2019-10-25
Thanks both for answers. 
Sounds like Firefox will soon gain popularity...

---

### Post by cruzer001 on 2019-10-25
How sad this is.  Canonical learned nothing from the Unity disaster.  We are here using Linux because we value our choice.

---

### Post by uRock on 2019-10-25
> **mörgæs said:**
> Thanks both for answers. 
Sounds like Firefox will soon gain popularity...
I just stopped using Firefox. It eats too much RAM and it's cache seems to grow to 1GB when I run Bleachbit every other day. I'm back to Chrome. I just have to get over the fact Facebook sees everything I do.
> **cruzer001 said:**
> How sad this is.  Canonical learned nothing from the Unity disaster.  We are here using Linux because we value our choice.
I was saddened when I went to VLC's site and saw they are now packaging as a snap.

---

### Post by TheFu on 2019-10-25
Perhaps there will be a flatpak with fewer constraints than the Ubuntu snaps, which break 50+ workflows by default?
Or hopefully, someone will create a PPA with chromium builds from the git repo?
We can hope.

I have a few years to decide still, but if Canonical continues to force snaps, I'll be looking at alternative distros. Looks like Debian isn't forcing it.  There's a warning about running a Franken-Ubuntu by using different distro packages.

---

### Post by VMC on 2019-10-25
Not sure what ungoogled-chromium is, but what about these binaries:
[https://ungoogled-software.github.io/ungoogled-chromium-binaries/](https://ungoogled-software.github.io/ungoogled-chromium-binaries/)

---

### Post by The Cog on 2019-10-26
> **uRock said:**
> I was saddened when I went to VLC's site and saw they are now packaging as a snap.
On Xubuntu 19.10 it's still a normal program. I guess we'll have to see what 20.04 brings.

---

### Post by ajgreeny on 2019-10-26
> **The Cog said:**
> On Xubuntu 19.10 it's still a normal program. I guess we'll have to see what 20.04 brings.
On the early daily ISOs (mine's Xubuntu from Tuesday 22 Oct) Chromium is snap or nothing.  You can install it from synaptic package manager, so presumably also with ***sudo apt install chromium-browser*** but that command and synaptic install it as a transitional package which then installs the snap.

It's my first use of a snap package and so far I have not had much time to fully test it, but I am disappointed that it may be available only in that manner.

---

### Post by The Cog on 2019-10-26
Sorry, I wasn't clear. Yes, chromium-browser installs a snap package. But VLC (for the moment) is still a normal deb package.

---

### Post by PaulW2U on 2019-10-26
> **ajgreeny said:**
> It's my first use of a snap package and so far I have not had much time to fully test it, but I am disappointed that it may be available only in that manner.

The Ubuntu community have been given more than sufficient notice of the intention to provide the Chromium browser as a snap rather than a .deb package.

[https://ubuntuforums.org/showthread.php?t=2393153&p=13771852](https://ubuntuforums.org/showthread.php?t=2393153&p=13771852) was created back in May 20**18** and updated by me on several occasions but received no response until recently.

[https://discourse.ubuntu.com/t/intent-to-provide-chromium-as-a-snap-only/5987](https://discourse.ubuntu.com/t/intent-to-provide-chromium-as-a-snap-only/5987) also originates from that time so Canonical's Desktop Team have given more than sufficient notice of a change that will not only reduce their workload but will quicken the release of updates to a web browser that they have chosen to support.

---

### Post by TheFu on 2019-10-26
> **PaulW2U said:**
> The Ubuntu community have been given more than sufficient notice of the intention to provide the Chromium browser as a snap rather than a .deb package.

[https://ubuntuforums.org/showthread.php?t=2393153&p=13771852](https://ubuntuforums.org/showthread.php?t=2393153&p=13771852) was created back in May 20**18** and updated by me on several occasions but received no response until recently.

[https://discourse.ubuntu.com/t/intent-to-provide-chromium-as-a-snap-only/5987](https://discourse.ubuntu.com/t/intent-to-provide-chromium-as-a-snap-only/5987) also originates from that time so Canonical's Desktop Team have given more than sufficient notice of a change that will not only reduce their workload but will quicken the release of updates to a web browser that they have chosen to support.

I learned about snaps when problems with VLC supporting DVD playback started being reported here and the normal fixes didn't help.  Also, playing media located on USB storage didn't work for some people.  Then the output from **df -h** started showing "loop" devices which never existed previously.

Probably not the introduction to snaps the hard working desktop team would have preferred.  Certainly, many things about snaps are excellent, well-executed.

> no chromium updates as deb package for 14.04 Trusty - press info 
A post about chromium updates for 14.04 in 2018 doesn't exactly get my attention.  
**Canonical Switching from Debian Packaging to Constrained "Snaps" **would have gotten much more attention, perhaps.

Discourse? Never used it.

Solutions to workflow problems would be appreciated.  How do we have snaps run in monitor-only mode, with relaxed constraints?
* allow access to any storage for read/write, especially USB and NFS storage?
* allow 1 program to communicate with "helper" programs, either in or outside snaps?  I'm thinking PDF viewers or having thunderbird send a URL to Chromium or Chromium to send a mailto:// URL to Thunderbird.

Snaps certainly have a place for high-risk programs like email and browsers, provided that existing workflows are still supported.  I've been using firejail for years now with high risk programs.  Firejail allows me to easily configure access to storage areas locally.  Also, because I set it up, the fact that the a package install isn't using debian packages isn't hidden from users.

Gotta ask - what is the reasoning behind making gnome-calc a snap package?  Is that a high risk app?

Perhaps it is ignorant of me, but most of the Ubuntu news I get comes from OMGUbuntu or /. or Phoronix.com .  /. is rapidly dropping out, since they started blocking anonymous users.  I tend not to read posts that aren't for LTS releases either.
I don't know how to communicate important ideas requesting feedback from normal Ubuntu Desktop users.  Alas, I'm not a normal desktop user - rocking fvwm here. 

I worry about using snaps on my low memory systems with just 2GB of RAM, but I also worry about RAM use on my huge systems with 8GB of RAM.  ;)

I can also admit that I'm confused by release names.  Sure, I know that b is old than c, but mapping the to the YY.MM is beyond me at this point. The numbers provide so much more information.

---

### Post by PaulW2U on 2019-10-26
> **TheFu said:**
> Discourse? Never used it.
You should at least take a look: [https://discourse.ubuntu.com/](https://discourse.ubuntu.com/)

Many of your questions about Ubuntu's future plans will be or have been answered there. Ubuntu's developers, whether employed by Canonical or not, post there and join **intelligent** discussions. That's something that they don't do here.

The reason for my previous post was that the reasoning of the transition of the Chromium browser from a .deb to a snap was published some **18 months** ago. It seems that many readers of these forums are **still** unaware of Canonical's plans with regards to the future of how they deliver the Chromium browser to their users.

I'm deliberately not going to refer to your other points regarding snaps as I know that you and I differ greatly on that method of packaging. You obviously don't like snaps but I'm prepared to report bugs and issues in the hope that the snap technology improves over time. I'm sure it will   :)

---

### Post by TheFu on 2019-10-26
> **PaulW2U said:**
> You should at least take a look: [https://discourse.ubuntu.com/](https://discourse.ubuntu.com/)

Many of your questions about Ubuntu's future plans will be or have been answered there. Ubuntu's developers, whether employed by Canonical or not, post there and join **intelligent** discussions. That's something that they don't do here.

The reason for my previous post was that the reasoning of the transition of the Chromium browser from a .deb to a snap was published some **18 months** ago. It seems that many readers of these forums are **still** unaware of Canonical's plans with regards to the future of how they deliver the Chromium browser to their users.

I'm deliberately not going to refer to your other points regarding snaps as I know that you and I differ greatly on that method of packaging. You obviously don't like snaps but I'm prepared to report bugs and issues in the hope that the snap technology improves over time. I'm sure it will   :)

There is no doubt to me that everyone working on the snap rollout is trying to be helpful and that snaps most definitely solve real issues in the world today.  Sorry that I haven't conveyed it before. I apologize.

---

### Post by The Cog on 2019-10-26
@PaulW2U : I can see that from your perspective, I must have been living in a cave for the past couple of years. Ineeed, I've been short of free time so that's not far wrong. But from my perspective, I am reminded of the "Beware of the leopard" notice in the Hitchiker's Guide.

Since installing 19.10, there have been three new paper-cuts with chromium. Firstly, it takes so long to start that I keep thinking "What is **wrong** with this machine?". Now I know it's a snap, I guess that's the reason. Secondly, it forgot all my passwords and seemed to unable to remember them every day when I re-entered them and told it to. Now I know that's a known bug, and thanks to you I know a fix. Thirdly, whenever I use the mouse to click a different tab, it pops up a big box just a couple of millimetres away from the tab that my cursor touches and repeats the title. To me, that's unexpected, pointless and annoying. 

These are on top of some other papar cuts that have irritated me for a while:
It refuses to use my chosen title-bar theme but enforces its own totally different title and buttons style instead.
It no longer shows the URL that I'm visiting. It doesn't show whether it's http or https, and I gather it now also hides some words in the rest of the URL too. Apparently, I'm too stupid to understand URLs and need protecting from their complexities, and hiding parts of them do that for me.
They recently removed (or maybe just hid rather well) the ability to choose my cookie policy on a site-by-site basis. I haven't been able to just whitelist my favourite sites.

So it's not just that it's a snap that made me uninstall chromium, it's just an accumulation of paper-cuts over time making me feel it's time for a change.

---

### Post by ajgreeny on 2019-10-26
And while we're discussing these details, how can I import all the settings from my 18.04 chromium.deb installation into the snap version?

Never mind; I think I have figured this out but will be interested to hear whether I did it correctly.
[LIST=1]
[*]Copy the ~/.config/chromium folder from the standard 18.04 .deb installation.
[*]In 19.10 or 20.04 go to ~/snap/chromium/909/config/chromium and rename that as chromium.bak
[*]Paste the copied /chromium folder from 18.04 in place of the renamed the snap version.
[*]Delete the chromium.bak folder if you wish to.
[/LIST]

---

### Post by DuckHook on 2019-10-26
For some time now, I've been running Chrome (not Chromium) sandboxed inside a VM, so—on the one hand—I understand the thinking behind Snaps. But I'm also still ignorant about just how effective snap sandboxing is. It seems to me that it may amount to being the worst of both worlds: not enough to be truly secure and yet too much to be convenient and trouble free. My objection to Snaps would be the overhead they impose with correspondingly minimal benefits.

If I understand correctly, PaulW2U is saying that there are advantages to the developers in packing apps up as snaps. I might be okay with that. If it makes life easier for the devs so they can put their time to better use improving Ubuntu elsewhere, that's a possible long-term win for all of us. But that's another matter about which I know little.

@The Cog,

Would you consider installing it as a standalone .deb?
[https://pkgs.org/download/chromium](https://pkgs.org/download/chromium)

*CAUTION* I don't know this site from Adam. Use at your own risk. Also, they are built for Debian Buster so may blow up on Ubuntu.

FWIW, I'm trying to wean myself off of Chrome(ium) over other concerns mainly having to do with Google, trust and privacy. I'm willing to put up with FF's bloat and foibles due to a possibly errant notion of their higher commitment to privacy and no tracking. But like uRock notes, it's noticeably slower, especially on Android.

---

### Post by Frogs Hair on 2019-10-26
> [COLOR=#000000]Would you consider installing it as a standalone .deb?[/COLOR]
[https://pkgs.org/download/chromium](https://pkgs.org/download/chromium)

[COLOR=#000000]*CAUTION* I don't know this site from Adam. Use at your own risk. Also, they are built for Debian Buster so may blow up on Ubuntu.[/COLOR]

There are dependency problems on my build. I would consider Iridium browser If I could get the repository to work.

---

### Post by The Cog on 2019-10-26
I don't doubt that snaps might have advantages for developers. Having fewer versions to maintain is a big one. Developer time is a precious resource. Some kind of sandboxing for things like browsers would be good, I don't know about details though. Right now, it seems that they take a lot longer to start up, and the passwords bug with the first snap I've ever seen was an unfortunate introduction. Hopefully things will improve.

@DuckHook
I don't think I would feel comfortable downloading a deb from "just somewhere", although it probably is OK. Right now I think I've been given enough nudge to give Firefox another try after some years with Chromium: I had been thinking about it for a while anyway. It feels faster than the Chromium snap, and it shows the full URL which I like. Maybe in a few weeks I'll remember the things that prompted me to try Chromium.

---

### Post by DuckHook on 2019-10-26
> **The Cog said:**
> …@DuckHook
I don't think I would feel comfortable downloading a deb from "just somewhere"
You are, of course, entirely correct, hence my big "caution". Normally, I wouldn't even suggest it, but you're an old dog with sound judgment ;)  WOOF.
> …I think I've been given enough nudge to give Firefox another try after some years with Chromium: I had been thinking about it for a while anyway. It feels faster than the Chromium snap, and it shows the full URL which I like. Maybe in a few weeks I'll remember the things that prompted me to try Chromium.
Strangely, I don't actually have any strong feelings for or against browsers. I know that many people have strong likes and dislikes about the exact placement of the toolbar, or the exact tone of this bell or that whistle, but I've always been rather indifferent towards them. I'm as happy with links2's primitivism as I am with Tor's tortoise-like pace. I'm more interested in how securely they work under the hood than in how comfortably they get me to the same destination. Having said that, I do understand the frustration that arises from a slow browser.

Hope you find your ultimate uber-browser!

---

### Post by TheFu on 2019-10-26
I use different browsers, for different purposes, in different ways.

**Trusted networks**
I use firefox when I'm inside my home or business LANs. It has addons to manage trust for different websites, but I'm only willing to trust those sites from a network I control and trust.  I use a slightly constrained firejail, but not in private mode. Settings do get written to disk.

I use Chromium when I'm visiting a few specific websites where I have to trust the website and provide access that I'd never allow firefox to provide.  For example, airline websites, banks or my brokerage accounts. I use firejail with some constraints in this mode and only when I'm on my home or business LANs.

**Untrusted Networks**
I use Chromium in a save-nothing firejail when I'm outside trusted networks. Nothing can be written to disk and an overlay file system prevents seeing any files in my HOME or anywhere else on the system.  For all effective purposes, the browser appears to be running for the very first time to any website.

I use lynx from servers and desktops when I just want to grab a download file quickly and know javascript isn't needed.  For example, my local University has lots of Linux downloads which are very fast if you happen to live in the state [http://www.gtlib.gatech.edu/](http://www.gtlib.gatech.edu/)

I use dillo when I don't want javascript or hassles with too much RAM use, but also want a GUI browser.  Dillo should never be trusted with HTTPS websites, though it will work. Zero javascript support.  Also handy when you want to browse using mobile designed websites.  Dillo doesn't write much to the file system.

Using the best tool for the job is a good thing.  One size doesn't fit everyone.   We choose Linux for the flexibility, which other OSes do not provide.

---

