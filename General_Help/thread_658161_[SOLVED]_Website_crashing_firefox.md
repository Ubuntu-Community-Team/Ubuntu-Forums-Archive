---
title: "[SOLVED] Website crashing firefox"
date: 2008-01-04
forum: General Help
---

### Post by tosszyx on 2008-01-04
Hi there, I have a problem with one site and apparently the MediaPlayerConnectivity plugin and VLC, firefox crashes and closes. And I would like some help to know what is wrong and if possible to fix it.

the site: [http://www.jtlopez.com/live/?p=20](http://www.jtlopez.com/live/?p=20)

Thank you very much


*************************************************************************************************
tosszyx@Coatl$ firefox &
[1] 7678
tosszyx@Coatl$
tosszyx@Coatl$ argn=src, argv= [http://donna.actlab.utexas.edu/actlab_tv/projects/weird_science_fall_2007/laser_harp.mov](http://donna.actlab.utexas.edu/actlab_tv/projects/weird_science_fall_2007/laser_harp.mov)
argn=controller, argv=true
argn=type, argv=video/quicktime
argn=autoplay, argv=false
argn=scale, argv=ASPECT
argn=pluginspage, argv=http://www.apple.com/quicktime/download/
argn=height, argv=256
argn=width, argv=320
[00000001] main private debug: checking builtin modules
[00000001] main private debug: checking plugin modules
[00000001] main private debug: loading plugins cache file /home/ule/.vlc/cache/plugins- 04041e.dat
[00000001] main private debug: recursively browsing `modules'
[00000001] main private debug: recursively browsing `/usr/lib/vlc'
[00000001] main private debug: recursively browsing `plugins'
[00000001] main private debug: module bank initialized, found 217 modules
[00000001] main private debug: opening config file /home/ule/.vlc/vlcrc
[00000001] main private debug: CPU has capabilities 486 586 MMX MMXEXT SSE SSE2 FPU
[00000001] main private debug: looking for memcpy module: 1 candidate
[00000001] main private debug: using memcpy module "memcpy"
[00000282] main playlist debug: waiting for thread completion
[00000282] main playlist debug: thread 2961857424 (playlist) created at priority 0 (playlist/playlist.c:184)
[00000283] main private debug: waiting for thread completion
[00000283] main private debug: thread 2941406096 (preparser) created at priority 0 (playlist/playlist.c:210)
[00000284] main interface debug: looking for interface module: 1 candidate
[00000284] main interface debug: using interface module "hotkeys"
[00000284] main interface debug: thread 2933013392 (interface) created at priority 0 (interface/interface.c:231)
[00000286] main interface debug: looking for interface module: 1 candidate
[00000286] main interface debug: using interface module "screensaver"
[00000286] main interface debug: thread 2858367888 (interface) created at priority 0 (interface/interface.c:231)
[00000282] main playlist debug: adding playlist item `[http://donna.actlab.utexas.edu/actlab_tv/projects/weird_science_fall_2007/laser_harp.mov](http://donna.actlab.utexas.edu/actlab_tv/projects/weird_science_fall_2007/laser_harp.mov)' ( [http://donna.actlab.utexas.edu/actlab_tv/projects/weird_science_fall_2007/laser_harp.mov](http://donna.actlab.utexas.edu/actlab_tv/projects/weird_science_fall_2007/laser_harp.mov) )
argn=src, argv= [http://donna.actlab.utexas.edu/actlab_tv/projects/weird_science_fall_2007/smoke_ring_canon_edit.mov](http://donna.actlab.utexas.edu/actlab_tv/projects/weird_science_fall_2007/smoke_ring_canon_edit.mov)
argn=controller, argv=true
argn=type, argv=video/quicktime
argn=autoplay, argv=false
argn=scale, argv=ASPECT
argn=pluginspage, argv=http://www.apple.com/quicktime/download/
argn=height, argv=256
argn=width, argv=320
[00000288] main private debug: translation test: code is "C"
[00000288] main private debug: module bank initialized, found 217 modules
[00000288] main private debug: opening config file /home/ule/.vlc/vlcrc
[00000288] main private debug: CPU has capabilities 486 586 MMX MMXEXT SSE SSE2 FPU
[00000288] main private debug: looking for memcpy module: 1 candidate
[00000288] main private debug: using memcpy module "memcpy"
[00000290] main playlist debug: waiting for thread completion
[00000290] main playlist debug: thread 2866760592 (playlist) created at priority 0 (playlist/playlist.c:184)
[00000291] main private debug: waiting for thread completion
[00000291] main private debug: thread 2849975184 (preparser) created at priority 0 (playlist/playlist.c:210)
[00000292] main interface debug: looking for interface module: 1 candidate
[00000292] main interface debug: using interface module "hotkeys"
[00000292] main interface debug: thread 2841582480 (interface) created at priority 0 (interface/interface.c:231)
[00000293] main interface debug: looking for interface module: 1 candidate
[00000293] main interface debug: using interface module "screensaver"
[00000293] main interface debug: thread 2833189776 (interface) created at priority 0 (interface/interface.c:231)
[00000290] main playlist debug: adding playlist item `[http://donna.actlab.utexas.edu/actlab_tv/projects/weird_science_fall_2007/smoke_ring_canon_edit.mov](http://donna.actlab.utexas.edu/actlab_tv/projects/weird_science_fall_2007/smoke_ring_canon_edit.mov)' ( [http://donna.actlab.utexas.edu/actlab_tv/projects/weird_science_fall_2007/smoke_ring_canon_edit.mov](http://donna.actlab.utexas.edu/actlab_tv/projects/weird_science_fall_2007/smoke_ring_canon_edit.mov) )
argn=src, argv= [http://donna.actlab.utexas.edu/actlab_tv/projects/weird_science_fall_2007/LCD_Smoke_Projection.mov](http://donna.actlab.utexas.edu/actlab_tv/projects/weird_science_fall_2007/LCD_Smoke_Projection.mov)
argn=controller, argv=true
argn=type, argv=video/quicktime
argn=autoplay, argv=false
argn=scale, argv=ASPECT
argn=pluginspage, argv=http://www.apple.com/quicktime/download/
argn=height, argv=256
argn=width, argv=320
[00000294] main private debug: translation test: code is "C"
[00000294] main private debug: module bank initialized, found 217 modules
[00000294] main private debug: opening config file /home/ule/.vlc/vlcrc
[00000294] main private debug: CPU has capabilities 486 586 MMX MMXEXT SSE SSE2 FPU
[00000294] main private debug: looking for memcpy module: 1 candidate
[00000294] main private debug: using memcpy module "memcpy"
[00000296] main playlist debug: waiting for thread completion
[00000296] main playlist debug: thread 2824797072 (playlist) created at priority 0 (playlist/playlist.c:184)
[00000297] main private debug: waiting for thread completion
[00000297] main private debug: thread 2816404368 (preparser) created at priority 0 (playlist/playlist.c:210)
[00000298] main interface debug: looking for interface module: 1 candidate
[00000298] main interface debug: using interface module "hotkeys"
[00000298] main interface debug: thread 2808011664 (interface) created at priority 0 (interface/interface.c:231)
[00000299] main interface debug: looking for interface module: 1 candidate
[00000299] main interface debug: using interface module "screensaver"
[00000299] main interface debug: thread 2799618960 (interface) created at priority 0 (interface/interface.c:231)
[00000296] main playlist debug: adding playlist item `[http://donna.actlab.utexas.edu/actlab_tv/projects/weird_science_fall_2007/LCD_Smoke_Projection.mov](http://donna.actlab.utexas.edu/actlab_tv/projects/weird_science_fall_2007/LCD_Smoke_Projection.mov)' ( [http://donna.actlab.utexas.edu/actlab_tv/projects/weird_science_fall_2007/LCD_Smoke_Projection.mov](http://donna.actlab.utexas.edu/actlab_tv/projects/weird_science_fall_2007/LCD_Smoke_Projection.mov) )
argn=src, argv= [http://donna.actlab.utexas.edu/actlab_tv/projects/weird_science_fall_2007/wards_crazy_water_project.mov](http://donna.actlab.utexas.edu/actlab_tv/projects/weird_science_fall_2007/wards_crazy_water_project.mov)
argn=controller, argv=true
argn=type, argv=video/quicktime
argn=autoplay, argv=false
argn=scale, argv=ASPECT
argn=pluginspage, argv=http://www.apple.com/quicktime/download/
argn=height, argv=256
argn=width, argv=320
[00000300] main private debug: translation test: code is "C"
[00000300] main private debug: module bank initialized, found 217 modules
[00000300] main private debug: opening config file /home/ule/.vlc/vlcrc
[00000300] main private debug: CPU has capabilities 486 586 MMX MMXEXT SSE SSE2 FPU
[00000300] main private debug: looking for memcpy module: 1 candidate
[00000300] main private debug: using memcpy module "memcpy"
[00000302] main playlist debug: waiting for thread completion
[00000302] main playlist debug: thread 2791226256 (playlist) created at priority 0 (playlist/playlist.c:184)
[00000303] main private debug: waiting for thread completion
[00000303] main private debug: thread 2782833552 (preparser) created at priority 0 (playlist/playlist.c:210)
[00000304] main interface debug: looking for interface module: 1 candidate
[00000304] main interface debug: using interface module "hotkeys"
[00000304] main interface debug: thread 2774440848 (interface) created at priority 0 (interface/interface.c:231)
[00000305] main interface debug: looking for interface module: 1 candidate
[00000305] main interface debug: using interface module "screensaver"
[00000305] main interface debug: thread 2766048144 (interface) created at priority 0 (interface/interface.c:231)
[00000302] main playlist debug: adding playlist item `[http://donna.actlab.utexas.edu/actlab_tv/projects/weird_science_fall_2007/wards_crazy_water_project.mov](http://donna.actlab.utexas.edu/actlab_tv/projects/weird_science_fall_2007/wards_crazy_water_project.mov)' ( [http://donna.actlab.utexas.edu/actlab_tv/projects/weird_science_fall_2007/wards_crazy_water_project.mov](http://donna.actlab.utexas.edu/actlab_tv/projects/weird_science_fall_2007/wards_crazy_water_project.mov) )
[00000001] main private debug: removing all interfaces
[00000286] main interface debug: thread 2858367888 joined (interface/interface.c:258)
[00000286] main interface debug: removing module "screensaver"
[00000284] main interface debug: thread 2933013392 joined (interface/interface.c:258)
[00000284] main interface debug: removing module "hotkeys"
[00000001] main private debug: removing playlist handler
[00000283] main private debug: thread 2941406096 joined (playlist/playlist.c:247)
[00000282] main playlist debug: thread 2961857424 joined (playlist/playlist.c:248)
[00000282] main playlist debug: deleting playlist item `[http://donna.actlab.utexas.edu/actlab_tv/projects/weird_science_fall_2007/laser_harp.mov](http://donna.actlab.utexas.edu/actlab_tv/projects/weird_science_fall_2007/laser_harp.mov)'
[00000001] main private debug: removing all video outputs
[00000001] main private debug: removing all audio outputs
[00000001] main private debug: removing module "memcpy"
Segmentation fault (core dumped)

[1]+  Exit 139                firefox
*****************************************************************************************************************

#### MediaPlayerConnectivity configuration report ####
MPC version=0.8.3
FF UserAgent=Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.11) Gecko/20071204 Ubuntu/7.10 (gutsy) Firefox/2.0.0.11

-Type Real Media
     active=true
     app=/usr/bin/vlc
     param=%f
     Embed=true
     ContextMenu=true
     File=true
     Autoplay=false

-Type Windows Media
     active=true
     app=/usr/bin/vlc
     param=%f
     Embed=true
     ContextMenu=true
     File=true
     Autoplay=false

-Type QuickTime
     active=true
     app=/usr/bin/vlc
     param=%f
     Embed=true
     ContextMenu=true
     File=true
     Autoplay=false

-Type Playlist (pls/m3u)
     active=true
     app=/usr/bin/gmplayer
     param=%f
     Embed=true
     ContextMenu=true
     File=true
     Autoplay=false

-Type MP3/AAC files
     active=true
     app=/usr/bin/gmplayer
     param=%f
     Embed=true
     ContextMenu=true
     File=true
     Autoplay=false

-Type OGG/Theora
     active=false
     app=
     param=%f
     Embed=true
     ContextMenu=true
     File=true
     Autoplay=false

-Type Flash
     active=false
     app=
     param=%f
     Embed=true
     ContextMenu=true
     File=true
     Autoplay=false

-Type Wave/Midi/Au/Aif
     active=true
     app=/usr/bin/gmplayer
     param=%f
     Embed=true
     ContextMenu=true
     File=true
     Autoplay=false

-Type NullSoft Video
     active=false
     app=
     param=%f
     Embed=true
     ContextMenu=true
     File=true
     Autoplay=false

-Type Shockwave
     active=false
     app=
     param=%f
     Embed=true
     ContextMenu=true
     File=true
     Autoplay=false

-Type Authorware
     active=false
     app=
     param=%f
     Embed=true
     ContextMenu=true
     File=true
     Autoplay=false

-Type Divx
     active=true
     app=/usr/bin/vlc
     param=%f
     Embed=true
     ContextMenu=true
     File=true
     Autoplay=false

-Type Podcast
     active=false
     app=
     param=%f
     Embed=true
     ContextMenu=true
     File=true
     Autoplay=false

-Type ViewPoint
     active=false
     app=
     param=%f
     Embed=true
     ContextMenu=true
     File=true
     Autoplay=false

SmartPlay=true
ClosePopUp=false
LinkIcon=false
ExpertMode=false
ActiveAppLinks=false
MenuHidden=false
HideStatusButton=false
MiniIconSize=10
MetaFileMaxSize=30 Kb
CollectLinks=false
SideBarMode=true
IsReusePopup=true
ToolbarButton=false
WhiteList=*rapidshare.de
NodeNameTable=object;embed;noembed;bgsound

Tools defined: 
     none

Installed plugins :
	Shockwave Flash (libflashplayer.so)
	VLC Multimedia Plugin (libvlcplugin.so)
	Java(TM) Plug-in 1.6.0_03-b05 (libjavaplugin_oji.so)
	DivX Browser Plug-In (mplayerplug-in-dvx.so)
	QuickTime Plug-in 6.0 / 7 (mplayerplug-in-qt.so)
	RealPlayer 9 (mplayerplug-in-rm.so)
	Windows Media Player Plugin (mplayerplug-in-wmp.so)
	mplayerplug-in 3.40 (mplayerplug-in.so)
	Kaffeine Starter Plugin (kaffeineplugin.so)
	Helix DNA Plugin: RealPlayer G2 Plug-In Compatible (nphelix.so)
######################################################

---

### Post by lahook on 2008-01-04
the website loads quicktime videos. it looks like your firefox tries to use the vlc plugin to play the videos. i think mplayer plugin might work for the videos. i would try uninstalling mozilla-vlc plugin temporarily and try the mplayer plugin. if it dosen't work you can always reinstall the vlc plugin.  
i had firefox crash on yahoo every time i tried to log into my account. it turned out i installed gnash and the free java, instead of micromedia flash and sun java. i uninstalled them and installed the others and my problem went away. 
i hope this helps you, but i'm not an expert so it's just something to try

---

### Post by tosszyx on 2008-01-05
Thank you very much, I uninstalled the vlc plugin and disable the MediaPlayerConnectivity, now the videos get played with the mozilla-mplayer and I can open the mentioned page without crashing my firefox. Now all I've to do is to make mplayer work better.

---

