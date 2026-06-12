---
title: "HELP configuring mozplugger"
date: 2004-11-18
forum: General Help
---

### Post by iminj on 2004-11-18
I recently installed MozPlugger 1.5 to stream video multimedia files to Firefox (1.0) via Totem-xine. Works great .... EXCEPT it broke my earlier ability to stream .pls (shoutcast) and .ogg files to xmms. The browser stalls when I click on a .pls or .ogg link, and xmms doesn't open.

I suspect that the solution requires a correct configuration of /etc/mozzpluggerrc. I'm looking for help from anyone with experience configuring this file.

Below is the present contents of my /etc/mozpluggerr:

thnx !! iminj



# Configure file for MozPlugger 1.5
# Commands which are not installed on your system will not be used.

video/mpeg: mpeg, mpg, mpe: MPEG animation
video/x-mpeg: mpeg, mpg, mpe: MPEG animation
video/x-mpeg2: mpv2, mp2ve: MPEG2 animation
	stream noisy ignore_errors: mplayer -really-quiet -nojoystick -nofs -wid $window -vo xv,x11 -ao esd,alsa9,oss,arts,null -zoom -osdlevel 0 -vc mpeg12 "$file" </dev/null
        nokill noisy: xine -pq "$file"
	loop: mtvp -l -W$window "$file"
	: mtvp -W$window "$file"
	loop: xanim +Av100 -Zr +W$window +q +f "$file"
	: xanim +Av100 -Zr +W$window +q +Ze +f "$file"

video/msvideo: avi: AVI animation
video/x-msvideo: avi: AVI animation
video/fli: fli, flc: FLI animation
video/x-fli: fli, flc: FLI animation
	stream noisy ignore_errors: mplayer -really-quiet -nojoystick -nofs -wid $window -vo xv,x11 -ao esd,alsa9,oss,arts,null -zoom -osdlevel 0 "$file" </dev/null
	noisy nokill: xine -pq "$file"

application/x-mplayer2: wmv,asf,mov: Windows Media
video/x-ms-asf: asf,asx,wma,wax,wmv,wvx: Windows Media
video/x-ms-wmv: wmv: Windows Media
	stream noisy ignore_errors: totem "$file" </dev/null

image/x-macpaint: pntg,mov: Quicktime animation
video/quicktime: mov,qt: Quicktime animation
video/x-quicktime: mov,qt: Quicktime animation
	stream noisy ignore_errors: totem "$file" </dev/null
	noisy nokill: xine -pq "$file"

video/dl: dl: DL animation
video/x-dl: dl: DL animation
video/sgi-movie: movie,movi,mv: SGI animation
video/x-sgi-movie: movie,movi,mv: SGI animation
video/anim: iff,anim5,anim3,anim7: IFF animation
video/x-anim: iff,anim5,anim3,anim7: IFF animation
	loop: xanim +Av100 -Zr +W$window +q +f "$file"
	: xanim +Av100 -Zr +W$window +q +Ze +f "$file"

audio/mid: midi,mid: MIDI audio file
audio/x-mid: midi,mid: MIDI audio file
audio/midi: midi,mid: MIDI audio file
audio/x-midi: midi,mid: MIDI audio file
	controls noisy: timidity "$file"
	controls: playmidi "$file"

audio/mod: mod: Soundracker audio Module
audio/x-mod: mod: Soundracker audio Module
	controls loop noisy: mikmod -q --interpolate "$file"
	controls noisy: mikmod -q --interpolate "$file"
	controls loop noisy: xmp -l --nocmd "$file"
	controls noisy: xmp --nocmd "$file"

