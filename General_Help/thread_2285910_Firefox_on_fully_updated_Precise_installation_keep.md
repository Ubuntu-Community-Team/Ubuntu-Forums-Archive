---
title: "Firefox on fully updated Precise installation keeps crashing repeatedly"
date: 2015-07-09
forum: General Help
---

### Post by ani.infinity on 2015-07-09
Hi, this is my first post on the Ubuntu forums, but I'll do my best to not mess up.
I have a fully updated installation of Ubuntu 12.04 which I for web development. Much of front-end work involves using firefox. Recently, firefox (version 39, updated the usual way) started crashing whenever I try to use it. I tried to narrow it down, and here's what I know so far -
[LIST]
[*]Firefox can connect to the internet since Google search prediction works, but crashes immediately whenever I try to actually visit a page on the world wide web. Local pages load and render correctly
[*]Firefox's crash report tells me that it's dying due to a SIGSEGV
[*]I've already tried
[LIST]
[*]disabling add-ons
[*]resetting firefox
[*]browsing in safe mode
[*]purging and reinstalling firefox
[*]deleting the apt-cache copy and reinstalling firefox
[/LIST]
[/LIST]
None of the above have fixed my problem. The only other options I see are to wait for an update that fixes everything (which means I can't do my work for some time), or to roll back to version 38 - which means descending into dependency hell.
I would really appreciate it if someone could even help me pinpoint the cause of this behaviour. :)

---

### Post by ajgreeny on 2015-07-09
Hi ani.infinity and welcome to the forums.

How did you get to FF version 39?

You must be updating FF in an unusual manner or perhaps using a PPA as even in 14.04 and 15.04 the repository version of FF is still at version 38, at least partly because there are some bugs with version 39 in certain Ubuntu versions.

