---
title: "Chrome wont load flash plug in on Chrobuntu using Chromebook"
date: 2013-02-04
forum: General Help
---

### Post by fritz269 on 2013-02-04
I installed chrUbuntu 12.4 on my Acer C7 Chromebook and it came with a chrome browser install. I upgrated to 12.10 and It seemed to be working fine until recently I cannot load the flash plug in. I downloaded Chromium and it works fine but it bothers me that I cannot use the original chrome install. My coworked informed me that he has the same issue with his chromebook but we can't seem to fix the issue. If i cannot get the plug ins working then how would I uninstall the original chrome browser and just keep the chromium browser? Thanks to everyone..I have always had good luck with this forum so lets hope it wont fail me now.

---

### Post by dan000 on 2013-02-04
Can you check chrome://plugins and see if you have multiple Flash installed? I wonder if Chrome's PepperFlash is conflicting with the system-installed Adobe Flash.

---

### Post by fritz269 on 2013-02-04
> **dan000 said:**
> Can you check chrome://plugins and see if you have multiple Flash installed? I wonder if Chrome's PepperFlash is conflicting with the system-installed Adobe Flash.

I don't think so but here is the plugins for Chrome

Plug-ins (4)		
Details
libpepflashplayer (8 files)
Name:	
Version:	
Location:	/opt/google/chrome/PepperFlash/libpepflashplayer.so
Type:	NPAPI
 	 Disable
Name:	Chrome Remote Desktop Viewer
Description:	This plugin allows you to securely access other computers that have been shared with you. To use this plugin you must first install the Chrome Remote Desktop webapp.
Version:	
Location:	internal-remoting-viewer
Type:	PPAPI (in-process)
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/vnd.chromium.remoting-viewer		
.
Name:	Native Client
Version:	
Location:	/opt/google/chrome/libppGoogleNaClPluginChrome.so
Type:	PPAPI (in-process)
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/x-nacl	Native Client Executable	
.nexe
Name:	iTunes Application Detector
Description:	This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.
Version:	
Location:	/usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so
Type:	NPAPI
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/itunes-plugin		
Name:	VLC Multimedia Plugin (compatible Totem 3.4.3)
Description:	The Totem 3.4.3 plugin handles video and audio streams.
Version:	
Location:	/usr/lib/mozilla/plugins/libtotem-cone-plugin.so
Type:	NPAPI
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/x-vlc-plugin	VLC Multimedia Plugin	
application/vlc	VLC Multimedia Plugin	
video/x-google-vlc-plugin	VLC Multimedia Plugin	
application/x-ogg	Ogg multimedia file	
.ogg
application/ogg	Ogg multimedia file	
.ogg
audio/ogg	Ogg Audio	
.oga
audio/x-ogg	Ogg Audio	
.ogg
video/ogg	Ogg Video	
.ogv
video/x-ogg	Ogg Video	
.ogg
application/annodex	Annodex exchange format	
.anx
audio/annodex	Annodex Audio	
.axa
video/annodex	Annodex Video	
.axv
video/mpeg	MPEG video	
.mpg	.mpeg	.mpe
audio/wav	WAV audio	
.wav
audio/x-wav	WAV audio	
.wav
audio/mpeg	MP3 audio	
.mp3
application/x-nsv-vp3-mp3	NullSoft video	
.nsv
video/flv	Flash video	
.flv
video/webm	WebM video	
.webm
application/x-totem-plugin	Totem Multimedia plugin	
audio/midi	MIDI audio	
.mid	.midi
Name:	Windows Media Player Plug-in 10 (compatible; Totem)
Description:	The Totem 3.4.3 plugin handles video and audio streams.
Version:	
Location:	/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so
Type:	NPAPI
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/x-mplayer2	AVI video	
.avi	.wma	.wmv
video/x-ms-asf-plugin	ASF video	
.asf	.wmv
video/x-msvideo	AVI video	
.asf	.wmv
video/x-ms-asf	ASF video	
.asf
video/x-ms-wmv	Windows Media video	
.wmv
video/x-wmv	Windows Media video	
.wmv
video/x-ms-wvx	Windows Media video	
.wmv
video/x-ms-wm	Windows Media video	
.wmv
video/x-ms-wmp	Windows Media video	
.wmv
application/x-ms-wms	Windows Media video	
.wms
application/x-ms-wmp	Windows Media video	
.wmp
application/asx	Microsoft ASX playlist	
.asx
audio/x-ms-wma	Windows Media audio	
.wma
Name:	DivX® Web Player
Description:	DivX Web Player version 1.4.0.233
Version:	
Location:	/usr/lib/mozilla/plugins/libtotem-mully-plugin.so
Type:	NPAPI
 	 Disable
MIME types:	
MIME type	Description	File extensions
video/divx	AVI video	
.divx
Name:	QuickTime Plug-in 7.6.6
Description:	The Totem 3.4.3 plugin handles video and audio streams.
Version:	
Location:	/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so
Type:	NPAPI
 	 Disable