audio/mp3: mp3: MPEG audio
audio/x-mp3: mp3: MPEG audio
audio/mpeg2: mp2: MPEG audio
audio/x-mpeg2: mp2: MPEG audio
audio/mpeg3: mp3: MPEG audio
audio/x-mpeg3: mp3: MPEG audio
audio/mpeg: mpa,abs,mpega: MPEG audio
audio/x-mpeg: mpa,abs,mpega: MPEG audio
	controls stream noisy ignore_errors: mplayer -really-quiet -ao esd,alsa9,oss,arts,null "$file" </dev/null
	controls: mpg123 -q -b 128 "$file"
	controls: mpg321 -q "$file"
	controls: splay -t 200 "$file"
	controls: amp -b 200 -q "$file"
	controls: maplay "$file"
	controls: mpeg3play "$file"
	nokill: xmms "$file"
	repeat noisy swallow(alsaplayer): alsaplayer -q "$file"

audio/mpeg-url: m3u: MPEG music resource locator
audio/x-mpeg-url: m3u: MPEG music resource locator
audio/mpegurl: m3u: MPEG music resource locator
audio/x-mpegurl: m3u: MPEG music resource locator
	controls: mpg123 -q -b 128 -@ "$file"
	controls: mpg321 -q -@ "$file"
	nokill: xmms "$file"

audio/x-ogg: ogg: OGG audio
audio/x-scpls: pls: OGG audio
application/x-ogg: ogg: OGG audio
application/ogg: ogg: OGG audio
	controls stream noisy ignore_errors: mplayer -really-quiet -ao esd,alsa9,oss,arts,null "$file" </dev/null
	controls stream noisy: ogg123 -q -b 128 "$file"
	nokill: xmms "$file"

audio/x-sidtune: sid,psid: Commodore 64 Audio
audio/sidtune: sid,psid: Commodore 64 Audio
audio/psid: psid,sid: Commodore 64 Audio
audio/x-psid: psid,sid: Commodore 64 Audio
	controls noisy: sidplay -16 -f44100 -a "$file"

audio/basic: au,snd: Basic audio file
audio/x-basic: au,snd: Basic audio file
	controls: play "$file"
	controls: sox "$file" -t .au - > /dev/audio

audio/wav:wav: Microsoft wave file
audio/x-wav:wav: Microsoft wave file
        controls: play "$file"
	controls: wavplay -q "$file"
	controls noisy: bplay "$file"
	controls: splay "$file"
	nokill: xmms "$file"
 	repeat noisy swallow(alsaplayer): alsaplayer -q "$file"

image/sun-raster: rs: SUN raster image
image/x-sun-raster: rs: SUN raster image
image/x-rgb: rgb: RGB Image
image/x-portable-pixmap: ppm: PPM Image
image/x-portable-graymap: pgm: PGM Image
image/x-portable-bitmap: pbm: PBM Image
image/x-portable-anymap: pnm: PBM Image
image/tiff: tiff,tif: TIFF image
image/x-tiff: tiff,tif: TIFF image
	repeat noisy swallow(gqview) fill: gqview -t "$file"
	repeat noisy swallow(xli) fill: xli -quiet "$file"
	repeat noisy swallow(xloadimage) fill: xloadimage -quiet "$file"
	: display -window $window -backdrop "$file"

audio/x-pn-realaudio-plugin: rpm: RealPlayer Plugin Metafile
audio/x-pn-realaudio: ra,rm,ram: Realaudio-plugin resource locator
audio/x-realaudio: ra,rm,ram: RealAudio file
application/vnd.rn-realmedia: rm: RealMedia file
application/smil: smi: RealPlayer
audio/vnd.rn-realaudio: ra,ram: RealAudio file
audio/vnd.rn-realvideo: rv: RealVideo file
        nokill stream: realplay "$file"

application/pdf: pdf: PDF file
application/x-pdf: pdf: PDF file
text/pdf: pdf: PDF file
text/x-pdf: pdf: PDF file
	repeat event_swallow(acrobatreader) fill: acroread -geometry +9000+9000 +useFrontEndProgram -tempFileTitle acrobatreader "$file"
	repeat noisy swallow(Xpdf) fill: xpdf -g +9000+9000 "$file"
	repeat noisy event_swallow(gv:) fill: gv -safer -quiet -antialias -geometry +9000+9000 "$file"

