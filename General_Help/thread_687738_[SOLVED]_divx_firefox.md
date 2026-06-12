---
title: "[SOLVED] divx firefox"
date: 2008-02-04
forum: General Help
---

### Post by tjwoosta on 2008-02-04
i have recently reinstalled ubuntu because my previous version was only 32 bit. After the reinstalation i have been unable to play divx videos at stage6. I have done
```
sudo apt-get install ubuntu-restricted-extras
```
I have gone to synaptic and downloaded the totem-mozilla file
I have also installed a whole bunch of different gstreamer files because i could not find the right one
the truth is i dont know what the hell im doing and i can't get stage6 to play
Do i have conflicting programs? 
What can i do to fix this?


here is a copy of what happens in terminal when i try to play a stage6 video

```
tj@tj-laptop:~$ firefox
** Message: NP_Initialize
** Message: NP_Initialize succeeded
** Message: totemPlugin ctor [0x1c50e40]
** Message: Init mimetype 'video/divx' mode 1
** Message: Base URI is 'http://www.stage6.com/'
** Message: Real mimetype for 'video/divx' is 'video/x-msvideo'
argv[0] id divx-plugin2169788
argv[1] src http://video.stage6.com/2169788/.divx
argv[2] type video/divx
argv[3] pluginspage http://go.divx.com/plugin/download/
argv[4] showpostplaybackad false
argv[5] statuscallback dv.status_callback
argv[6] custommode Stage6
argv[7] disabledimmer true
argv[8] height 384
argv[9] width 645
** Message: mSrc: http://video.stage6.com/2169788/.divx
** Message: mCache: 0
** Message: mControllerHidden: 0
** Message: mShowStatusbar: 0
** Message: mHidden: 0
** Message: mAudioOnly: 0
** Message: mAutostart: 1, mRepeat: 0
** Message: Launching: /usr/lib/totem/totem-plugin-viewer --plugin-type mully --user-agent Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.8.1.11) Gecko/20071204 Ubuntu/7.10 (gutsy) Firefox/2.0.0.11 --mimetype video/x-msvideo 
** Message: Viewer spawned, PID 13179
** Message: GetValue variable 14 (e)
** Message: Initial window set, XID 2e00f18 size 645x384
** Message: No viewer proxy yet, deferring SetWindow
** Message: GetValue variable 15 (f)
** Message: Unhandled variable NPPVpluginScriptableNPObject
** Message: GetValue variable 11 (b)
** Message: GetValue variable 268435466 (1000000a)
** Message: GetScriptable [0x1c50e40]
** Message: totemMullYPlugin ctor [0x1faf100]
** Message: Viewer DBus interface name is 'org.gnome.totem.PluginViewer_13179'
** Message: NameOwnerChanged old-owner '' new-owner ':1.25'
** Message: Viewer now connected to the bus
** Message: ViewerSetup
** Message: Calling SetWindow
** Message: NameOwnerChanged old-owner '' new-owner ':1.25'
** Message: Already have owner, why are we notified again?
** Message: GetValue variable 15 (f)
** Message: Unhandled variable NPPVpluginScriptableNPObject
** Message: GetValue variable 11 (b)
** Message: GetValue variable 268435466 (1000000a)
** Message: GetScriptable [0x1c50e40]
Viewer: SetWindow XID 48238360 size 645:384
** Message: NewStream mimetype 'application/octet-stream' URL 'http://divx-096.vo.llnwd.net/stage6vid/2169788.divx?e=1202161053&h=90a7ea9974ecff6da16b8c3cc5212ad9/.divx'
** Message: Not expecting a new stream; aborting stream
** Message: Viewer state: STOPPED
** Message: SetWindow reply
** Message: ViewerReady
** Message: IsSchemeSupported scheme 'http': yes
** Message: totem_embedded_open_internal 'fd://0' is-browser-stream 1 start-play 1
** Message: BEFORE _open
** Message: AFTER _open (ret: 1)
** Message: Viewer state: PLAYING
** Message: OpenStream reply
** Message: NewStream mimetype 'application/octet-stream' URL 'http://divx-096.vo.llnwd.net/stage6vid/2169788.divx?e=1202161053&h=90a7ea9974ecff6da16b8c3cc5212ad9/.divx'
** Message: Is unsupported mime-type 'video/x-msvideo'
** Message: StreamAsFile filename '/home/tj/.mozilla/firefox/fkvj3ea1.default/Cache/7D5084DFd01'
** Message: mBytesStreamed 21952352
** Message: DestroyStream reason 0
** Message: URLNotify URL 'http://video.stage6.com/2169788/.divx' reason 0
** Message: Viewer state: STOPPED
** Message: totem_embedded_open_internal 'file:///home/tj/.mozilla/firefox/fkvj3ea1.default/Cache/7D5084DFd01' is-browser-stream 0 start-play 0
** Message: BEFORE _open
** Message: AFTER _open (ret: 0)
** Message: totem_embedded_set_error: 'Totem could not play 'file:///home/tj/.mozilla/firefox/fkvj3ea1.default/Cache/7D5084DFd01'', 'Video codec 'DivX 5' is not handled. You might need to install additional plugins to be able to play some types of movies'
** Message: totemPlugin dtor [0x1c50e40]
** Message: NP_Shutdown
** Message: totemMullYPlugin dtor [0x1faf100]
tj@tj-laptop:~$ 

```

---

### Post by y-lee on 2008-02-04
Do you have mplayerplug-in  installed?

---