MIME types:	
MIME type	Description	File extensions
video/quicktime	QuickTime video	
.mov
video/mp4	MPEG-4 video	
.mp4
image/x-macpaint	MacPaint Bitmap image	
.pntg
image/x-quicktime	Macintosh Quickdraw/PICT drawing	
.pict	.pict1	.pict2
video/x-m4v	MPEG-4 video	
.m4v
application/vnd.apple.mpegurl	HTTP Live Streaming playlist	
.m3u8
Disable   Always allowed
Chrome PDF Viewer
Name:	Chrome PDF Viewer
Version:	
Location:	/opt/google/chrome/libpdf.so
Type:	PPAPI (in-process)
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/pdf	Portable Document Format	
.pdf
application/x-google-chrome-print-preview-pdf	Portable Document Format	
.pdf
Disable   Always allowed
Google Talk (2 files)
Google Talk Plugin Video Accelerator version:0.1.44.23
Name:	Google Talk Plugin Video Accelerator
Description:	Google Talk Plugin Video Accelerator version:0.1.44.23
Version:	
Location:	/opt/google/talkplugin/libnpgtpo3dautoplugin.so
Type:	NPAPI
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/vnd.gtpo3d.auto	O3D MIME	
Name:	Google Talk Plugin
Description:	Version: 3.10.2.0
Version:	
Location:	/opt/google/talkplugin/libnpgoogletalk.so
Type:	NPAPI
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/googletalk	Google Talk Plugin	
.googletalk
Disable   Always allowed
Adobe Flash Player (2 files) - Version: 11.5.31.138
Shockwave Flash 11.5 r31
Name:	Shockwave Flash
Description:	Shockwave Flash 11.5 r31
Version:	11.5.31.138
Location:	/home/fritz269/.config/google-chrome/PepperFlash/11.5.31.138/libpepflashplayer.so
Type:	PPAPI (out-of-process)
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/x-shockwave-flash	Shockwave Flash	
.swf
application/futuresplash	Shockwave Flash	
.spl
Name:	Shockwave Flash
Version:	11.2 r202
Location:	/usr/lib/flashplugin-installer/libflashplayer.so
Type:	NPAPI
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/x-shockwave-flash	Shockwave Flash	
.swf
application/futuresplash	FutureSplash Player	
.spl
Disable   Always allowed

Here is the ones for Chromium

Plug-ins
Plug-ins (8)		
Details
iTunes Application Detector
This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.
Name:	iTunes Application Detector
Description:	This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.
Version:	
Location:	/usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so
Type:	NPAPI
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/itunes-plugin		
Disable   Always allowed
Chromoting Viewer
This plugin allows you to securely access other computers that have been shared with you. To use this plugin you must first install the Chrome Remote Desktop webapp.
Name:	Chromoting Viewer
Description:	This plugin allows you to securely access other computers that have been shared with you. To use this plugin you must first install the Chrome Remote Desktop webapp.
Version:	
Location:	internal-remoting-viewer
Type:	PPAPI (in-process)
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/vnd.chromium.remoting-viewer		
.
Disable   Always allowed
DivX® Web Player
DivX Web Player version 1.4.0.233
Name:	DivX® Web Player
Description:	DivX Web Player version 1.4.0.233
Version:	
Location:	/usr/lib/mozilla/plugins/libtotem-mully-plugin.so
Type:	NPAPI
 	 Disable
MIME types:	
MIME type	Description	File extensions
video/divx	AVI video	
.divx
Disable   Always allowed
Windows Media Player Plug-in 10 (compatible; Totem)
The Totem 3.4.3 plugin handles video and audio streams.
Name:	Windows Media Player Plug-in 10 (compatible; Totem)
Description:	The Totem 3.4.3 plugin handles video and audio streams.
Version:	
Location:	/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so
Type:	NPAPI
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/x-mplayer2	AVI video	
.avi	.wma	.wmv
video/x-ms-asf-plugin	ASF video	
.asf	.wmv
video/x-msvideo	AVI video	
.asf	.wmv
video/x-ms-asf	ASF video	
.asf
video/x-ms-wmv	Windows Media video	
.wmv
video/x-wmv	Windows Media video	
.wmv
video/x-ms-wvx	Windows Media video	
.wmv
video/x-ms-wm	Windows Media video	
.wmv
video/x-ms-wmp	Windows Media video	
.wmv
application/x-ms-wms	Windows Media video	
.wms
application/x-ms-wmp	Windows Media video	
.wmp
application/asx	Microsoft ASX playlist	
.asx
audio/x-ms-wma	Windows Media audio	
.wma
Disable   Always allowed
Google Talk (2 files)
Google Talk Plugin Video Accelerator version:0.1.44.23
Name:	Google Talk Plugin Video Accelerator
Description:	Google Talk Plugin Video Accelerator version:0.1.44.23
Version:	
Location:	/opt/google/talkplugin/libnpgtpo3dautoplugin.so
Type:	NPAPI
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/vnd.gtpo3d.auto	O3D MIME	
Name:	Google Talk Plugin
Description:	Version: 3.10.2.0
Version:	
Location:	/opt/google/talkplugin/libnpgoogletalk.so
Type:	NPAPI
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/googletalk	Google Talk Plugin	
.googletalk
Disable   Always allowed
QuickTime Plug-in 7.6.6
The Totem 3.4.3 plugin handles video and audio streams.
Name:	QuickTime Plug-in 7.6.6
Description:	The Totem 3.4.3 plugin handles video and audio streams.
Version:	
Location:	/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so
Type:	NPAPI
 	 Disable
