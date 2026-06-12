---
title: "Problem loading Miro"
date: 2008-01-18
forum: General Help
---

### Post by Muscar on 2008-01-18
When i start up miro i get this error:
```
/var/lib/python-support/python2.5/dbus_bindings.py:1: DeprecationWarning: The dbus_bindings module is not public API and will go away soon.

Most uses of dbus_bindings are applications catching the exception
dbus.dbus_bindings.DBusException. You should use dbus.DBusException
instead (this is compatible with all dbus-python versions since 0.40.2).

If you need additional public API, please contact the maintainers via
<dbus@lists.freedesktop.org>.

  from dbus.dbus_bindings import *
INFO     Starting up Miro
INFO     Version:  0.9.8.1
INFO     Revision: unknown
INFO     Loading preferences...
INFO     Starting event loop thread
INFO     Restoring database...
INFO     Connecting to /home/marcus/.miro/sqlitedb
TIMING   Database load slow: 1.996
INFO     Recomputing filters...
INFO     Spawning auto downloader...
INFO     Displaying main frame...
INFO     Creating video display...
INFO     failed() called; generating crash report.
/home/marcus/.themes/marble-look/gtk-2.0/gtkrc:49: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
INFO     *** Launching Downloader Daemon ****
WARNING  Menu item action "CheckVersion" not implemented
WARNING  Menu item action "RenameVideo" not implemented
INFO     ----- CRASH REPORT (DANGER CAN HAPPEN) -----
INFO     App:        Miro
Publisher:  Participatory Culture Foundation
Platform:   gtk-x11
Python:     2.5.1 (r251:54863, Oct  5 2007, 13:36:32) 
[GCC 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)]
Py Path:    ['/var/lib/python-support/python2.5/miro', '/usr/bin', '/usr/lib/python25.zip', '/usr/lib/python2.5', '/usr/lib/python2.5/plat-linux2', '/usr/lib/python2.5/lib-tk', '/usr/lib/python2.5/lib-dynload', '/usr/local/lib/python2.5/site-packages', '/usr/lib/python2.5/site-packages', '/usr/lib/python2.5/site-packages/Numeric', '/usr/lib/python2.5/site-packages/gst-0.10', '/var/lib/python-support/python2.5', '/usr/lib/python2.5/site-packages/gtk-2.0', '/var/lib/python-support/python2.5/gtk-2.0']
Version:    0.9.8.1
Serial:     20070719000
Revision:   unknown
Time:       Sat Jan 19 00:47:17 2008
When:       while finishing starting up

Exception
---------
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/miro/app.py", line 746, in _finishStartup
    self.videoDisplay.setVolume(config.get(prefs.VOLUME_LEVEL))
  File "/var/lib/python-support/python2.5/miro/frontend_implementation/VideoDisplay.py", line 165, in setVolume
    volumeScale = app.controller.frame.widgetTree['volume-scale']
AttributeError: MainFrame instance has no attribute 'widgetTree'

Call stack
----------
  File "threading.py", line 460, in __bootstrap
    self.run()
  File "threading.py", line 440, in run
    self.__target(*self.__args, **self.__kwargs)
  File "/var/lib/python-support/python2.5/miro/eventloop.py", line 277, in loop
    event()
  File "/var/lib/python-support/python2.5/miro/eventloop.py", line 134, in processNextIdle
    dc.dispatch()
  File "/var/lib/python-support/python2.5/miro/eventloop.py", line 66, in dispatch
    util.trapCall(when, self.function, *self.args, **self.kwargs)
  File "/var/lib/python-support/python2.5/miro/app.py", line 656, in <lambda>
    eventloop.addIdle(lambda :self._finishStartup(gatheredVideos), "Finishing startup")
  File "/var/lib/python-support/python2.5/miro/app.py", line 819, in _finishStartup
    util.failedExn("while finishing starting up")
  File "/var/lib/python-support/python2.5/miro/util.py", line 149, in failedExn
    failed(when, withExn = True, **kwargs)

Threads
-------
Current: Event Loop
Active:
 - MainThread
 - ThreadPool - 0 [Daemon]
 - ThreadPool - 2 [Daemon]
 - ThreadPool - 1 [Daemon]
 - Event Loop

INFO     ----- END OF CRASH REPORT -----
TIMING   idle (Finishing startup) too slow (4.854 secs)
WARNING  Menu item action "FastForward" not implemented
WARNING  Menu item action "Rewind" not implemented
WARNING  Menu item action "UpVolume" not implemented
WARNING  Menu item action "DownVolume" not implemented
TIMING   gtkAsyncMethod: <function _gtkInit at 0x8a9be2c> took too long: 1.360
INFO     *** Daemon ready ***
alsa
oss
pulseaudio
esd
none
file
INFO     loaded renderer 'xinerenderer'
TIMING   gtkAsyncMethod: <function initRenderers at 0x8a07f44> took too long: 5.506
TIMING   WARNING: Calling <function <lambda> at 0x8b12684> on HTTPClient: http://e.static.blip.tv/user_photo_jetset739-484.jpg too slow (5.880 secs)
TIMING   WARNING: Calling <function <lambda> at 0x926eed4> on HTTPClient: http://www.theonion.com/content/themes/onion/assets/onn/itunes_med.jpg too slow (0.631 secs)
TIMING   WARNING: Calling <function <lambda> at 0x92656bc> on HTTPClient: http://www.democracynow.org/images/dn-logo-for-itunes.jpg too slow (0.763 secs)
TIMING   WARNING: Calling <function <lambda> at 0x9250614> on HTTPClient: http://feeds.feedburner.com/TEDTalks_video too slow (3.876 secs)
TIMING   feed update for: http://www.onnetworks.com/videos/shows/25/podcast/hd too slow (1.260 secs)
TIMING   idle (Thread Pool Callback (Feedparser callback - http://www.onnetworks.com/videos/shows/25/podcast/hd)) too slow (1.413 secs)
TIMING   feed update for: http://jetset.blip.tv/?skin=rss too slow (1.274 secs)
TIMING   idle (Thread Pool Callback (Feedparser callback - http://jetset.blip.tv/?skin=rss)) too slow (1.290 secs)
TIMING   WARNING: Calling <function <lambda> at 0x926502c> on HTTPClient: http://feeds.feedburner.com/AskANinja too slow (4.025 secs)
TIMING   WARNING: Calling <function <lambda> at 0x925dfb4> on HTTPClient: http://feeds.feedburner.com/Theburg/ too slow (0.886 secs)
TIMING   WARNING: Calling <function <lambda> at 0x8aa217c> on HTTPClient: http://feeds.feedburner.com/Terravideos too slow (11.321 secs)
TIMING   timeout (Save database) too slow (0.771 secs)
TIMING   feed update for: http://revision3.com/diggnation/feed/quicktime-large too slow (1.659 secs)
TIMING   idle (Thread Pool Callback (Feedparser callback - http://revision3.com/diggnation/feed/quicktime-large)) too slow (1.660 secs)
TIMING   feed update for: http://www.democracynow.org/podcast-video.xml too slow (0.894 secs)
TIMING   idle (Thread Pool Callback (Feedparser callback - http://www.democracynow.org/podcast-video.xml)) too slow (0.895 secs)
INFO     WARNING: error in Feed.update for Feed - http://www.kqed.org/.pod/questvideo -- <class 'httpclient.ConnectionError'>: Can't connect -- Connection Error: No address associated with hostname
TIMING   feed update for: http://feeds.feedburner.com/TEDTalks_video too slow (8.236 secs)
TIMING   idle (Thread Pool Callback (Feedparser callback - http://feeds.feedburner.com/TEDTalks_video)) too slow (8.237 secs)
TIMING   idle (Thread Pool Callback (Feedparser callback - http://feeds.feedburner.com/TEDTalks_video)) cumulative is too slow (8.237 secs)
TIMING   feed update for: http://feeds.feedburner.com/Theburg/ too slow (2.121 secs)
TIMING   idle (Thread Pool Callback (Feedparser callback - http://feeds.feedburner.com/Theburg/)) too slow (2.124 secs)
TIMING   feed update for: http://feeds.feedburner.com/AskANinja too slow (1.351 secs)
TIMING   idle (Thread Pool Callback (Feedparser callback - http://feeds.feedburner.com/AskANinja)) too slow (1.392 secs)
TIMING   timeout (Save database) too slow (10.068 secs)
TIMING   timeout (Save database) cumulative is too slow (11.082 secs)
TIMING   WARNING: Calling <function <lambda> at 0x92650d4> on HTTPClient: http://feeds.feedburner.com/tmv too slow (0.900 secs)
TIMING   WARNING: Calling <function <lambda> at 0x92cbbc4> on HTTPClient: http://revision3.com/static/images/shows/diggnation/2007-12-13kilofv/screenshot.jpg too slow (1.038 secs)
TIMING   WARNING: Calling <function <lambda> at 0xa9aeaac> on HTTPClient: http://ted.streamguys.net/TEDTalksvideo_tile.jpg too slow (1.358 secs)
TIMING   feed update for: http://www.telemusicvision.com/videos/rss.php too slow (1.339 secs)
TIMING   idle (Thread Pool Callback (Feedparser callback - http://www.telemusicvision.com/videos/rss.php)) too slow (1.340 secs)
TIMING   WARNING: Calling <function <lambda> at 0xa9aea3c> on HTTPClient: http://creativecommons.org/images/public/somerights20.gif too slow (0.521 secs)
TIMING   feed update for: http://feeds.feedburner.com/Terravideos too slow (7.820 secs)
TIMING   idle (Thread Pool Callback (Feedparser callback - http://feeds.feedburner.com/Terravideos)) too slow (7.824 secs)
TIMING   idle (Thread Pool Callback (Feedparser callback - http://feeds.feedburner.com/Terravideos)) cumulative is too slow (7.824 secs)
TIMING   timeout (Save database) too slow (4.681 secs)
TIMING   WARNING: Calling <function <lambda> at 0xaa53e79c> on HTTPClient: http://revision3.com/static/images/shows/diggnation/2007-12-06joesixpack/screenshot.jpg too slow (0.936 secs)
TIMING   WARNING: Calling <function <lambda> at 0xa9aed4c> on HTTPClient: http://mirror7.video.blip.tv/user_photo_theburgtv201.jpg too slow (0.812 secs)
TIMING   WARNING: Calling <function <lambda> at 0xaa53e3e4> on HTTPClient: http://revision3.com/static/images/shows/diggnation/2007-11-29mlohmiller/screenshot.jpg too slow (0.812 secs)
TIMING   WARNING: Calling <function <lambda> at 0x92cbbc4> on HTTPClient: http://www.telemusicvision.com/images/TMV-logo.gif too slow (0.699 secs)
TIMING   WARNING: Calling <function <lambda> at 0x92cb144> on HTTPClient: http://revision3.com/static/images/shows/diggnation/2007-11-22dagosn/screenshot.jpg too slow (0.684 secs)
TIMING   WARNING: Calling <function <lambda> at 0xaa53e3e4> on HTTPClient: http://revision3.com/static/images/shows/diggnation/2007-11-08thepierre/screenshot.jpg too slow (0.783 secs)
TIMING   WARNING: Calling <function <lambda> at 0xa9aee2c> on HTTPClient: http://revision3.com/static/images/shows/diggnation/2007-11-15jmp2071/screenshot.jpg too slow (0.815 secs)
TIMING   WARNING: Calling <function <lambda> at 0xa9ae994> on HTTPClient: http://revision3.com/static/images/shows/diggnation/2007-11-01erisar/screenshot.jpg too slow (0.702 secs)
TIMING   WARNING: Calling <function <lambda> at 0xa9aec6c> on HTTPClient: http://revision3.com/static/images/shows/diggnation/2007-10-25popltree2/screenshot.jpg too slow (0.644 secs)
TIMING   WARNING: Calling <function <lambda> at 0xaa53e534> on HTTPClient: http://revision3.com/static/images/shows/diggnation/2007-10-18arcticfox/screenshot.jpg too slow (0.596 secs)
TIMING   WARNING: Calling <function <lambda> at 0xaa53e3e4> on HTTPClient: http://revision3.com/static/images/shows/diggnation/2007-10-11logant/screenshot.jpg too slow (0.519 secs)
TIMING   WARNING: Calling <function <lambda> at 0xa9ae9cc> on HTTPClient: http://revision3.com/static/images/shows/diggnation/2007-10-04London/screenshot.jpg too slow (0.521 secs)
TIMING   WARNING: Calling <function <lambda> at 0xa9aec6c> on HTTPClient: http://revision3.com/static/images/shows/diggnation/2007-09-27masherscf/screenshot.jpg too slow (0.552 secs)
TIMING   WARNING: Calling <function <lambda> at 0xaa53e534> on HTTPClient: http://revision3.com/static/images/shows/diggnation/2007-09-20travislopes/screenshot.jpg too slow (0.562 secs)
TIMING   WARNING: Calling <function <lambda> at 0xa19e924> on HTTPClient: http://revision3.com/static/images/shows/diggnation/2007-09-13arrogantb/screenshot.jpg too slow (0.507 secs)
TIMING   WARNING: Calling <function <lambda> at 0xabfcdbc> on HTTPClient: http://revision3.com/static/images/shows/diggnation/2007-08-23moylans/screenshot.jpg too slow (0.585 secs)
TIMING   WARNING: Calling <function <lambda> at 0xaa53e534> on HTTPClient: http://revision3.com/static/images/shows/diggnation/2007-08-16stone/screenshot.jpg too slow (0.680 secs)
TIMING   WARNING: Calling <function <lambda> at 0xa19e924> on HTTPClient: http://revision3.com/static/images/shows/diggnation/2007-08-02racer5/screenshot.jpg too slow (0.592 secs)
TIMING   WARNING: Calling <function <lambda> at 0xabfce2c> on HTTPClient: http://revision3.com/static/images/shows/diggnation/2007-07-26multipass/screenshot.jpg too slow (0.638 secs)
TIMING   WARNING: Calling <function <lambda> at 0x8b12374> on HTTPClient: http://e.static.blip.tv/Jetset-politicalMadnessInsaneSportsGOS651.jpg too slow (1.351 secs)
TIMING   WARNING: Calling <function <lambda> at 0xaa53e3e4> on HTTPClient: http://e.static.blip.tv/Jetset-cesLosersMacbookAirMusicFileSharing200.jpg too slow (1.805 secs)
TIMING   WARNING: Calling <function <lambda> at 0xabfcb1c> on HTTPClient: http://e.static.blip.tv/Jetset-wonderfullyBizarreCommentInterpretations316.jpg too slow (2.195 secs)
TIMING   WARNING: Calling <function <lambda> at 0xabfce9c> on HTTPClient: http://e.static.blip.tv/Jetset-oneCrazyEffingYear407.jpg too slow (1.770 secs)
TIMING   timeout (Save database) cumulative is too slow (5.350 secs)
TIMING   WARNING: Calling <function <lambda> at 0xabfc87c> on HTTPClient: http://e.static.blip.tv/Jetset-giftGuideSantasDepressionLaptopGiving122.jpg too slow (1.603 secs)
TIMING   WARNING: Calling <function <lambda> at 0xabfc924> on HTTPClient: http://e.static.blip.tv/Jetset-illegalBeautyWutangEverydayNormalGuySuperluckycat820.jpg too slow (1.627 secs)
TIMING   WARNING: Calling <function <lambda> at 0xabfcaac> on HTTPClient: http://e.static.blip.tv/Jetset-rockBandTipsAndTricksSantaconSeesmic998.png too slow (1.753 secs)
TIMING   WARNING: Calling <function <lambda> at 0xabfc95c> on HTTPClient: http://e.static.blip.tv/Jetset-hotTop5HowToNotMasterGuitarHeroJelly795.jpg too slow (1.892 secs)
TIMING   WARNING: Calling <function <lambda> at 0xabfc8b4> on HTTPClient: http://e.static.blip.tv/Jetset-howToGetFreeMusicCrowdsourcingRcrdLbl942.png too slow (2.709 secs)
TIMING   WARNING: Calling <function <lambda> at 0xabfc7d4> on HTTPClient: http://e.static.blip.tv/Jetset-takingNoSh1tInternetLoveSongWritersGuild857.png too slow (2.572 secs)
TIMING   WARNING: Calling <function <lambda> at 0xabfcd84> on HTTPClient: http://e.static.blip.tv/Jetset-niggyTardustFreakoutsTheMaeShiJailbreakme199.png too slow (2.168 secs)
TIMING   WARNING: Calling <function <lambda> at 0xabfc8b4> on HTTPClient: http://e.static.blip.tv/Jetset-epicfuZombiesIndieMusicGuitarHero492.png too slow (1.841 secs)
TIMING   WARNING: Calling <function <lambda> at 0x926509c> on HTTPClient: http://telemusicvision-server.com/static/tmv_thumbs/Koldproduk-Hush.jpg too slow (0.996 secs)
TIMING   WARNING: Calling <function <lambda> at 0xabfcd14> on HTTPClient: http://telemusicvision-server.com/static/tmv_thumbs/The.Faint-Agenda.Suicide.jpg too slow (1.333 secs)
TIMING   WARNING: Calling <function <lambda> at 0xabfcc6c> on HTTPClient: http://telemusicvision-server.com/static/tmv_thumbs/Basement.Jaxx_Take.Me.Back.To.Your.House.jpg too slow (1.219 secs)
TIMING   WARNING: Calling <function <lambda> at 0xabfcd4c> on HTTPClient: http://telemusicvision-server.com/static/tmv_thumbs/devandrabanhart.jpeg too slow (1.646 secs)
TIMING   WARNING: Calling <function <lambda> at 0xabfcdf4> on HTTPClient: http://telemusicvision-server.com/static/tmv_thumbs/The.Soviettes-Multiply.and.Divide.jpg too slow (1.345 secs)
TIMING   WARNING: Calling <function <lambda> at 0xabfc80c> on HTTPClient: http://telemusicvision-server.com/static/tmv_thumbs/antipop.consortium-ghostlawns.jpg too slow (1.216 secs)
INFO     Shutting down Downloader...
INFO     Shutting down Downloader...
INFO     Shutting down downloaders...
INFO     Shutdown complete
INFO     Closing Database...
INFO     Shutting down event loop
INFO     Shutting down frontend
Killed

```

:confused:

---

### Post by Muscar on 2008-01-19
HELLO!! I really need help on this. stop viewing without replying!

---

### Post by kellemes on 2008-01-19
> **Muscar said:**
> HELLO!! I really need help on this. stop viewing without replying!


Well, ok. ;-)

Sorry, I don't have the answer.. :(

---

