---
title: "Rhythmbox and AAC?"
date: 2007-01-07
forum: General Help
---

### Post by Cable on 2007-01-07
I have configured Sound Juicer to rip AAC (.m4a) files, and that works fine.  However, I cannot for the life of me get Rhythmbox to play them.  I have installed gstreamer0.10-plugins-bad, gstreamer0.10-plugins-bad-multiverse, and any gstreamer0.8 plugins that seemed relevant but it still will not play them.  It has an error when importing the song that says something along the lines of not being able to identify the MIME type.  If I go to the file itself and look at the properties dialog, it doesn't have an audio properties tab either.  Even though I have the plugins installed, it's as if Ubuntu has no idea what an AAC or m4a file is.  Please help!

By the way, this box is running Xubuntu (just in case that matters).

Thanks for any help!

---

### Post by Travisty on 2007-01-08
I think you want the "faad" package. You should see it if you search for it or aac in Synaptic.

---

### Post by Cable on 2007-01-08
That package is installed as well.  I installed all packages that appeared relevant to AAC, and I read the wiki entries about [CD ripping]("https://help.ubuntu.com/community/CDRipping") and [playing back AAC files]("https://help.ubuntu.com/community/RestrictedFormats/AAC").  Would the gstreamer plugin(s) not register themselves with gstreamer for some reason?  I have AAC playback working perfectly on my Ubuntu box, but the Xubuntu box just doesn't want to cooperate.

---

### Post by Travisty on 2007-01-08
I checked both my Ubuntu and Kubuntu boxes and here are the packages that they share.

faac
libfaac0
gstreamer0.18-plugins-bad
gstreamer0.18-plugins-bad-multiverse
gstreamer0.18-plugins-ugly
gstreamer0.18-plugins-ugly-multiverse

You can run "gst-register" in the terminal and that should re-register all gstreamer plugins. If that still doesn't work then I think the gstreamer forums might be the way to go. Unless someone with more knowledge on this chimes in.

---

### Post by Cable on 2007-01-08
Doesn't the gst-register command only work with v0.8?  I believe it's v0.10 that is having the problems.

---

### Post by killernurd on 2007-01-17
You'll want to use 'gst-inspect' or 'gst-inspect-0.10' to handle GST 0.10 plugins.

---

### Post by Cable on 2007-01-17
I have tried everything mentioned here.  I've tried gst-inspect-0.10, I've tried purging and reinstalling the plug-ins.  I don't know what else to do.  I still cannot get this Xubuntu box to read/recognize AAC files, and yet it works perfectly on my Ubuntu box.  Any other ideas?  I would really love to get this working.

---

### Post by killernurd on 2007-01-18
Err... have you erased your current GST registry? You'll want to do that, first...

You'll also need faad and libfaad (faac is the encoder, faad is the decoder).

---

