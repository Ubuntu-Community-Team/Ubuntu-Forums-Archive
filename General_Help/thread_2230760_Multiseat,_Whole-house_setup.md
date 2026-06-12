---
title: "Multiseat, Whole-house setup"
date: 2014-06-20
forum: General Help
---

### Post by T-W-X on 2014-06-20
Old Linux user that's been out of the fold for quite some time.  Started with Slackware and the 2.0.0 kernel, experienced Redhat, SuSE, and ended up on either Debian *Woody* or *Etch *before walking away from computers as a hobby for awhile.  Kept working on Wintel professionally in the meantime, but unfortunately no Linux for many years.

So, here's the plan...

I've got a Dell Precision T7400 workstation.  Dual quad-core 64 bit Xeon processors, currently 12GB RAM, expandable quite a bit.  Slots for five SATA**-II** drives, apparently there's a BIOS size issue that means the boot-drive has to be smaller than 2TB.  It has one of the fancier video cards of the era, don't know which one off the top of my head.  I also have a few PCI-X 64-bit 4-interface 1000BaseTX controllers and a few Soundblaster Audigy cards.

I want to build a multiseat, multihead (only one of the seats, the one on my desk nearest the physical box), Mythtv and XBMC setup with xdmcp support for other locations that aren't close enough to directly connect to the box, with Pulseaudio connectivity.  I want one computer (this box) to do all of the work for the house.  Add-in card will be needed for Myth for TV tuning.

I look at it as follows:


[LIST=1]
[*]Pick components needed to complete the physical box 
[*]Pick and install OS 
[*]Configure X for multiseat 
[*]Configure Pulseaudio for multiseat 
[*]Configure X for multihead 
[*]Configure X for remote connections 
[*]Configure Pulseaudio for remote connections 
[*]Configure MythTV 
[*]Install and configure remote locations 
[/LIST]

I've found the Ubuntu docs for multiseat, they don't specifically mention 14.04, but do go up 13.04.  I assume that there's a good chance it'll work.  Any feedback from those that have tried would be appreciated.

As to the OS, I'm leaning toward 14.04.  As I said I'm an old Debian guy from back before Ubuntu was a thing though I got disillusioned and stopped the computer hobby for awhile; and I've taken a job where I'm admining some Ubuntu 12.04 boxes, it's not a lot different than I expected, but 12.04 with the particular application has required a whole lot of third-party repositories, so with this box I'd like to go with something a little newer.  Any pitfalls that I should be aware of?

I've run multihead X since the early days of Xinerama on XFree86.  It appears to be straightforward still.

Haven't worked with Pulseaudio.  ALSA was hot stuff and esound was still common last I was in this, anything in particular I should keep in mind?

As for Myth, this will end up being a client/server on one box sort of thing.  We've been using XBMC on a Windows box for a couple of years now, it looks like XBMC has some controls or interfacing for Myth.  Any suggestions on what to use and what to stay clear of would be appreciated.

I mentioned the quad controller because I'm considering running direct gigabit ethernet from this box to each of the old boxes that will effectively become X-Terminals.  I'm also considering running a wireless access point off of one of the interfaces to attempt to do the same thing with some older laptops.  I'm typing this on an old Dell Latitude D420 now, it doesn't have the horsepower to play streaming video when it has to decode it, so I'm hoping that if I offload the decode part of the picture to another box that it'll be viable again.  I have several old laptops so this could make them useful again.

So right now I'm on step 1, specifically on a hardware ATSC interface (we don't have cable and don't intend to) with at least two tuners, and picking out drives, then choosing what to run (ie, 14.04?  Something else?) filesystem choice, etc.  Any thoughts or suggestions are appreciated.

Thanks.

---

### Post by TheFu on 2014-06-21
I cannot help with most of that, however, I can say
* remote video never works well, I use FreeNX for secured, remote desktops with "productivity apps" - not audio or video. FreeNX is going away x2go seems to be the replacement, but I haven't tried it.
* Get an HDHR network tuner or 2. You'll thank me. Forget the inside-the-case cards. Why restrict yourself to 1 system having access to the tuners, when they can be on the network.
* Consider using VMs to separate different functions. It isn't like you don't have enough RAM.
* Those low-end boxes  ... well, local video will completely depend on the GPU and available drivers. 3+ yr old systems generally have terrible GPU drivers AND those do not support h.264. That means the CPU will need to decode video. Any HiDef video will probably stutter in a terrible way though 480p stuff should be fine. 720+ is what most video comes in these days. You can transcode the recorded videos down to what each client can handle.  Current Gen systems have GPUs with HW support for these video types and handle 1080p video easily in the GPU.