application/x-dvi: dvi: DVI file
        repeat swallow(kviewshell) fill: kdvi "$file"
	repeat swallow(xdvi) fill: xdvi -safer -hush -geometry +9000+9000 "$file"

application/x-postscript: ps: PostScript file
application/postscript: ps: PostScript file
	repeat noisy event_swallow(gv:) fill: gv -safer -quiet -antialias -geometry +9000+9000 "$file"
	repeat swallow(Pageview) fill: pageview "$file"

application/x-rtf: rtf: Rich Text Format
application/rtf: rtf: Rich Text Format
text/rtf: rtf: Rich Text Format
	repeat noisy event_swallow(Ted:) fill: Ted "$file"
	repeat noisy swallow(AbiWord) fill: abiword --nosplash --geometry +9000+9000 "$file"
	nokill: ooffice -writer -nologo "$file"
	nokill: soffice -writer -nologo "$file"
	nokill: kword "$file"

application/x-msword: doc, dot: Microsoft Word Document
application/msword: doc, dot: Microsoft Word Document
	nokill: ooffice -writer -nologo "$file"
	nokill: soffice -writer -nologo "$file"
        noisy nokill: kword "$file"
        repeat noisy swallow(AbiWord) fill: abiword --nosplash --geometry +9000+9000 "$file"

application/vnd.ms-excel: xls, xlb: Microsoft Excel Document
	repeat swallow(PluggerGnumeric) fill: gnumeric --class PluggerGnumeric "$file"

# OpenOffice MimeTypes ([http://framework.openoffice.org/documentation/mimetypes/mimetypes.html](http://framework.openoffice.org/documentation/mimetypes/mimetypes.html))
application/vnd.sun.xml.writer: sxw: OpenOffice Writer 6.0 documents
application/vnd.sun.xml.writer.template: stw: OpenOffice Writer 6.0 templates
application/vnd.sun.xml.writer.global: sxg: OpenOffice Writer 6.0 global documents
application/vnd.stardivision.writer: sdw: StarWriter 5.x documents
application/vnd.stardivision.writer-global: sgl: StarWriter 5.x global documents
application/x-starwriter: sdw: StarWriter 4.x documents
	nokill: ooffice -writer -nologo "$file"
	nokill: soffice -writer -nologo "$file"

application/vnd.sun.xml.calc: sxc: OpenOffice Calc 6.0 spreadsheets
application/vnd.sun.xml.calc.template: stc: OpenOffice Calc 6.0 templates
application/vnd.stardivision.calc: sdc: StarCalc 5.x spreadsheets
application/x-starcalc: sdc: StarCalc 4.x spreadsheets
	nokill: ooffice -calc -nologo "$file"
	nokill: soffice -calc -nologo "$file"

application/vnd.sun.xml.draw: sxd: OpenOffice Draw 6.0 documents
application/vnd.sun.xml.draw.template: std: OpenOffice Draw 6.0 templates
application/vnd.stardivision.draw: sda: StarDraw 5.x documents
application/x-stardraw: sda: StarDraw 4.x documents
	nokill: ooffice -draw -nologo "$file"
	nokill: soffice -draw -nologo "$file"

application/vnd.sun.xml.impress: sxi: OpenOffice Impress 6.0 presentations
application/vnd.sun.xml.impress.template: sti: OpenOffice Impress 6.0 templates
application/vnd.stardivision.impress: sdd: StarImpress 5.x presentations
application/vnd.stardivision.impress-packed: sdp: StarImpress Packed 5.x files
application/x-starimpress: sdd: StarImpress 4.x presentations
application/vnd.ms-powerpoint: ppt: PowerPoint
	nokill: ooffice -impress -nologo "$file"
	nokill: soffice -impress -nologo "$file"

application/vnd.sun.xml.math: sxm: OpenOffice Math 6.0 documents
application/vnd.stardivision.math: smf: StarMath 5.x documents
application/x-starmath: smf: StarMath 4.x documents
	nokill: ooffice -math -nologo "$file"
	nokill: soffice -math -nologo "$file"

---