### Post by Cable on 2007-01-20
I deleted the registry.i486.xml file in the .gstreamer-0.10 directory, then did
```

$gst-inspect-0.10

```
Following is the output of that command
```

1394:  dv1394src: Firewire (1394) DV video source
a52dec:  a52dec: ATSC A/52 audio decoder
aasink:  aasink: ASCII art video sink
adder:  adder: Adder
alaw:  alawdec: A Law audio decoder
alaw:  alawenc: A Law audio encoder
alpha:  alpha: Alpha filter
alphacolor:  alphacolor: Alpha color filter
alsa:  alsadmixsink: Audio Sink (ALSA with dmix)
alsa:  alsasink: Audio sink (ALSA)
alsa:  alsasrc: Audio source (ALSA)
alsa:  alsamixer: Alsa mixer
alsaspdif:  alsaspdifsink: S/PDIF ALSA audiosink
annodex:  cmmldec: CMML stream decoder
annodex:  cmmlenc: CMML streams encoder
apetag:  apedemux: APE tag demuxer
asf:  asfdemux: ASF Demuxer
audioconvert:  audioconvert: Audio converter
audiorate:  audiorate: Audio rate adjuster
audioresample:  audioresample: Audio scaler
audiotestsrc:  audiotestsrc: Audio test source
auparse:  auparse: AU audio demuxer
autodetect:  autoaudiosink: Auto audio sink
autodetect:  autovideosink: Auto video sink
avi:  avimux: Avi muxer
avi:  avidemux: Avi demuxer
bz2:  bz2dec: BZ2 decoder
bz2:  bz2enc: BZ2 encoder
cacasink:  cacasink: A colored ASCII art video sink
cairo:  cairotimeoverlay: Time overlay
cairo:  cairotextoverlay: Text overlay
cdio:  cdiocddasrc: CD audio source (CDDA)
cdparanoia:  cdparanoiasrc: CD Audio (cdda) Source, Paranoia IV
cdxaparse:  cdxaparse: (S)VCD parser
coreelements:  typefind: TypeFind
coreelements:  tee: Tee pipe fitting
coreelements:  filesink: File Sink
coreelements:  queue: Queue
coreelements:  identity: Identity
coreelements:  filesrc: File Source
coreelements:  fdsink: Filedescriptor Sink
coreelements:  fdsrc: Disk Source
coreelements:  fakesink: Fake Sink
coreelements:  fakesrc: Fake Source
coreelements:  capsfilter: CapsFilter
coreindexers:  fileindex: A index that stores entries in file
coreindexers:  memindex: A index that stores entries in memory
cutter:  cutter: Audio cutter
debug:  testsink: Test plugin
debug:  progressreport: Progress report
debug:  navseek: Seek based on left-right arrows
debug:  breakmydata: Break my data
decodebin:  decodebin: Decoder Bin
dtsdec:  dtsdec: DTS audio decoder
dv:  dvdec: DV video decoder
dv:  dvdemux: DV system stream demuxer
dvdlpcmdec:  dvdlpcmdec: DVD LPCM Audio decoder
dvdread:  dvdreadsrc: DVD Source
dvdsub:  dvdsubdec: DVD subtitle Decoder
efence:  efence: Electric Fence
effectv:  quarktv: QuarkTV effect
effectv:  revtv: RevTV effect
effectv:  vertigotv: VertigoTV effect
effectv:  shagadelictv: ShagadelicTV
effectv:  warptv: WarpTV effect
effectv:  dicetv: DiceTV effect
effectv:  agingtv: AgingTV effect
effectv:  edgetv: EdgeTV effect
faac:  faac: AAC audio encoder
faad:  faad: AAC audio decoder
ffmpeg:  ffvideoscale: FFMPEG Scale element
ffmpeg:  ffdeinterlace: FFMPEG Deinterlace element
ffmpeg: fftype_avs: no extensions
ffmpeg:  ffdemux_avs: FFMPEG avs format demuxer
ffmpeg:  ffdemux_tta: FFMPEG true-audio demuxer
ffmpeg: fftype_voc: no extensions
ffmpeg:  ffdemux_voc: FFMPEG Creative Voice File format demuxer
ffmpeg: fftype_daud: 302
ffmpeg:  ffdemux_daud: FFMPEG D-Cinema audio format demuxer
ffmpeg: fftype_nsv: no extensions
ffmpeg:  ffdemux_nsv: FFMPEG NullSoft Video format demuxer
ffmpeg: fftype_ea: no extensions
ffmpeg:  ffdemux_ea: FFMPEG Electronic Arts Multimedia Format demuxer
ffmpeg: fftype_sol: no extensions
ffmpeg:  ffdemux_sol: FFMPEG Sierra SOL Format demuxer
ffmpeg:  ffdemux_matroska: FFMPEG Matroska file format demuxer
ffmpeg: fftype_nut: nut
ffmpeg:  ffdemux_nut: FFMPEG nut format demuxer
ffmpeg: fftype_ffm: no extensions
ffmpeg:  ffdemux_ffm: FFMPEG ffm format demuxer
ffmpeg: fftype_ogg: ogg
ffmpeg:  ffdemux_ogg: FFMPEG Ogg demuxer
ffmpeg: fftype_yuv4mpegpipe: y4m
ffmpeg:  ffdemux_yuv4mpegpipe: FFMPEG YUV4MPEG pipe format demuxer
ffmpeg: fftype_mm: no extensions
ffmpeg:  ffdemux_mm: FFMPEG American Laser Games MM format demuxer
ffmpeg: fftype_vmd: no extensions
ffmpeg:  ffdemux_vmd: FFMPEG Sierra VMD format demuxer
ffmpeg: fftype_flic: no extensions
ffmpeg:  ffdemux_flic: FFMPEG FLI/FLC/FLX animation format demuxer
ffmpeg: fftype_idcin: no extensions
ffmpeg:  ffdemux_idcin: FFMPEG Id CIN format demuxer
ffmpeg: fftype_film_cpk: no extensions
ffmpeg:  ffdemux_film_cpk: FFMPEG Sega FILM/CPK format demuxer
ffmpeg: fftype_wsvqa: no extensions
ffmpeg:  ffdemux_wsvqa: FFMPEG Westwood Studios VQA format demuxer
ffmpeg: fftype_wsaud: no extensions
ffmpeg:  ffdemux_wsaud: FFMPEG Westwood Studios audio format demuxer
ffmpeg: fftype_wc3movie: no extensions
ffmpeg:  ffdemux_wc3movie: FFMPEG Wing Commander III movie format demuxer
ffmpeg: fftype_ipmovie: no extensions
ffmpeg:  ffdemux_ipmovie: FFMPEG Interplay MVE format demuxer
ffmpeg: fftype_RoQ: no extensions
ffmpeg:  ffdemux_RoQ: FFMPEG Id RoQ format demuxer
ffmpeg: fftype_psxstr: no extensions
ffmpeg:  ffdemux_psxstr: FFMPEG Sony Playstation STR format demuxer
ffmpeg: fftype_flv: flv
ffmpeg:  ffdemux_flv: FFMPEG flv format demuxer
ffmpeg: fftype_4xm: no extensions
ffmpeg:  ffdemux_4xm: FFMPEG 4X Technologies format demuxer
ffmpeg: fftype_dv: dv,dif
ffmpeg:  ffdemux_dv: FFMPEG DV video format demuxer
ffmpeg:  ffdemux_mov_mp4_m4a_3gp_3g2: FFMPEG QuickTime/MPEG4 format demuxer
ffmpeg: fftype_gif: no extensions
ffmpeg:  ffdemux_gif: FFMPEG gif format demuxer
ffmpeg: fftype_aiff: no extensions
ffmpeg:  ffdemux_aiff: FFMPEG Audio IFF demuxer
ffmpeg:  ffdemux_au: FFMPEG SUN AU Format demuxer
ffmpeg: fftype_swf: no extensions
ffmpeg:  ffdemux_swf: FFMPEG Flash format demuxer
ffmpeg: fftype_mmf: no extensions
ffmpeg:  ffdemux_mmf: FFMPEG mmf format demuxer
ffmpeg:  ffdemux_wav: FFMPEG wav format demuxer
ffmpeg:  ffdemux_avi: FFMPEG avi format demuxer
ffmpeg:  ffdemux_asf: FFMPEG asf format demuxer
ffmpeg:  ffdemux_rm: FFMPEG rm format demuxer
ffmpeg:  ffdemux_mp3: FFMPEG MPEG audio demuxer
ffmpeg: fftype_ingenient: cgi
ffmpeg:  ffdemux_ingenient: FFMPEG Ingenient MJPEG demuxer
ffmpeg: fftype_mpegts: no extensions
ffmpeg:  ffdemux_mpegts: FFMPEG MPEG2 transport stream format demuxer
ffmpeg:  ffdemux_mpeg: FFMPEG MPEG PS format demuxer
ffmpeg:  ffdec_adpcm_sbpro_2: FFMPEG SB-Pro ADPCM 2 decoder
ffmpeg:  ffdec_adpcm_sbpro_3: FFMPEG SB-Pro ADPCM 3 decoder
ffmpeg:  ffdec_adpcm_sbpro_4: FFMPEG SB-Pro ADPCM 4 decoder
ffmpeg:  ffdec_adpcm_yamaha: FFMPEG Yamaha ADPCM decoder
ffmpeg:  ffdec_adpcm_swf: FFMPEG Shockwave ADPCM decoder
ffmpeg:  ffdec_adpcm_ct: FFMPEG CT ADPCM decoder
ffmpeg:  ffdec_g726: FFMPEG G.726 ADPCM decoder
ffmpeg:  ffdec_adpcm_ea: FFMPEG Electronic Arts ADPCM decoder
ffmpeg:  ffdec_adpcm_adx: FFMPEG ADX ADPCM decoder
ffmpeg:  ffdec_adpcm_xa: FFMPEG CD-ROM XA ADPCM decoder
ffmpeg:  ffdec_adpcm_4xm: FFMPEG 4-XM ADPCM audio decoder
ffmpeg:  ffdec_adpcm_ms: FFMPEG Microsoft ADPCM audio decoder
ffmpeg:  ffdec_adpcm_ima_smjpeg: FFMPEG IMA/SMJPEG ADPCM audio decoder
ffmpeg:  ffdec_adpcm_ima_ws: FFMPEG IMA/Westwood ADPCM audio decoder
ffmpeg:  ffdec_adpcm_ima_dk4: FFMPEG IMA/DK4 ADPCM decoder
ffmpeg:  ffdec_adpcm_ima_dk3: FFMPEG IMA/DK3 ADPCM audio decoder
ffmpeg:  ffdec_adpcm_ima_wav: FFMPEG IMA/DVI ADPCM audio decoder
ffmpeg:  ffdec_adpcm_ima_qt: FFMPEG IMA/Quicktime ADPCM audio decoder
ffmpeg:  ffdec_mmvideo: FFMPEG American Laser Games MM Video decoder
ffmpeg:  ffdec_bmp: FFMPEG BMP bitmap decoder
ffmpeg:  ffdec_avs: FFMPEG AVS Video decoder
ffmpeg:  ffdec_tta: FFMPEG Lossless True Audio decoder
ffmpeg:  ffdec_truespeech: FFMPEG DSP Group TrueSpeech Audio decoder
ffmpeg:  ffdec_cook: FFMPEG Realaudio G2 (Cook) audio decoder
ffmpeg:  ffdec_qdm2: FFMPEG QDesign Music 2 decoder
ffmpeg:  ffdec_ws_snd1: FFMPEG Westwood Sound-1 decoder
ffmpeg:  ffdec_alac: FFMPEG Apple lossless audio decoder
ffmpeg:  ffdec_shorten: FFMPEG Shorten lossless audio decoder
ffmpeg:  ffdec_flac: FFMPEG FLAC lossless audio decoder
ffmpeg:  ffdec_qtrle: FFMPEG Quicktime RLE animation video decoder
ffmpeg:  ffdec_sol_dpcm: FFMPEG SOL DPCM audio decoder
ffmpeg:  ffdec_xan_dpcm: FFMPEG XAN DPCM audio decoder
ffmpeg:  ffdec_interplay_dpcm: FFMPEG Interplay DPCM audio decoder
ffmpeg:  ffdec_roq_dpcm: FFMPEG RoQ DPCM audio decoder
ffmpeg:  ffdec_real_288: FFMPEG Realaudio 28k8bps decoder
ffmpeg:  ffdec_real_144: FFMPEG Realaudio 14k4bps decoder
ffmpeg:  ffdec_sonic: FFMPEG Sonic audio decoder
ffmpeg:  ffdec_zmbv: FFMPEG Zip Motion Blocks Video decoder
ffmpeg:  ffdec_zlib: FFMPEG Lossless zlib video decoder
ffmpeg:  ffdec_mszh: FFMPEG Lossless MSZH video decoder
ffmpeg:  ffdec_vmdaudio: FFMPEG Sierra VMD audio decoder
ffmpeg:  ffdec_vmdvideo: FFMPEG Sierra VMD video decoder
ffmpeg:  ffdec_truemotion2: FFMPEG Duck Truemotion 2 video decoder
ffmpeg:  ffdec_truemotion1: FFMPEG Duck Truemotion video decoder
ffmpeg:  ffdec_flic: FFMPEG FLIC animation video decoder
ffmpeg:  ffdec_smc: FFMPEG Quicktime SMC graphics video decoder
ffmpeg:  ffdec_8bps: FFMPEG Quicktime planar 8bps video decoder
ffmpeg:  ffdec_idcinvideo: FFMPEG ID Quake II CIN video decoder
ffmpeg:  ffdec_vqavideo: FFMPEG Westwood VQA video decoder
ffmpeg:  ffdec_msvideo1: FFMPEG Microsoft video v1 decoder
ffmpeg:  ffdec_msrle: FFMPEG Microsoft RLE video decoder
ffmpeg:  ffdec_cinepak: FFMPEG Cinepak video decoder
ffmpeg:  ffdec_rpza: FFMPEG Apple RPZA video decoder
ffmpeg:  ffdec_xan_wc3: FFMPEG XAN Wing Commander 3 video decoder
ffmpeg:  ffdec_interplayvideo: FFMPEG Interplay video decoder
ffmpeg:  ffdec_roqvideo: FFMPEG ID/RoQ video decoder
ffmpeg:  ffdec_mdec: FFMPEG Playstation MDEC video decoder
ffmpeg:  ffdec_4xm: FFMPEG 4-XM video decoder
ffmpeg:  ffdec_cljr: FFMPEG Cirrus Logipak AccuPak video decoder
ffmpeg:  ffdec_vcr1: FFMPEG ATI VCR-1 video decoder
ffmpeg:  ffdec_asv2: FFMPEG Asus video v2 decoder
ffmpeg:  ffdec_asv1: FFMPEG Asus video v1 decoder
ffmpeg:  ffdec_theora: FFMPEG Theora video decoder
ffmpeg:  ffdec_vp3: FFMPEG VP3 video decoder
ffmpeg:  ffdec_h264: FFMPEG H.264 video decoder
ffmpeg:  ffdec_cyuv: FFMPEG CYUV lossless video decoder
ffmpeg:  ffdec_snow: FFMPEG Snow wave video decoder
ffmpeg:  ffdec_ffv1: FFMPEG FFMpeg video v1 decoder
ffmpeg:  ffdec_ffvhuff: FFMPEG FFMPEG non-compliant Huffyuv video decoder
ffmpeg:  ffdec_huffyuv: FFMPEG Huffyuv lossless video decoder
ffmpeg:  ffdec_mace6: FFMPEG MACE-6 audio decoder
ffmpeg:  ffdec_mace3: FFMPEG MACE-3 audio decoder
ffmpeg:  ffdec_mp3on4: FFMPEG MP3ON4 decoder
ffmpeg:  ffdec_mp3adu: FFMPEG ADU-formatted MPEG-1 layer 3 audio decoder
ffmpeg:  ffdec_mp3: FFMPEG MPEG-1 layer 3 audio decoder
ffmpeg:  ffdec_png: FFMPEG PNG image decoder
ffmpeg:  ffdec_sp5x: FFMPEG Sp5x-like JPEG decoder
ffmpeg:  ffdec_mjpeg: FFMPEG Motion-JPEG decoder
ffmpeg:  ffdec_dvvideo: FFMPEG Digital video decoder
ffmpeg:  ffdec_mpegvideo: FFMPEG MPEG-2 video decoder
ffmpeg:  ffdec_mpeg2video: FFMPEG MPEG-2 video decoder
ffmpeg:  ffdec_fraps: FFMPEG FRAPS video decoder
ffmpeg:  ffdec_aasc: FFMPEG Autodesk RLE video decoder
ffmpeg:  ffdec_wnv1: FFMPEG Winnov video 1 decoder
ffmpeg:  ffdec_loco: FFMPEG LOCO video decoder
ffmpeg:  ffdec_xl: FFMPEG Miro VideoXL decoder
ffmpeg:  ffdec_qdraw: FFMPEG Applet Quickdraw video decoder
ffmpeg:  ffdec_ultimotion: FFMPEG Ultimotion video decoder
ffmpeg:  ffdec_camstudio: FFMPEG CamStudio video decoder
ffmpeg:  ffdec_camtasia: FFMPEG Techsmith Camtasia video decoder
ffmpeg:  ffdec_indeo3: FFMPEG Indeo-3 video decoder
ffmpeg:  ffdec_indeo2: FFMPEG Indeo=2 video decoder
ffmpeg:  ffdec_wmav2: FFMPEG Windows Media Audio v8/9 decoder
ffmpeg:  ffdec_wmav1: FFMPEG Windows Media Audio v7 decoder
ffmpeg:  ffdec_svq3: FFMPEG Sorensen-3 video decoder
ffmpeg:  ffdec_svq1: FFMPEG Sorensen-1 video decoder
ffmpeg:  ffdec_rv20: FFMPEG Realvideo 2.0 decoder
ffmpeg:  ffdec_rv10: FFMPEG Realvideo 1.0 decoder
ffmpeg:  ffdec_flv: FFMPEG FLV video decoder
ffmpeg:  ffdec_h263i: FFMPEG Intel H.263 video decoder
ffmpeg:  ffdec_vc9: FFMPEG Microsoft Video Codec v1 decoder
ffmpeg:  ffdec_wmv2: FFMPEG Windows Media Video v8 decoder
ffmpeg:  ffdec_wmv1: FFMPEG Windows Media Video v7 decoder
ffmpeg:  ffdec_msmpeg4: FFMPEG Microsoft MPEG-4 v3 decoder
ffmpeg:  ffdec_msmpeg4v2: FFMPEG Microsoft MPEG-4 v2 decoder
ffmpeg:  ffdec_msmpeg4v1: FFMPEG Microsoft MPEG-4 v1 decoder
ffmpeg:  ffdec_mpeg4: FFMPEG MPEG-4 compatible video decoder
ffmpeg:  ffdec_h261: FFMPEG H.261 video decoder
ffmpeg:  ffdec_h263: FFMPEG H.263 video decoder
ffmpeg:  ffdec_pam: FFMPEG PAM image decoder
ffmpeg:  ffdec_pbm: FFMPEG PBM image decoder
ffmpeg:  ffdec_pgmyuv: FFMPEG PGM-YUV image decoder
ffmpeg:  ffdec_pgm: FFMPEG PGM image decoder
ffmpeg:  ffdec_ppm: FFMPEG PPM image decoder
ffmpeg:  ffenc_adpcm_sbpro_2: FFMPEG SB-Pro ADPCM 2 encoder
ffmpeg:  ffenc_adpcm_sbpro_3: FFMPEG SB-Pro ADPCM 3 encoder
ffmpeg:  ffenc_adpcm_sbpro_4: FFMPEG SB-Pro ADPCM 4 encoder
ffmpeg:  ffenc_adpcm_yamaha: FFMPEG Yamaha ADPCM encoder
ffmpeg:  ffenc_adpcm_swf: FFMPEG Shockwave ADPCM encoder
ffmpeg:  ffenc_adpcm_ct: FFMPEG CT ADPCM encoder
ffmpeg:  ffenc_g726: FFMPEG G.726 ADPCM encoder
ffmpeg:  ffenc_adpcm_ea: FFMPEG Electronic Arts ADPCM encoder
ffmpeg:  ffenc_adpcm_adx: FFMPEG ADX ADPCM encoder
ffmpeg:  ffenc_adpcm_xa: FFMPEG CD-ROM XA ADPCM encoder
ffmpeg:  ffenc_adpcm_4xm: FFMPEG 4-XM ADPCM audio encoder
ffmpeg:  ffenc_adpcm_ms: FFMPEG Microsoft ADPCM audio encoder
ffmpeg:  ffenc_adpcm_ima_smjpeg: FFMPEG IMA/SMJPEG ADPCM audio encoder
ffmpeg:  ffenc_adpcm_ima_ws: FFMPEG IMA/Westwood ADPCM audio encoder
ffmpeg:  ffenc_adpcm_ima_dk4: FFMPEG IMA/DK4 ADPCM encoder
ffmpeg:  ffenc_adpcm_ima_dk3: FFMPEG IMA/DK3 ADPCM audio encoder
ffmpeg:  ffenc_adpcm_ima_wav: FFMPEG IMA/DVI ADPCM audio encoder
ffmpeg:  ffenc_adpcm_ima_qt: FFMPEG IMA/Quicktime ADPCM audio encoder
ffmpeg:  ffenc_sonicls: FFMPEG Sonic lossless audio encoder
ffmpeg:  ffenc_sonic: FFMPEG Sonic audio encoder
ffmpeg:  ffenc_dvvideo: FFMPEG Digital video encoder
ffmpeg:  ffenc_snow: FFMPEG Snow wave video encoder
ffmpeg:  ffenc_ffv1: FFMPEG FFMpeg video v1 encoder
ffmpeg:  ffenc_asv2: FFMPEG Asus video v2 encoder
ffmpeg:  ffenc_asv1: FFMPEG Asus video v1 encoder
ffmpeg:  ffenc_ffvhuff: FFMPEG FFMPEG non-compliant Huffyuv video encoder
ffmpeg:  ffenc_huffyuv: FFMPEG Huffyuv lossless video encoder
ffmpeg:  ffenc_pam: FFMPEG PAM image encoder
ffmpeg:  ffenc_pbm: FFMPEG PBM image encoder
ffmpeg:  ffenc_pgmyuv: FFMPEG PGM-YUV image encoder
ffmpeg:  ffenc_pgm: FFMPEG PGM image encoder
ffmpeg:  ffenc_ppm: FFMPEG PPM image encoder
ffmpeg:  ffenc_png: FFMPEG PNG image encoder
ffmpeg:  ffenc_ljpeg: FFMPEG Lossless JPEG encoder
ffmpeg:  ffenc_mjpeg: FFMPEG Motion-JPEG encoder
ffmpeg:  ffenc_svq1: FFMPEG Sorensen-1 video encoder
ffmpeg:  ffenc_wmv2: FFMPEG Windows Media Video v8 encoder
ffmpeg:  ffenc_wmv1: FFMPEG Windows Media Video v7 encoder
ffmpeg:  ffenc_msmpeg4: FFMPEG Microsoft MPEG-4 v3 encoder
ffmpeg:  ffenc_msmpeg4v2: FFMPEG Microsoft MPEG-4 v2 encoder
ffmpeg:  ffenc_msmpeg4v1: FFMPEG Microsoft MPEG-4 v1 encoder
ffmpeg:  ffenc_mpeg4: FFMPEG MPEG-4 compatible video encoder
ffmpeg:  ffenc_rv20: FFMPEG Realvideo 2.0 encoder
ffmpeg:  ffenc_rv10: FFMPEG Realvideo 1.0 encoder
ffmpeg:  ffenc_flv: FFMPEG FLV video encoder
ffmpeg:  ffenc_h263p: FFMPEG H.263 (P) video encoder
ffmpeg:  ffenc_h263: FFMPEG H.263 video encoder
ffmpeg:  ffenc_h261: FFMPEG H.261 video encoder
ffmpeg:  ffenc_mpeg2video: FFMPEG MPEG-2 video encoder
ffmpeg:  ffenc_mpeg1video: FFMPEG MPEG-1 video encoder
ffmpeg:  ffenc_mp2: FFMPEG MPEG-1 layer 2 audio encoder
ffmpeg:  ffenc_ac3: FFMPEG AC-3 audio encoder
ffmpegcolorspace:  ffmpegcolorspace: FFMPEG Colorspace converter
filter:  bpwsinc: Band-pass Windowed sinc filter
filter:  lpwsinc: Low-pass Windowed sinc filter
filter:  iir: Infinite Impulse Response (IIR) filter
flac:  flacdec: FLAC audio decoder
flac:  flacenc: FLAC audio encoder
flxdec:  flxdec: FLX audio decoder
freeze:  freeze: Stream freezer
gconfelements:  gconfaudiosrc: GConf audio source
gconfelements:  gconfaudiosink: GConf audio sink
gconfelements:  gconfvideosrc: GConf video source
gconfelements:  gconfvideosink: GConf video sink
gdkpixbuf:  gdkpixbufscale: GdkPixbuf image scaler
gdkpixbuf:  gdkpixbufdec: GdkPixbuf image decoder
gdp:  gdppay: GDP Payloader
gdp:  gdpdepay: GDP Depayloader
gnomevfs:  gnomevfssink: GnomeVFS Sink
gnomevfs:  gnomevfssrc: GnomeVFS Source
goom:  goom: GOOM: what a GOOM!
gsm:  gsmdec: GSM audio decoder
gsm:  gsmenc: GSM audio encoder
h264parse:  h264parse: H264Parse
halelements:  halaudiosrc: HAL audio source
halelements:  halaudiosink: HAL audio sink
icydemux:  icydemux: ICY tag demuxer
id3demux:  id3demux: ID3 tag demuxer
iec958:  ac3iec958: AC3 to IEC958 filter
jpeg:  smokedec: Smoke video decoder
jpeg:  smokeenc: Smoke video encoder
jpeg:  jpegdec: JPEG image decoder
jpeg:  jpegenc: JPEG image encoder
lame:  lame: L.A.M.E. mp3 encoder
level:  level: Level
libvisual:  libvisual_oinksie: libvisual oinksie plugin plugin v.0.1
libvisual:  libvisual_lv_scope: libvisual libvisual scope plugin v.0.1
libvisual:  libvisual_jess: libvisual jess plugin plugin v.0.1
libvisual:  libvisual_jakdaw: libvisual Jakdaw plugin plugin v.0.0.1
libvisual:  libvisual_infinite: libvisual infinite plugin plugin v.0.1
libvisual:  libvisual_corona: libvisual libvisual corona plugin plugin v.0.1
libvisual:  libvisual_bumpscope: libvisual Bumpscope plugin plugin v.0.0.1
mad:  id3mux: id3 tag muxer
mad:  mad: mad mp3 decoder
matroska:  matroskamux: Matroska muxer
matroska:  matroskademux: Matroska demuxer
mms:  mmssrc: MMS streaming source
modplug:  modplug: ModPlug
mpeg2dec:  mpeg2dec: mpeg1 and mpeg2 video decoder
mpegaudioparse:  mp3parse: MPEG1 Audio Parser
mpegstream:  dvddemux: DVD Demuxer
mpegstream:  mpegdemux: MPEG Demuxer
mpegstream:  mpegparse: MPEG System Parser
mulaw:  mulawdec: Mu Law audio decoder
mulaw:  mulawenc: Mu Law audio encoder
multipart:  multipartmux: Multipart muxer
multipart:  multipartdemux: Multipart demuxer
musepack:  musepackdec: Musepack decoder
navigationtest:  navigationtest: Video navigation test
neon:  neonhttpsrc: HTTP client source
ogg:  oggaviparse: Ogg AVI parser
ogg:  oggparse: Ogg parser
ogg:  ogmtextparse: OGM text stream parser
ogg:  ogmvideoparse: OGM video stream parser
ogg:  ogmaudioparse: OGM audio stream parser
ogg:  oggmux: Ogg muxer
ogg:  oggdemux: Ogg demuxer
ossaudio:  osssink: Audio Sink (OSS)
ossaudio:  osssrc: Audio Source (OSS)
ossaudio:  ossmixer: OSS Mixer
pango:  textrender: Text renderer
pango:  clockoverlay: Clock overlay
pango:  timeoverlay: Time overlay
pango:  textoverlay: Text overlay
playbin:  playbin: Player Bin
png:  pngenc: PNG image encoder
png:  pngdec: PNG image decoder
qtdemux:  qtdemux: QuickTime demuxer
rmdemux:  rmdemux: RealMedia Demuxer
rtp:  rtpspeexdepay: RTP packet parser
rtp:  rtpspeexpay: RTP packet parser
rtp:  rtpmp4gpay: RTP packet parser
rtp:  rtpmp4gdepay: RTP packet parser
rtp:  rtpmp4vdepay: RTP packet parser
rtp:  rtpmp4vpay: RTP packet parser
rtp:  rtpmp2tdepay: RTP packet parser
rtp:  asteriskh263: RTP packet parser
rtp:  rtph263pay: RTP packet parser
rtp:  rtph263pdepay: RTP packet parser
rtp:  rtph263ppay: RTP packet parser
rtp:  rtpmpapay: RTP packet parser
rtp:  rtpmpadepay: RTP packet parser
rtp:  rtppcmapay: RTP packet parser
rtp:  rtppcmupay: RTP packet parser
rtp:  rtppcmudepay: RTP packet parser
rtp:  rtppcmadepay: RTP packet parser
rtp:  rtpamrpay: RTP packet parser
rtp:  rtpamrdepay: RTP packet parser
rtp:  rtpgsmpay: RTP GSM audio payloader
rtp:  rtpgsmdepay: RTP packet parser
rtp:  rtpdepay: RTP payloader
rtsp:  rtpdec: RTP Decoder
rtsp:  rtspsrc: RTSP packet receiver
shout2send:  shout2send: Icecast network sink
siddec:  siddec: Sid decoder
smpte:  smpte: SMPTE transitions
spectrum:  spectrum: Spectrum analyzer
speed:  speed: Speed
speex:  speexdec: Speex audio decoder
speex:  speexenc: Speex audio encoder
subparse:  ssaparse: SSA Subtitle Parser
subparse:  subparse: Subtitle parser
subparse: subparse_typefind: srt, sub, mpsub, mdvd, smi
swfdec:  swfdec: SWF video decoder
taglib:  apev2mux: TagLib-based APEv2 Muxer
taglib:  id3v2mux: TagLib-based ID3v2 Muxer
tcp:  multifdsink: Multi filedescriptor sink
tcp:  tcpserversrc: TCP server source
tcp:  tcpserversink: TCP server sink
tcp:  tcpclientsrc: TCP client source
tcp:  tcpclientsink: TCP client sink
theora:  theoraparse: TheoraParse
theora:  theoraenc: Theora video encoder
theora:  theoradec: Theora video decoder
musicbrainz:  trm: MusicBrainz TRM generator
tta:  ttadec: TTA audio decoder
tta:  ttaparse: TTA file parser
typefindfunctions: multipart/x-mixed-replace: no extensions
typefindfunctions: video/x-dirac: no extensions
typefindfunctions: application/x-ms-dos-executable: dll, exe, ocx, sys, scr, msstyles, cpl
typefindfunctions: application/x-ar: a
typefindfunctions: application/x-tar: tar
typefindfunctions: application/x-rar: rar
typefindfunctions: audio/x-wavpack-correction: wvc
typefindfunctions: audio/x-wavpack: wv, wvp
typefindfunctions: audio/x-spc: spc
typefindfunctions: adts_mpeg_stream: aac
typefindfunctions: application/x-executable: no extensions
typefindfunctions: text/x-cmml: no extensions
typefindfunctions: application/x-ogg-skeleton: no extensions
typefindfunctions: audio/x-speex: no extensions
typefindfunctions: application/x-ogm-text: no extensions
typefindfunctions: application/x-ogm-audio: no extensions
typefindfunctions: application/x-ogm-video: no extensions
typefindfunctions: video/x-theora: no extensions
typefindfunctions: audio/x-vorbis: no extensions
typefindfunctions: application/x-compress: Z
typefindfunctions: application/zip: zip
typefindfunctions: application/x-gzip: gz
typefindfunctions: application/x-bzip: bz2
typefindfunctions: image/x-sun-raster: ras
typefindfunctions: image/x-xpixmap: xpm
typefindfunctions: image/x-jng: jng
typefindfunctions: video/x-mng: mng
typefindfunctions: image/x-xcf: xcf
typefindfunctions: audio/x-sid: sid
typefindfunctions: audio/iLBC-sh: ilbc
typefindfunctions: audio/x-amr-wb-sh: amr
typefindfunctions: audio/x-amr-nb-sh: amr
typefindfunctions: video/x-dv: dv, dif
typefindfunctions: video/x-mve: mve
typefindfunctions: video/x-matroska: mkv, mka
typefindfunctions: image/tiff: tif, tiff
typefindfunctions: image/bmp: bmp
typefindfunctions: image/png: png
typefindfunctions: image/gif: gif
typefindfunctions: image/jpeg: jpg, jpe, jpeg
typefindfunctions: application/x-ape: ape
typefindfunctions: audio/x-shorten: shn
typefindfunctions: audio/x-w64: w64
typefindfunctions: audio/x-ircam: sf
typefindfunctions: audio/x-sds: sds
typefindfunctions: audio/x-voc: voc
typefindfunctions: audio/x-nist: nist
typefindfunctions: audio/x-paris: paf
typefindfunctions: audio/x-svx: iff, svx
typefindfunctions: audio/x-aiff: aiff, aif, aifc
typefindfunctions: audio/x-wav: wav
typefindfunctions: application/xml: xml
typefindfunctions: application/smil: smil
typefindfunctions: text/uri-list: ram
typefindfunctions: text/plain: txt
typefindfunctions: video/x-flv: flv
typefindfunctions: application/x-shockwave-flash: swf, swfl
typefindfunctions: application/x-pn-realaudio: ra, ram, rm, rmvb
typefindfunctions: application/vnd.rn-realmedia: ra, ram, rm, rmvb
typefindfunctions: text/html: htm, html
typefindfunctions: video/quicktime: mov
typefindfunctions: application/x-3gp: 3gp
typefindfunctions: audio/x-m4a: m4a
typefindfunctions: video/mpeg4: m4v
typefindfunctions: video/mpeg-stream: mpv, mpeg, mpg
typefindfunctions: video/mpeg: mpv, mpeg, mpg
typefindfunctions: application/ogg: anx, ogg, ogm
typefindfunctions: video/mpegts: ts
typefindfunctions: video/mpeg2: mpe, mpeg, mpg
typefindfunctions: video/mpeg1: mpe, mpeg, mpg
typefindfunctions: audio/x-ac3: ac3
typefindfunctions: audio/mpeg: mp3, mp2, mp1, mpga
typefindfunctions: audio/x-mod: 669, amf, dsm, gdm, far, imf, it, med, mod, mtm, okt, sam, s3m, stm, stx, ult, xm
typefindfunctions: audio/x-ttafile: tta
typefindfunctions: application/x-apetag: ape, mpc, wv
typefindfunctions: application/x-id3v1: mp3, mp2, mp1, mpga, ogg, flac, tta
typefindfunctions: application/x-id3v2: mp3, mp2, mp1, mpga, ogg, flac, tta
typefindfunctions: video/x-fli: flc, fli
typefindfunctions: audio/x-flac: flac
typefindfunctions: video/x-vcd: dat
typefindfunctions: video/x-cdxa: dat
typefindfunctions: video/x-msvideo: avi
typefindfunctions: audio/x-au: au, snd
typefindfunctions: audio/x-musepack: mpc
typefindfunctions: video/x-ms-asf: asf, wm, wma, wmv
udp:  udpsrc: UDP packet receiver
udp:  dynudpsink: UDP packet sender
udp:  multiudpsink: UDP packet sender
udp:  udpsink: UDP packet sender
video4linux:  v4lsrc: Video (video4linux/raw) Source
video4linux2:  v4l2src: Video (video4linux2/raw) Source
videobalance:  videobalance: Video balance
videobox:  videobox: Video box filter
videocrop:  videocrop: Crop
videoflip:  videoflip: Video flipper
videomixer:  videomixer: Video mixer
videorate:  videorate: Video rate adjuster
videoscale:  videoscale: Video scaler
videotestsrc:  videotestsrc: Video test source
volume:  volume: Volume
vorbis:  vorbisparse: VorbisParse
vorbis:  vorbisdec: Vorbis audio decoder
vorbis:  vorbisenc: Vorbis audio encoder
wavenc:  wavenc: WAV audio muxer
wavpack:  wavpackenc: Wavpack audio encoder
wavpack:  wavpackdec: WavePack audio decoder
wavpack:  wavpackparse: WavePack parser
wavparse:  wavparse: WAV audio demuxer
ximagesink:  ximagesink: Video sink
ximagesrc:  ximagesrc: Ximage video source
xingheader:  xingmux: MP3 Xing muxer
xvid:  xviddec: XviD video decoder
xvid:  xvidenc: XviD video encoder
xvimagesink:  xvimagesink: Video sink
pitfdll:  qtadec_bin: quicktime binary audio decoder
pitfdll:  dmodec_wmspdmodv1: DMO wmspdmod decoder version 1
pitfdll:  dmodec_wmadmodv3: DMO wmadmod decoder version 3
pitfdll:  dmodec_wmadmodv2: DMO wmadmod decoder version 2
pitfdll:  dmodec_wmadmodv1: DMO wmadmod decoder version 1
pitfdll:  dmodec_wmvdmodv3: DMO wmvdmod decoder version 3
pitfdll:  dmodec_wmvdmodv2: DMO wmvdmod decoder version 2
pitfdll:  dmodec_wmvdmodv1: DMO wmvdmod decoder version 1
pitfdll:  dmodec_wmv9dmodv3: DMO wmv9dmod decoder version 3
pitfdll:  dshowdec_ir41_32v4: DS ir41_32 decoder version 4
pitfdll:  dshowdec_ir50_32v5: DS ir50_32 decoder version 5
staticelements:  bin: Generic bin
staticelements:  pipeline: Pipeline object

Total count: 118 plugins, 560 features

```
I don't see anything wrong in there, but it is pretty large and I don't know what a problem really looks like.  The Xubuntu box is still not recognizing or playing AAC files.  Even the properties dialog for an AAC audio file does not show the "Audio" tab like it does for an mp3.