If you want to playback video around the house, take a look at Plex for the server. There is a Plex plugin for XBMC. I'd been using XBMC for a few years and only discovered Plex last fall. I don't like that it isn't F/LOSS, but it is the best DLNA server I've found. No need to create a Plex account at all - it works fine on the same LAN without any login needed.  Networked video devices tend to be DLNA clients, so nothing more is needed. Plex server on your system will transcode on-the-fly per device.  My Plex server is on a cheap $100 box, which cannot handle transcoding on the fly. Fortunately, my playback devices all handle 1080p ... er ... except the Chromecast which is entirely too picky about audio/video codecs.

File systems - ext4. It is the easy choice, the default and works.
As an old timer - you might be temped to create partitions for all sorts of things. Generally that isn't needed much anymore.  If you don't use LVM or encryption, then 1 partition (30G) for OS/Apps/Var is fine, just put /home somewhere else and mount media storage anywhere else.  With LVM and/or encryption, you'll need a /boot partition - don't make it too small. Old kernels tend to lay around and suck up that space. Don't know when that started by sometime in 2010-ish, the automatic cleanup of older kernels stopped happening. It is a manual process now.  Running out of inodes sucks.

---

### Post by T-W-X on 2014-06-21
Heh.  I actually used to own an honest-to-gods HP X-Terminal back in the day, had to set up a TFTP server for it to pull its configuration and runtime stuff from at power-up.  Figured going to high-bandwidth on a proper light Linux box with minimal hooks for video and sound would be fast enough to keep up with video playback if the bulk of the decode was on the main box.  Still might play with that.

I'll look into the network video devices, hadn't considered that.  I still have a RealMagic Hollywood Plus in a static bag in the office, it's been so long since I was heavily involved in video in Linux.

I'm probably going to make a 1TB or 2TB drive act as / and /boot.  /home will be part of that since I don't anticipate needing more than that (my primary system has an 80GB drive right now and I've only started having to delete old ISOs to free up space for fresh stuff), but I'm not sure about the video.  I'll have to see what kind of hardware RAID the T7400 has, I know that the lowliest configuration allow for 0 or 1, so even without anything fancy I could take four drives, create two mirrors, and then create a stripe in Linux (let the hardware do the mirror, software do the stripe), but if this one was equipped with something fancier than I might go 5.

---

### Post by TheFu on 2014-06-21
I've setup x-terminals too ... in the early 1990s.  xdmcp isn't the most efficient protocol, which is why we don't use it commercially much anymore. Good luck with your ideas about video decoding. Don't think it works that way, but I could be wrong.  I know of commercial solutions that DO work that way, but nothing free or even reasonably priced for Linux.

Be VERY careful with FakeRAID, this isn't Windows and support isn't easily possible. For a home user, it is almost always better to let Linux softwareRAID do everything. Much more flexible than HW RAID, unless you keep identical spares around.

And backups are more important than RAID, but you know that already.

Remote audio isn't hard, it is the video playback that is next to impossible at normal resolutions. Plex can transcode down to whatever resolution your systems can handle, but a $50 WDTV Live HD can handle 1080p content easily, never needs patching and just works. BluRay players, smart-TVs, and Android devices just work with DLNA.

Anyway - hopefully others will step in an provide alternative input. We all have our biases ... I've been burned with HW-RAID at home, so I'm still gun-shy.  OTOH, I've migrated an external SW-RAID array between 3 different systems with zero issues over the last 8 yrs.  Even did disk upgrades (4x320G to 4x2TB) to the array in that time.

---

### Post by T-W-X on 2014-06-21
I've done software RAID before, one of the goals is to eventually migrate the data on an old box that's been powered down for close to ten years.  I had built a box with four 120GB drives in a software RAID5 configuration running Reiser, figure it's better to bring up the new one before attempting to coax this old one back up.  A lot of my multimedia files were stored on there.

I may decide to drop the X terminal idea, it was mainly a, "hey, that'd be cool if..." kind of thing, we'll see.  That's part why I'm interested in trying multiseat, so that the GPUs in the native box will do the work for the various stations.  I'd love it if that worked and I could position the T7400 right in the middle of all expected locations, but unfortunately I don't think that without some fairly pricey USB extenders (the kind that use Cat5 and some ethernet-like signalling) that it'd be possible to go that kind of distance.  I can at least reach three spots without violating the distance limitations.

---

