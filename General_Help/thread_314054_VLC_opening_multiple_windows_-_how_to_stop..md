---
title: "VLC opening multiple windows - how to stop."
date: 2006-12-07
forum: General Help
---

### Post by Roasted on 2006-12-07
When I double click a song, it plays in VLC.

When I double click another song, it opens a new VLC window. Both songs now play. Sounds bad.

How can I adjust VLC so when I double click a new song, it stops the first song and continues playing the one I recently selected?

---

### Post by bapoumba on 2006-12-07
Hi,
I have not been using vlc from a long time ...
> Preferences > Advanced > Check "allow only one running instance" > Save > Close vlc.
Should be close ;)

---

### Post by Roasted on 2006-12-07
Do we have the same version here? I don't see anything under advanced except CPU Settings and that doesn't help me...

---

### Post by bapoumba on 2006-12-08
```
 apt-cache policy vlc
vlc:
  Installed: 0.8.6-svn20061012.debian-1ubuntu1
  Candidate: 0.8.6-svn20061012.debian-1ubuntu1
  Version table:
 *** 0.8.6-svn20061012.debian-1ubuntu1 0
        500 http://fr.archive.ubuntu.com edgy/universe Packages
        100 /var/lib/dpkg/status

```

Okay, so I did install vlc (I had not been using it for ages), and you are correct, "allow only one running instance" is not in the menu. Sorry (my recollection is that I used it in the past. It's in the Microsoft Windows menu, but I do not use at all this OS.) :/

[https://trac.videolan.org/vlc/ticket/505]("https://trac.videolan.org/vlc/ticket/505")
Should be coming soon ;)
From what I understand, the issue is how to handle a crash in the active vlc instance.

One [thread]("http://ubuntuforums.org/showthread.php?p=1852100") has some kind of a general GNOME solution, not sure I would do that.

---

### Post by Roasted on 2006-12-08
It's just annoying because I use BEEP for mp3s and VLC for videos. But I'd rather use 1 program for everything because BEEP gets pissy as hell if I have VLC open. I can't have VLC open and just sitting idle, I have to shut it off. And even if I do, sometimes I get errors with BEEP saying it couldn't open the file.

If only Amarok didn't start screwing up on me I would of never had to do this. Arg.

---

### Post by spyrojyros_tail on 2007-03-15
Hey guys, 

If you  go into settings -> preferences, and look at the bottom right hand corner there is a button for advanced settings, click that and then click on advanced. This will open up more options and click "allow only one running instance" and click on save, and that should be it. 

Hope this helps,

---

### Post by kpkeerthi on 2007-03-15
Thanks spyrojyros_tail. Its been quite annoying though I play only videos in VLC.

---

### Post by gene6482 on 2007-04-25
i don't seem to see that option, even with that checked.

---

### Post by stchman on 2007-04-25
> **Roasted said:**
> It's just annoying because I use BEEP for mp3s and VLC for videos. But I'd rather use 1 program for everything because BEEP gets pissy as hell if I have VLC open. I can't have VLC open and just sitting idle, I have to shut it off. And even if I do, sometimes I get errors with BEEP saying it couldn't open the file.

If only Amarok didn't start screwing up on me I would of never had to do this. Arg.

Make VLC your default player for .mp3 files.  Problem solved.

---

### Post by Denja on 2007-11-17
Yeathis is  really annoying. I always use one instance but that will change reaaal soon..in ver 0.9.0.. u can check : [https://trac.videolan.org/vlc/search?q=one+instance&wiki=on&changeset=on&ticket=on](https://trac.videolan.org/vlc/search?q=one+instance&wiki=on&changeset=on&ticket=on) for more changes to come...

 	Changes between 0.8.6 and 0.9.0-svn (not released yet):
 	-------------------------------------------------------
	
 	Important notes:
 	----------------
 	 * The HTTP interface is now only available on the local machine by default.
 	   If you want to make it available from other machines, you will have to
 	   edit the ".hosts" file.
 	   - On UNIX/Linux, the file is in /usr/share/vlc/http/.hosts
 	     If you're using the old http interface, it's located in
 	     /usr/share/vlc/http/old/.hosts
 	   - On Windows they are in C:\Program Files\VideoLAN\VLC\http\.hosts and
 	     C:\Program Files\VideoLAN\VLC\http\old\.hosts
 	   - On Mac OS X, you can find it in VLC.app/Contents/MacOS/share/http/.hosts
 	     and respectively in VLC.app/Contents/MacOS/share/http/old/.hosts
 	 * This version of VLC contains a new interface for Windows and Linux. This
 	   interface lacks a few features that used to be present in vlc 0.8.6:
 	   - "Streaming wizard" and "VLM control". These features will be replaced
 	     by a better alternative in the next version. If you absolutely need these
 	     features, we advise you to keep vlc 0.8.6
 	   - Similarly, "Bookmarks" will be reintroduced in an improved version at a
 	     later point
 	  * The default for --sout-keep has changed. It's now activated by default.
 	  * The marq, mosaic and logo commands in the rc interface changed. They
 	    now require a target name as their first argument. Example:
 	    vlc --sub-filter "marq@test{marquee=Hello}" -I rc <somevideo>
 	    You can then use commands like: @test marq-marquee Goodbye
 	    These new commands are also available in the telnet interface.
 	
 	Changes:
 	--------
 	
 	Playlist:
 	 * Vastly improved playlist support:
 	    * Media library support
 	    * "Live search"
 	    * Shoutcast TV listings
 	    * Audioscrobbler/last.fm support
 	 * User definable Lua playlist scripts. See share/luaplaylist/README.txt
 	   (Default scripts open YouTube, DailyMotion, metacafe and Google Video URLs)
 	
 	Input/Demuxers:
 	  * UDP-Lite protocol (requires OS support) for RTP/AVP
 	  * Proxy support for MMSH stream
 	  * JACK audio input support
 	  * MP4 gpac and Apple chapter support
 	  * Input run time option ( improved live stream recording )
 	  * Fixed aiff stereo file
 	  * Fixed audio glitch on seek
 	  * Improved FLAC demuxer ( duration / current time / meta data )
 	  * AAC tags support
 	  * APEv1/2 tags support
 	  * Improved ID3v2 tags support
 	  * Improved Ogg/Vorbis tags support
 	  * Raw video support
 	
 	Decoders:
 	 * VP60/VP61/VP6F/VP62 support
 	 * MKV USF subtitles support
 	 * HTML based subtitles support
 	 * Flash Screen Video support
 	 * CamStudio Screen Video support
 	 * DosBox Capture support
 	 * Karl Morton's Video support
 	 * limited atrac3 support
 	 * New codec FOURCCs to support more specific files (Avid, FCP, Sony, Samsung, ...)
 	
 	Encoders:
 	 * Flash Screen Video support
 	
 	Video output and filters:
 	 * Adjust, Invert and Distort (now split into Wave, Ripple, Gradient and
 	   Psychedelic) video filters can now be streamed
 	 * New puzzle video output filter
 	 * Rewrite motion detection video filter
 	 * New extract video filter (extract Red, Green and Blue components from a
 	   video)
 	 * New sharpen video filter (increase the contrast of adjacent pixels)
 	 * New erase video filter (remove a logo from a video)
 	 * Enhancements to subtitles' renderer to support bold, italics and some HTML
 	   tags
 	 * Support for RGBA and I420 blending. This improves Mosaic CPU usage *a lot*.
 	 * New transparency mask video filter (for use with the mosaic_bridge module).
 	 * New bluescreen video filter (for use with the mosaic_bridge module). This
 	   was previously part of the mosaic module.
 	 * Fix random characters problem in RSS filter.
 	 * Add rotate-deciangle for more precision on rotate filter
 	 * Support for Intel SSE2 intruction set in chroma converters
 	 * Improved use of Intel MMX intruction set in chroma converters
 	
 	Audio output and filters
 	 * Replay gain support.
 	 * Play audio when going slower/faster ( no pitch filter yet ).
 	 * New spatializer audio filter.
 	
 	Stream output:
 	 * UDP-Lite (requires OS support) for RTP/TS encapsulation
 	
 	Interfaces:
 	 * Windows/Linux
 	   * Brand new interface for Linux and Windows, based on the Qt toolkit
 	 * All
 	   * Improved user interaction
 	   * Improved mouse gestures
 	 * Unix
 	  ](*,) * Option to allow only one running instance, using D-Bus interface.
 	   * D-Bus Interface implementing the MPRIS
 	     (Media Player Remote Interfacing specification), a common dbus control
 	     interface for media players that intends to become an xdg standard when
 	     finished: [http://wiki.xmms2.xmms.se/index.php/Media_Player_Interfaces](http://wiki.xmms2.xmms.se/index.php/Media_Player_Interfaces) .
 	   * Motion module use disk accelerometers to keep video horizontal
 	
 	 * new BDA device driver plugin for DVB-C/S/T capture cards on Microsoft
 	   Windows
 	
 	Localisations:
 	 * Persian

---

### Post by meganox on 2007-12-10
yeah hopefully in the next few weeks...

---