---

### Post by killernurd on 2007-01-21
Huh.

/me shrugs

I... don't know, then. I haven't used Rhythmbox in a while 'cause frankly... it sucks for what I want in a media player. Also, no matter *what* you do with it, it won't play MP3s, period. It could be that Rhythmbox isn't playing the AACs because it's refusing to play anything bug Ogg Vorbis.

---

### Post by Cable on 2007-01-21
> **killernurd said:**
> Huh.

/me shrugs

I... don't know, then. I haven't used Rhythmbox in a while 'cause frankly... it sucks for what I want in a media player. Also, no matter *what* you do with it, it won't play MP3s, period. It could be that Rhythmbox isn't playing the AACs because it's refusing to play anything bug Ogg Vorbis.
That's odd, because it plays mp3's perfectly fine on both my Ubuntu and Xubuntu boxes.  I just cannot get the Xubuntu box to play AAC.  Strange...](*,)

---

### Post by hotani on 2007-02-07
same here. the mp3 plugins were installed with ease via add/remove, and I had high hopes for aac playback since it appeared in there as well. mp3 files showed up in rhythmbox, but no aac. after digging through synaptic, still no go.

---

### Post by djlyx on 2007-03-10
I had the same problem.  I went into synaptic and checked off almost everything that had to do with gstreamer (Good, Bad, ugly Ver 8 and Ver 10)

It worked! Now AAC plays in totem and rhythmbox.

Hopes this helps.

---

### Post by shiwei on 2007-03-15
well, i just recently reinstalled rhythmbox, and everything works, don't know why, but i installed along with rhythmbox, gstreamer-faac, faad, etc.. maybe that's why..

---

### Post by schteeve on 2007-04-04
Could someone whose got aac/m4a files working post the output of their gst-inspect please?  Im trying to them working on my feisty install.

thanks

---

### Post by hotani on 2007-04-04
i got them working via add/remove. If you search for 'aac' it will return the bad/ugly codec sets. After installing those it was fine.

---

### Post by orphzirra on 2007-04-22
I had the same success following the advice of the above post.

---

### Post by bestiarosa on 2007-07-29
I've installed these packages and now it works:

gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.8-faad

I guess if you want encoding you have to install gstreamer0.8-faac as well, but I haven't checked.

:guitar:

---