### Post by Mantis86 on 2008-02-04
Try to install a 32 -bit firefox inside your 64 bit Ubuntu installation --> [http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)

worked for me

---

### Post by tjwoosta on 2008-02-04
yes i do have mplayer plugin installed but i have disabled it because it was not working and i thought it might be conflicting with the totem-mozilla file that i installed from synaptic


i am going to try this link for 32 bit firefox, will this be slower than the 64 bit version?

---

### Post by Mantis86 on 2008-02-04
the difference wont be noticeable for firefox

---

### Post by ubuntu-freak on 2008-02-05
> **tjwoosta said:**
> yes i do have mplayer plugin installed but i have disabled it because it was not working and i thought it might be conflicting with the totem-mozilla file that i installed from synaptic


i am going to try this link for 32 bit firefox, will this be slower than the 64 bit version?

 
You can't have totem-mozilla and mozilla-mplayer installed at the same time. Use my [how-to](http://ubuntuforums.org/showthread.php?t=661833) as a guide. 
 
Nathan

---

### Post by tjwoosta on 2008-02-06
ok i have installed the firefox32 with the mplayer flash and java plugins  and it works great  but now how can i install the divx codec? can i just click install from the stage6 website? do i need to do something special to use it with firefox32? i just dont want to mess it up.

---

### Post by tjwoosta on 2008-02-06
also i still cannot play wmv files with totem it says i dont have the right codecs installed.
this is the same problem i have with the 64 bit version so basically it has not helped at all to get the 32 bit version.  i already had flash with sound and java all working on the 64 bit version, my problem has been playing wmv files and divx and whatever other codecs i need.

---

### Post by ubuntu-freak on 2008-02-06
> **tjwoosta said:**
> ok i have installed the firefox32 with the mplayer flash and java plugins  and it works great  but now how can i install the divx codec? can i just click install from the stage6 website? do i need to do something special to use it with firefox32? i just dont want to mess it up.

 
MPlayer will play it so long as you have the w32codecs. Copy the settings for mozilla-mplayer from my [how-to](http://ubuntuforums.org/showthread.php?t=661833). If you want it to stream rm, ram, rv etc, change the rm, helix and smil values from 0 to 1 in the settings conf. If yot want RealPlayer to stream them, leave them as they are. Remember to delete the pluginreg.dat also. It's all in my how-to.
 
Nathan

---

### Post by ubuntu-freak on 2008-02-06
> **tjwoosta said:**
> also i still cannot play wmv files with totem it says i dont have the right codecs installed.
this is the same problem i have with the 64 bit version so basically it has not helped at all to get the 32 bit version.  i already had flash with sound and java all working on the 64 bit version, my problem has been playing wmv files and divx and whatever other codecs i need.

 
If you had that all working before, all you needed was to remove totem-mozilla, install w64codecs, ubuntu-restricted-extras (contains codecs, java and more) and just stream with mplayer. You can't mix firefox video plugins, except for realplayer and mplayer plugins cos you can stop mplayer streaming rm media.
 
Did you even read my how-to? I'm repeating what's already there. Kinda frustrating. Hope you get it working though.
 
Nathan

---

### Post by ubuntu-freak on 2008-02-06
Sorry, you already have the restricted extras.
 
All you should need is either w32codecs or w64codecs and either totem-mozilla, xine-plugin or mozilla-mplayer - only ONE of those, they will disable each other. Good settings for mplayer is important too. I suggest you use mozilla-mplayer and copy my settings. 
 
Nathan

---

### Post by tjwoosta on 2008-02-06
i did read your thread and i have done this
```
sudo apt-get remove totem-mozilla mozilla-plugin-vlc xine-plugin kaffeine-mozilla helix-player mozilla-helix-player
```
i have also done this
```
sudo apt-get install ubuntu-restricted-extras w64codecs alsa-oss libdvdcss2 faac faad ffmpeg compizconfig-settings-manager
```
when it gets to the w64codecs it says
```
tj@tj-laptop:~$ sudo apt-get install ubuntu-restricted-extras w64codecs alsa-oss libdvdcss2 faac faad ffmpeg compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
E: Couldn't find package w64codecs
```
what did i do wrong? how else can i get the w64codecs?

---

### Post by tjwoosta on 2008-02-06
also i cant find it in synaptic 
i have main, universe, restricted, multiverse, and source code all checked in repositories

---

### Post by ubuntu-freak on 2008-02-06
> **tjwoosta said:**
> also i cant find it in synaptic 
i have main, universe, restricted, multiverse, and source code all checked in repositories

 
Did you enable the medibuntu repo as it says in my how-to?
 
Are you running a 64-bit firefox again or still using 32-bit?
 
Nathan

---

### Post by tjwoosta on 2008-02-06
it was my bad, i didnt read your how-to good enough, i skipped right over the part about medibuntu but i have finally gotten everything working pro with the 64bit version 

so thank you for all of your help and sorry to be such a pain

---

### Post by ubuntu-freak on 2008-02-06
> **tjwoosta said:**
> it was my bad, i didnt read your how-to good enough, i skipped right over the part about medibuntu but i have finally gotten everything working pro with the 64bit version 

so thank you for all of your help and sorry to be such a pain

 
Ahh okay. Maybe I should make it stand out more. 
 
All this will become easy to you in a few months, trust me. You will wonder why it was ever difficult. When I first started using Linux, I had no idea where to paste all the commands everyone posted. Seems silly now that I didn't know, but that's why I tell people where to paste them in my how-to, and where to find the terminal.
 
Glad you got it all sorted.
 
Nathan

---