MIME types:	
MIME type	Description	File extensions
video/quicktime	QuickTime video	
.mov
video/mp4	MPEG-4 video	
.mp4
image/x-macpaint	MacPaint Bitmap image	
.pntg
image/x-quicktime	Macintosh Quickdraw/PICT drawing	
.pict	.pict1	.pict2
video/x-m4v	MPEG-4 video	
.m4v
application/vnd.apple.mpegurl	HTTP Live Streaming playlist	
.m3u8
Disable   Always allowed
Adobe Flash Player - Version: 11.2 r202
Shockwave Flash 11.2 r202
Name:	Shockwave Flash
Version:	11.2 r202
Location:	/usr/lib/flashplugin-installer/libflashplayer.so
Type:	NPAPI
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/x-shockwave-flash	Shockwave Flash	
.swf
application/futuresplash	FutureSplash Player	
.spl
Disable   Always allowed
VLC Multimedia Plugin (compatible Totem 3.4.3)
The Totem 3.4.3 plugin handles video and audio streams.
Name:	VLC Multimedia Plugin (compatible Totem 3.4.3)
Description:	The Totem 3.4.3 plugin handles video and audio streams.
Version:	
Location:	/usr/lib/mozilla/plugins/libtotem-cone-plugin.so
Type:	NPAPI
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/x-vlc-plugin	VLC Multimedia Plugin	
application/vlc	VLC Multimedia Plugin	
video/x-google-vlc-plugin	VLC Multimedia Plugin	
application/x-ogg	Ogg multimedia file	
.ogg
application/ogg	Ogg multimedia file	
.ogg
audio/ogg	Ogg Audio	
.oga
audio/x-ogg	Ogg Audio	
.ogg
video/ogg	Ogg Video	
.ogv
video/x-ogg	Ogg Video	
.ogg
application/annodex	Annodex exchange format	
.anx
audio/annodex	Annodex Audio	
.axa
video/annodex	Annodex Video	
.axv
video/mpeg	MPEG video	
.mpg	.mpeg	.mpe
audio/wav	WAV audio	
.wav
audio/x-wav	WAV audio	
.wav
audio/mpeg	MP3 audio	
.mp3
application/x-nsv-vp3-mp3	NullSoft video	
.nsv
video/flv	Flash video	
.flv
video/webm	WebM video	
.webm
application/x-totem-plugin	Totem Multimedia plugin	
audio/midi	MIDI audio	
.mid	.midi
Disable   Always allowed


Do you see anything weird? Chrome plug in does not work. Chromium works.

---

### Post by dan000 on 2013-02-04
Yep. You have both Adobe Flash, and Google's PepperFlash installed in Chrome. Try disabling one of them, and see if that it that fixes things.

---

### Post by fritz269 on 2013-02-04
Ok I disabled the following and it worked.

Name:	Shockwave Flash
Description:	Shockwave Flash 11.5 r31
Version:	11.5.31.138
Location:	/home/fritz269/.config/google-chrome/PepperFlash/11.5.31.138/libpepflashplayer.so


This one is enabled

Name:	Shockwave Flash
Version:	11.2 r202
Location:	/usr/lib/flashplugin-installer/libflashplayer.so
Type:	NPAPI
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/x-shockwave-flash	Shockwave Flash	
.swf
application/futuresplash	FutureSplash Player	
.spl

So it looks like it was a confict. Thank you so much. This one is solved!

---

### Post by dan000 on 2013-02-05
Just to check things out, you might want to try disabling Adobe Flash, and enabling PepperFlash. I've heard reports that PepperFlash can be a little faster. As I understand it, Google actually worked with Adobe to develop PepperFlash specifically for Chrome (which is why it isn't in Chromium).

But either way, I'm glad to hear you got it working.

---

### Post by fritz269 on 2013-02-06
I tried disabling the PepperFlash first and it did not work. Then I tried the Adobe Flash and that worked. So im guessing there is an issue with the PepperFlash. I am sticking with the Adobe Flash unless there is an update later.

---

### Post by dan000 on 2013-02-06
Good to know. Thanks for the followup.

---