See [http://ubuntuforums.org/showthread.php?t=2285667](http://ubuntuforums.org/showthread.php?t=2285667) for more info on this whole subject, and information about other ways to try new versions of FF from the archive from Mozilla without removing the repository version you would normally have from the repos.

---

### Post by monkeybrain20122 on 2015-07-09
I just get Firefox 39 on 15.04 a few minutes ago (there was no updates one hr ago) so somehow you get it early in 12.04? It is firefox 39.0+build5. Do you have a different build?

It is working fine here.

---

### Post by ani.infinity on 2015-07-09
> **monkeybrain20122 said:**
> I just get Firefox 39 on 15.04 a few minutes ago (there was no updates one hr ago) so somehow you get it early in 12.04? It is firefox 39.0+build5. Do you have a different build?

It is working fine here.

I have no idea how I got it, actually. The backed-up debian file in /var/cache/apt has the filename firefox_39.0+build5-0ubuntu0.12.04.1_i386.deb
I have my updates configured to come from precise-security, precise-updates, and precise-backports. I forgot to mention it, but my installation is 32-bit. Apart from that, I haven't done much else.
The way I see it, FF is probably using a library that it hasn't been tested with on 12.04. As far as i know, certain libraries are not updated anymore on 12.04, but are maintained for newer versions of Ubuntu (14.04 and above), so I guess that the compatibility issue was either absent or removed for 15.04. That's probably why you aren't having any trouble with it.

I don't mess around with my ppa settings too much, but i do have a few extra ppas. I think I'll try disabling them one by one and reinstalling firefox each time, that should help me identify if any of them is a culprit.

Thanks for your help, both of you. ajgreeny, I don't know how to quote multiple people in a single reply yet, but thank you too, your reply gave me another useful hint. :)
I'll update the thread if I can solve my issue. Until then, does anyone know how the dependency tree in apt works? how does apt decide if you're ready to receive a certain version of FF (apart from FF being present in the repositories)? Does it simply check if all the dependencies are at the required versions? Not directly related to my original question, but this might help me to understand what is going on.

---

### Post by ajgreeny on 2015-07-09
An update to my first post.

I have just updated my system, and "lo-and-behold" along came FF 39!

Sorry for the confusion; no doubt 12.04 has now also got FF39, so you may well have just updated normally and got that version yourself.  Unfortunately, I have no idea why it keeps crashing.  I will now have to try my own FF39 to see if it runs OK and I'll come back and let you know.

EDIT:
Not been running for a very long time yet but FF39 all seems good so far.  I have disabled pocket in **about:config** as I don't need that, but I doubt that will be making the difference between crashing and not crashing

---

### Post by ani.infinity on 2015-07-09
> **ajgreeny said:**
> Hi ani.infinity and welcome to the forums.

How did you get to FF version 39?

You must be updating FF in an unusual manner or perhaps using a PPA as even in 14.04 and 15.04 the repository version of FF is still at version 38, at least partly because there are some bugs with version 39 in certain Ubuntu versions.

See [http://ubuntuforums.org/showthread.php?t=2285667](http://ubuntuforums.org/showthread.php?t=2285667) for more info on this whole subject, and information about other ways to try new versions of FF from the archive from Mozilla without removing the repository version you would normally have from the repos.

Alright, After taking a closer look at my sources, I found the ubuntu-mozilla-security ppa among them, and I have no memory of putting it there :-s . I removed those sources, reinstalled firefox, and now everything is fine. Thanks again for your help, ajgreeny! I'll be more careful with what sources I use in future.

EDIT: Just read your reply, and now I have no idea what's going on. I am definitely back on FF version 38, though. Curiouser and curiouser! I get my updates from the server in India and not from the main servers, so it's likely that the Indian server doesn't have FF39 yet (but it might in a few minutes, too - I have no clue how the synchronization actually works). My setup is fine for the time being, so please don't go to any trouble on my behalf. Thanks again for your help - this community really is awesome.

EDIT: I think I'll mark this thread as solved.

---

### Post by howefield on 2015-07-09
Looks like 12.04 hasn't got Firefox 39 yet, so 38 would be right for you as it stands.

[http://packages.ubuntu.com/search?keywords=firefox](http://packages.ubuntu.com/search?keywords=firefox)

---

### Post by monkeybrain20122 on 2015-07-09
> **ani.infinity said:**
> Alright, After taking a closer look at my sources, I found the ubuntu-mozilla-security ppa among them, and I have no memory of putting it there :-s . 

About the Mozilla security ppa 

> Staging PPA for Mozilla and other browser-related security updates.  Unless you are testing updates, you should not install packages from  this PPA 

---

### Post by ajgreeny on 2015-07-09
An update for you all, and unfortunately things are not going as smoothly as I said earlier.

I've now been using FF39 since I upgraded early this afternoon with very mixed results including several crashes which I think followed after use of the flash plugin, which in my case is the freshplayerplugin, ie pepperflash, the same version of flash as in chromium.

I will keep it going for a while and try to see if disabling the pocket and reader options, both of which seem to be new to FF39 and keep popping up notifications annoyingly in the toolbar, helps with stability.  If not I shall downgrade to version 38 again as I have the .deb available from my apt cache, thank goodness, and will then lock the FF version to 38 until this problem is sorted out..

---

### Post by monkeybrain20122 on 2015-07-09
> **ajgreeny said:**
> An update for you all, and unfortunately things are not going as smoothly as I said earlier.

I've now been using FF39 since I upgraded early this afternoon with very mixed results including several crashes which I think followed after use of the flash plugin, which in my case is the freshplayerplugin, ie pepperflash, the same version of flash as in chromium.

I will keep it going for a while and try to see if disabling the pocket and reader options, both of which seem to be new to FF39 and keep popping up notifications annoyingly in the toolbar, helps with stability.  If not I shall downgrade to version 38 again as I have the .deb available from my apt cache, thank goodness, and will then lock the FF version to 38 until this problem is sorted out..

I upgraded this morning. No problem so far. Also use freshplayer plugin.

---

### Post by QDR06VV9 on 2015-07-09
Just a side note you maybe aware of already but dose not hurt to post it.
> Also, the Fresh Player Plugin page has an important **security** note that you should read: "*[...]  the API itself doesn't make any sandboxing, it only allows sandboxed  implementations. This particular implementation doesn't implement any  sandbox. That means that if any malicious code breaks through plugin  security, there are no additional barriers*".
The last time I had checked on that information about a month ago it was still the same. Just saying is all.
Probably a good thing to note in the general section of the forum.
Regards
@ajgreeny have you seen this yet [https://addons.mozilla.org/en-US/firefox/addon/disable-hello-pocket-reader/?src=hp-dl-upandcoming](https://addons.mozilla.org/en-US/firefox/addon/disable-hello-pocket-reader/?src=hp-dl-upandcoming)

---

### Post by ajgreeny on 2015-07-09
Thanks for that runrickus; no, I had not seen it but was wondering if there might be one soon as so many people seem to want to get rid of those supposed extras.

Mozilla really seem to have shot themselves in the foot this time in a bigger way than I remember them ever doing in the past.  I certainly do not want, and have absolutely no use for pocket, reader or hello, and I can not understand why they decided to integrate them with FF rather than have them as installable add-ons.  As someone has said somewhere it makes me consider using seamonkey instead of FF.

---

### Post by QDR06VV9 on 2015-07-09
> **ajgreeny said:**
> Thanks for that runrickus; no, I had not seen it but was wondering if there might be one soon as so many people seem to want to get rid of those supposed extras.

Mozilla really seem to have shot themselves in the foot this time in a bigger way than I remember them ever doing in the past.  I certainly do not want, and have absolutely no use for pocket, reader or hello, and I can not understand why they decided to integrate them with FF rather than have them as installable add-ons.  As someone has said somewhere it makes me consider using seamonkey instead of FF.

+1 :D
I use firefox about 50 percent of the time, then seamonkey for heavy lifting.
Kind Regards

---

### Post by ajgreeny on 2015-07-09
I've just downloaded seamonkey as the latest tar.gz archive but it will not run and gives me an error
```
XPCOMGlueLoad error for file /home/andrew/Downloads/seamonkey/libxul.so:
libXcomposite.so.1: cannot open shared object file: No such file or directory
Couldn't load XPCOM.
```
Not had time to search for an answer to that yet but will report back.

I've now downgraded FF to v38 which is fine; it's just FF39 that continuously crashes.

---

### Post by night_sky2 on 2015-07-09
> **ajgreeny said:**
> I've now been using FF39 since I upgraded early this afternoon with very mixed results including several crashes which I think followed after use of the flash plugin, which in my case is the freshplayerplugin, ie pepperflash, the same version of flash as in chromium.

Man, I've the exact same problem. Running the Fresh Player Plugin and latest pepperflash version.

After watching a video requiring flash player, I now experience crashes almost everytime I exit the browser or even randomly.
This is solved by disabling the Shockwave plugin. I suspect there is an issue between the Fresh Player plugin and Firefox 39.

---

### Post by night_sky2 on 2015-07-09
> **runrickus said:**
> Just a side note you maybe aware of already but dose not hurt to post it.

The last time I had checked on that information about a month ago it was still the same. Just saying is all.
Probably a good thing to note in the general section of the forum.
Regards
@ajgreeny have you seen this yet [https://addons.mozilla.org/en-US/firefox/addon/disable-hello-pocket-reader/?src=hp-dl-upandcoming](https://addons.mozilla.org/en-US/firefox/addon/disable-hello-pocket-reader/?src=hp-dl-upandcoming)

Sure but as far as I know, NPAPI plugins are not sandboxed in Firefox. This is the same thing for the older Adobe Flash Player 11.2

The Fresh Player plugin is just a wrapper allowing pepperflash to be converted to the NPAPI architecture.
 People shouldn't expect it to be sandboxed like in the Google Chrome browser.

---

### Post by monkeybrain20122 on 2015-07-10
> **night_sky2 said:**
> Man, I've the exact same problem. Running the Fresh Player Plugin and latest pepperflash version.

After watching a video requiring flash player, I now experience crashes almost everytime I exit the browser or even randomly.
This is solved by disabling the Shockwave plugin. I suspect there is an issue between the Fresh Player plugin and Firefox 39.

I cannot reproduce the problem. Firefox 39 on Ubuntu 15.04 64 bits on two different machines (intel gpu one, AMD gpu with open driver the other) Latest freshplayer compiled from master. I tested on quite a few flash videos: Youtube, ted, National geographic, CNN,  facebook embedded videos etc.

You may want to take a look at the freshplayer config file.  Here is mine from the intel machine (enabling vaapi or vdpau give enormous performance boost but may cause problems for some hardware or some sites)

 ```
Configuration options for FreshPlayerPlugin

# This configuration file is optional. Wrapper will search for it first
# in ~/.config/freshwrapper.conf, then in /etc/freshwrapper.conf.
# If wrapper fails to find configuration, it will use default values,
# which you can find below

# Audio buffer is used to continuously provide sound adapter with data.
# Values too low may lead to buffer underruns and stuttering.  Values
# too high will lead to noticeable latency. Usually plugin selects size
# on its own, but you may override bounds here

# lower bound for audio buffer size, in milliseconds
audio_buffer_min_ms = 20

# higher bound of audio buffer size, in milliseconds
audio_buffer_max_ms = 500

# output sound through JACK. If enabled, only JACK will be tried, and if
# your machine doesn't have it, there would be no sound, and no sync
audio_use_jack = 0

# Path to the Pepper Flash plugin.
# If the option is absent, freshwrapper will search for Pepper Flash in
# a number of location where it could be. Usually that's enough, but if
# not, you should manually enter the right path. Multiple paths could
# be specified, separated by colon.
pepperflash_path = "/opt/google/chrome/PepperFlash/libpepflashplayer.so"

# "Command-line" arguments for Flash
flash_command_line = "enable_hw_video_decode=1,enable_stagevideo_auto=1"

# enable 3d and stage 3d
enable_3d = 1

#enable_3d_transparent = 0

# enable hardware-accelerated video decoding. Requires 3d to really work
enable_hwdec = 1

# when set to 1, limits output to warnings and errors only
quiet = 0

# When multiple monitors with different resolutions are used, size
# of fullscreen window can vary. But some Flash movies request these
# parameters once at startup and rely on them to be correct. By default,
# if zeros are used here, freshwrapper will select minimal width and
# height across all monitors.
fullscreen_width = 0
fullscreen_height = 0

# Enables DNS query case randomization to partially protect against DNS
# poisoning attacks. It was reported that some Mikrotik routers do not
# support this trick. Set parameter to 0 if you have an affected model
randomize_dns_case = 0

# scaling factor (floating point value) used to convert screen pixels
# to device independent pixels. You may need it for displays with
# high DPI
device_scale = 1

# method org.freedesktop.ScreenSaver.SimulateUserActivity() in KDE 5 seems
# to have no effect unless GetSessionIdleTime() called afterwards. Set
# parameter to 1 to call latter
quirk_plasma5_screensaver = 0

# whenever to use windowed plugin mode
enable_windowed_mode = 0

# whenever XEmbed used in windowed mode (if browser advertises its support)
enable_xembed = 1

# if set to 1, fullscreen window will be kept always above browser, and hidden
# from taskbar and pager
tie_fullscreen_window_to_browser = 1

# enable using of VA-API for hardware accelerated video decoding
enable_vaapi = 1

# enable using of VDPAU for hardware accelerated video decoding
enable_vdpau = 0
```

Edited:  Tested with 14.04 64 bits booting off the same intel machine above with latest freshplugin from master. Works just fine.

Edited: Fedora 22 is still on FF 38.05.  FF39 is apparently in testing repo because some bugs need to be ironed out according to posts on the Fedora forum.

---

### Post by ajgreeny on 2015-07-10
> **monkeybrain20122 said:**
> I cannot reproduce the problem. Firefox 39 on Ubuntu 15.04 64 bits on two different machines (intel gpu one, AMD gpu with open driver the other) Latest freshplayer compiled from master. I tested on quite a few flash videos: Youtube, ted, National geographic, CNN,  facebook embedded videos etc.

You may want to take a look at the freshplayer config file.  Here is mine from the intel machine (enabling vaapi or vdpau give enormous performance boost but may cause problems for some hardware or some sites)

 ```
Configuration options for FreshPlayerPlugin

# This configuration file is optional. Wrapper will search for it first
# in ~/.config/freshwrapper.conf, then in /etc/freshwrapper.conf.
# If wrapper fails to find configuration, it will use default values,
# which you can find below

# Audio buffer is used to continuously provide sound adapter with data.
# Values too low may lead to buffer underruns and stuttering.  Values
# too high will lead to noticeable latency. Usually plugin selects size
# on its own, but you may override bounds here

# lower bound for audio buffer size, in milliseconds
audio_buffer_min_ms = 20

# higher bound of audio buffer size, in milliseconds
audio_buffer_max_ms = 500

# output sound through JACK. If enabled, only JACK will be tried, and if
# your machine doesn't have it, there would be no sound, and no sync
audio_use_jack = 0

# Path to the Pepper Flash plugin.
# If the option is absent, freshwrapper will search for Pepper Flash in
# a number of location where it could be. Usually that's enough, but if
# not, you should manually enter the right path. Multiple paths could
# be specified, separated by colon.
pepperflash_path = "/opt/google/chrome/PepperFlash/libpepflashplayer.so"

# "Command-line" arguments for Flash
flash_command_line = "enable_hw_video_decode=1,enable_stagevideo_auto=1"

# enable 3d and stage 3d
enable_3d = 1

#enable_3d_transparent = 0

# enable hardware-accelerated video decoding. Requires 3d to really work
enable_hwdec = 1

# when set to 1, limits output to warnings and errors only
quiet = 0

# When multiple monitors with different resolutions are used, size
# of fullscreen window can vary. But some Flash movies request these
# parameters once at startup and rely on them to be correct. By default,
# if zeros are used here, freshwrapper will select minimal width and
# height across all monitors.
fullscreen_width = 0
fullscreen_height = 0

# Enables DNS query case randomization to partially protect against DNS
# poisoning attacks. It was reported that some Mikrotik routers do not
# support this trick. Set parameter to 0 if you have an affected model
randomize_dns_case = 0

# scaling factor (floating point value) used to convert screen pixels
# to device independent pixels. You may need it for displays with
# high DPI
device_scale = 1

# method org.freedesktop.ScreenSaver.SimulateUserActivity() in KDE 5 seems
# to have no effect unless GetSessionIdleTime() called afterwards. Set
# parameter to 1 to call latter
quirk_plasma5_screensaver = 0

# whenever to use windowed plugin mode
enable_windowed_mode = 0

# whenever XEmbed used in windowed mode (if browser advertises its support)
enable_xembed = 1

# if set to 1, fullscreen window will be kept always above browser, and hidden
# from taskbar and pager
tie_fullscreen_window_to_browser = 1

# enable using of VA-API for hardware accelerated video decoding
enable_vaapi = 1

# enable using of VDPAU for hardware accelerated video decoding
enable_vdpau = 0
```

Edited:  Tested with 14.04 64 bits booting off the same intel machine above with latest freshplugin from master. Works just fine.

Edited: Fedora 22 is still on FF 38.05.  FF39 is apparently in testing repo because some bugs need to be ironed out according to posts on the Fedora forum.
Where is that config file for freshplayer and what is its name?
I do not have any such file in my system so I'm not sure where it should go in my next attempt.

[COLOR="#FF0000"]EDIT:[/COLOR]
Sorry, Ive just seen where it should go in the first paragraph.

Note to self:  I must read more carefully!

---

### Post by QDR06VV9 on 2015-07-10
> **night_sky2 said:**
> Sure but as far as I know, NPAPI plugins are not sandboxed in Firefox. This is the same thing for the older Adobe Flash Player 11.2

The Fresh Player plugin is just a wrapper allowing pepperflash to be converted to the NPAPI architecture.
 _People shouldn't expect it to be sandboxed like in the Google Chrome browser_.
+1 Have you seen this yet 
> Sandboxing finally comes to the Firefox web browser. After enabling a (currently) non-restrictive [   content sandbox in Firefox Nightly]("http://www.techsupportforum.com/forums/external-link/?link=http%3A%2F%2Fwww.ghacks.net%2F2014%2F12%2F01%2Ffirst-bit-of-firefoxs-sandbox-lands-in-nightly-for-windows%2F") last month, [   the organization enabled]("http://www.techsupportforum.com/forums/external-link/?link=https%3A%2F%2Fbugzilla.mozilla.org%2Fshow_bug.cgi%3Fid%3D1123245") the upcoming NPAPI plug-in sandbox in Aurora and Nightly versions of the browser as well.
 
These sandboxes are designed to limit the rights of tabs and plug-ins in the browser to harden and stabilize it.
 
The plug-in sandbox is deactivated by default and needs to be enabled by the user before it becomes available.
 
It is sandboxing all browser plug-ins by default when enabled but there is also an option to enable it only for select plug-ins.

> **ajgreeny said:**
> I've just downloaded seamonkey as the latest tar.gz archive but it will not run and gives me an error
```
XPCOMGlueLoad error for file /home/andrew/Downloads/seamonkey/libxul.so:
libXcomposite.so.1: cannot open shared object file: No such file or directory
Couldn't load XPCOM.
```
Not had time to search for an answer to that yet but will report back.

I've now downgraded FF to v38 which is fine; it's just FF39 that continuously crashes.
Maybe this will help it also keeps seamonkey up to date through system updates(so in other words it adds a ppa)   
```
echo -e "deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main" | sudo tee -a /etc/apt/sources.list > /dev/null

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29

sudo apt-get update

sudo apt-get install seamonkey-mozilla-build
```
Just another way is all.
Regards

---

### Post by monkeybrain20122 on 2015-07-10
> **ajgreeny said:**
> Where is that config file for freshplayer and what is its name?
I do not have any such file in my system so I'm not sure where it should go in my next attempt.


In case you want to build freshplayer I built with the options 
```
-DCMAKE_BUILD_TYPE=RelWithDebInfo -DWITH_HWDEC=1 -DWITH_GLES2=0

```

The sample .config file is in the "data" subfolder in the freshplayer directory. Edit and change its name (remove .sample) and place it in ~/.config

DWITH_GLES2=0 because otherwise I get black screen with only audio, your hardware may not need it. If videos are breaking up just disable vaapi or vdpau (whichever you use) in the .config file and restart Firefox.

Edited: also I compiled against ffmpeg instead of avconv (I don't have the standard libav-dev files in my system), not sure if that has anything to do with whether it crashes Firefox though.

---

### Post by ajgreeny on 2015-07-10
Just as a test I have updated again to FF39,  and even after trying it with the config file you suggested, and disabling both vaapi and vdpau FF FF still crashed.

As another test I removed the freshplayerplugin, and reinstalled flashplugin-installer and once again FF seems to be stable.  I'll keep trying it for a long time but flash sites now have not crashed in over an hour; when using freshplayerplugin I could not run for more than a minute or two.

So in my situation with Xubuntu 14.04 64bit on an Intel i5-3570K using only the intel integrated HD4000 graphics it was almost certainly freshplayerplugin that was my problem.

PS:  I Have installed the FF add-on to disable pocket, reader and hello, as mentioned by runrickus.
[https://addons.mozilla.org/en-US/firefox/addon/disable-hello-pocket-reader/?src=hp-dl-upandcoming](https://addons.mozilla.org/en-US/firefox/addon/disable-hello-pocket-reader/?src=hp-dl-upandcoming)

---

### Post by monkeybrain20122 on 2015-07-10
> **ajgreeny said:**
> Just as a test I have updated again to FF39,  and even after trying it with the config file you suggested, and disabling both vaapi and vdpau FF FF still crashed.



I don't know when was the last time you got freshplayer update from the ppa. But some options were added to the .config rather recently (around the last 10 days or so) so perhaps don't apply to older builds.

---

### Post by ajgreeny on 2015-07-12
> **monkeybrain20122 said:**
> I don't know when was the last time you got freshplayer update from the ppa. But some options were added to the .config rather recently (around the last 10 days or so) so perhaps don't apply to older builds.
I am using the most recent update for freshplayer from the nilarimogard-webupd8 ppa repository, and have now managed to get it to work fine with FF39.

I thought I had edited the conf file to disable both vdpau and vaapi but stupidly had left the edited file open and unsaved.  Having now edited and saved it properly all is now working well.

---

### Post by monkeybrain20122 on 2015-07-12
> **ajgreeny said:**
> I am using the most recent update for freshplayer from the nilarimogard-webupd8 ppa repository, and have now managed to get it to work fine with FF39.

I thought I had edited the conf file to disable both vdpau and vaapi but stupidly had left the edited file open and unsaved.  Having now edited and saved it properly all is now working well.

Good to hear that. Enjoy your FF 39. :)

---

