---
title: "installed a mythtv client, very choppy video on All meida (tv,video etc)"
date: 2007-01-24
forum: General Help
---

### Post by zeltak on 2007-01-24
Hi all

i just installed my mythtv client pc today (p4 1.5, 512 mb RdRAM,ATI radeon 9500). All seems to go well except i am having major playback issue. all my live tv,playback of tv records and media library files (avi,mpeg,divx etc..) are very choppy when played. The sound seems to work ok. The music module gives me an error about "Decoder error. DecoderMAD: Failed to open input. Error 5.". i have been able to connect to the backend and watch live tv (in bad quality) and see the program guide so i assume its not a connection problem. the choppy playback also happens in Xine as well but works well in vnc.

any idea guys?

thx

Zeltak

---

### Post by SyvanX on 2007-01-24
Is your MythTV frontend on a separate machine from the backend?  I've had trouble with bandwidth over a wireless network, which seemed to cause choppy playback.  Is your data crossing a wireless network at some point, or is there some bandwidth sink on your frontend?

Try opening mythfrontend from a terminal window, which should display any errors back to that terminal.

---

### Post by zeltak on 2007-01-24
thx for the answer

the mythtv frontend is on a seprate machine and over a wired network (LAN). The strange thing is that vlc works perfectly. 

thx

Zeltak

---

### Post by SyvanX on 2007-01-24
Your VLC is playing your recorded programs (/var/lib/mythtv/*.mpg) ok?  If so, that's strange, especially since your graphics card should have no problem with the frontend.  I think the frontend wants to use OpenGL, but the 9500 should support that anyway.  If you haven't tried a recording in VLC, copy one from your mythtv directory to your mythvideo directory, that should allow you to open it with your mythvideo player.  That should show you if you have a transfer speed problem, or just an internal myth player.

try running mythfrontend from a terminal and post any output, that should help diagnose the problem.  

I have a frontend / backend running flawlessly on lower specs than that, also serving to a frontend (over wireless, just fast enough).  The only thing I can think of offhand is that your computer is using a bunch of bandwidth some other way, restricting mythtv.

---

### Post by zeltak on 2007-01-24
ok a few things

first i was mistaken about VLC. i get the same very poor quality playback with vnc as well. i also tried playing the recording mpg and other files as well (divx,etc..) localy (copied it to the client HD) and i get the same problems with all of them as well.
Attached is the output requested

thx again

zeltak

---

### Post by vigleik on 2007-01-24
If you also get poor quality with VLC, then MythTV is most likely not to blame. Which graphics driver are you using? Maybe you need to use the ATI driver instead of whatever driver you are using. To check how well the graphics card is working, do the following:

$sudo apt-get update
$sudo apt-get install glxgears
$glxgears -printfps

and see how many frames per second you get. It should be several thousand, if you have acceleration going. If you get a low number you really need to try changing the driver. Maybe use easyubuntu to change the driver?

---

### Post by SyvanX on 2007-01-24
you keep referencing 'vnc.'  Are you using desktop sharing to view the mythfrontend, or do you mean vlc instead of vnc?

If you are using vnc to view the mythfrontend I could imagine that there would be severe playback issues.

---

### Post by zeltak on 2007-01-25
oops sorry, its VLC of course :)

did the output file reveal anything? i noticed a suspicious part in the terminal when i run mythfronend manually:

2007-01-24 21:16:52.688 TV: Attempting to change from None to WatchingLiveTV
2007-01-24 21:16:52.690 Using protocol version 31
2007-01-24 21:16:53.970 DPMS Deactivated
2007-01-24 21:16:54.262 AFD: Opened codec 0x9d8f240, id(MPEG2VIDEO) type(Video)
2007-01-24 21:16:54.339 AFD: Opened codec 0x9d8ec00, id(MP2) type(Audio)
2007-01-24 21:16:54.629 Opening OSS audio device '/dev/dsp'.
2007-01-24 21:16:54.714 VideoOutputXv: XvMCTex: Init failed
2007-01-24 21:16:54.716 VideoOutputXv Error: Could not find suitable XVideo surf
ace.
2007-01-24 21:16:54.717 VideoOutputXv: Falling back to X shared memory video out
put.
*** May be slow ***
2007-01-24 21:17:01.397 TV: Changing from None to WatchingLiveTV
2007-01-24 21:17:01.405 New DB connection, total: 3
2007-01-24 21:17:01.408 Realtime priority would require SUID as root.
2007-01-24 21:17:01.442 Connected to database 'mythconverg' at host: 192.168.0.7
2007-01-24 21:17:01.597 Video timing method: USleep with busy wait
2007-01-24 21:17:03.116 NVP: prebuffering pause
2007-01-24 21:17:04.324 NVP: prebuffering pause
2007-01-24 21:17:05.554 NVP: prebuffering pause
2007-01-24 21:17:07.087 NVP: prebuffering pause
2007-01-24 21:17:07.457 VideoOutputXv Error:
***
* Your system is not capable of displaying the
* full framerate at 800x600 resolution. Frames
* will be skipped in order to keep the audio and
* video in sync.

thx

Zeltak

---

### Post by SyvanX on 2007-01-25
It looks like your problem with "XvMCTex: Init failed" shouldn't be the problem.
see this old email: [http://threebit.net/mail-archive/mythtv-dev/msg03726.html](http://threebit.net/mail-archive/mythtv-dev/msg03726.html)
One forum seems to think this might be the cause of the problem though.

When I was running a remote frontend over a wireless connection, I was getting Prebuffering pauses also, I just figured the wireless card was bad, because my other frontend runs fine on wireless.  I'm guessing that was probably a problem with the graphics card config.

Here are some potential causes / fixes:
**Probably your problem**: [http://www.mythtvtalk.com/forum/viewtopic.php?t=4386&start=0](http://www.mythtvtalk.com/forum/viewtopic.php?t=4386&start=0)
**old**: [http://mythtv.org/pipermail/mythtv-dev/2004-April/020958.html](http://mythtv.org/pipermail/mythtv-dev/2004-April/020958.html)
**you are on PAL tv**: [http://gentoo-wiki.com/HOWTO_Setup_MythTV](http://gentoo-wiki.com/HOWTO_Setup_MythTV)

---

