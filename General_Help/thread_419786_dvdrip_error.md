---
title: "dvd::rip error?"
date: 2007-04-23
forum: General Help
---

### Post by Foxman2k on 2007-04-23
When I try to start the transcoding process,  I get this error?

```

Mon Apr 23 09:17:31 2007	Job 'Transcode multipass - title #1' exited with error: Job 'Transcode video - title #1, pass 1' failed with error message:
Command exits with failure code:
Command: mkdir -m 0775 -p '/home/slincoln/dvdrip-data/eternal/tmp' && cd /home/slincoln/dvdrip-data/eternal/tmp && mkdir -p /home/slincoln/dvdrip-data/eternal/avi/001 && execflow -n 19 transcode -H 10 -a 1 -x vob -i \/home\/slincoln\/dvdrip\-data\/eternal\/vob\/001\/ -w 1804,50 -A -N  -f 24,1 -M 2 -Y 10,0,14,0 -B 15,10,8 -R 1 -y xvid,null --psu_mode --nav_seek /home/slincoln/dvdrip-data/eternal/tmp/eternal-001-nav.log --no_split  -o /dev/null --print_status 25 && echo EXECFLOW_OK

Output: transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg

Usage: transcode [options]

options:
 -i name             input file/directory/device/mountpoint/host name
 -H n                auto-probe n MB of source (0=off) [1]
 -p file             read audio stream from separate file [off]
 -x vmod[,amod]      video[,audio] import modules [null]
 -a a[,v]            extract audio[,video] track [0,0]
--dvd_access_delay N delay DVD access by N seconds [3]

 -e r[,b[,c]]        PCM audio stream parameter [48000,16,2]
 -E r[,b[,c]]        audio output samplerate, bits, channels [as input]
 -n 0xnn             import audio format id [0x2000]
 -N 0xnn             export audio format id [0x55]
 -b b[,v[,q[,m]]]    audio encoder bitrate kBits/s[,vbr[,quality[,mode]]] [128,0,5,0]
--no_audio_adjust    disable audio frame sample adjustment [off]
--no_bitreservoir    disable lame bitreservoir [off]
--lame_preset name[,fast]  use lame preset with name. [off]

 -g wxh              RGB video stream frame size [720x576]
--import_asr C       set import display aspect ratio code C [auto]
--export_asr C       set export display aspect ratio code C [as input]
--export_par N,D     set export pixel aspect ratio [auto]
--keep_asr           try to keep aspect ratio (only with -Z) [off]
 -f rate[,frc]       input video frame rate[,frc] [25.000,0] fps
--export_fps f[,c]   output video frame rate[,code] [as input] [25.000,3]
--export_frc F       set export frame rate code F [as input]
--hard_fps           disable smooth dropping (for variable fps clips) [off]

 -o file             output file name
 -m file             write audio stream to separate file [off]
 -y vmod[,amod]      video[,audio] export modules [null]
 -F codec            encoder parameter strings [module dependent]
 --avi_limit N       split output AVI file after N MB [2048]
 --avi_comments F    Read AVI header comments from file F (see transcode(1)) [off]

 -d                  swap bytes in audio stream [off]
 -s g[,c[,f[,r]]]    increase volume by gain,[center,front,rear] [off,1,1,1]

 -u m[,n]            use m framebuffer[,n threads] for AV processing [10,1]
 -A                  use AC3 as internal audio codec [off]
 -V                  use YV12/I420/YUV420 as internal video format [deprecated, default]
 --use_rgb           use RGB as internal video format [off]
--uyvy               use UYVY/YUV422 as internal video format [off]
 -J f1[,f2[,...]]    apply external filter plugins [off]
 -P flag             pass-through flag (0=off|1=V|2=A|3=A+V) [0]

 -D num              sync video start with audio frame num [0]
--av_fine_ms t       AV fine-tuning shift t in millisecs [autodetect]

 -M mode             demuxer PES AV sync mode (0=off|1=PTS only|2=full) [1]
 -O                  flush lame mp3 buffer on encoder stop [off]

 -r n[,m]            reduce video height/width by n[,m] [off]
 -B n[,m[,M]]        resize to height-n*M rows [,width-m*M] columns [off,32]
 -X n[,m[,M]]        resize to height+n*M rows [,width+m*M] columns [off,32]
 -Z wxh[,fast]       resize to w columns, h rows with filtering [off,notfast]
--zoom_filter str    use filter string for video resampling -Z [Lanczos3]

 -C mode             enable anti-aliasing mode (1-3) [off]
--antialias_para w,b center pixel weight, xy-bias [0.333,0.500]

 -I mode             enable de-interlacing mode (1-5) [off]

 -K                  enable b/w mode [off]
 -G val              gamma correction (0.0-10.0) [off]
 -z                  flip video frame upside down [off]
 -l                  mirror video frame [off]
 -k                  swap red/blue (Cb/Cr) in video frame [off]

 -j t[,l[,b[,r]]]    select frame region by clipping border [off]
 -Y t[,l[,b[,r]]]    select (encoder) frame region by clipping border [off]
--pre_clip t[,l[,b[,r]]]  select initial frame region by clipping border [off]
--post_clip t[,l[,b[,r]]] select final frame region by clipping border [off]

 -w b[,k[,c]]        encoder bitrate[,keyframes[,crispness]] [1800,250,100]
--video_max_bitrate  maximum bitrate when encoding variable bitrate MPEG-2 streams [same as -w]
 -R n[,f1[,f2]]      enable multi-pass encoding (0-3) [0,divx4.log,pcm.log]
 -Q n[,m]            encoding[,decoding] quality (0=fastest-5=best) [5,5]
--divx_quant min,max divx encoder min/max quantizer [2,31]
--divx_rc p,rp,rr    divx encoder rate control parameter [2000,10,20]
--divx_vbv_prof N    divx5 encoder VBV profile (0=free-5=hiqhq) [3]
--divx_vbv br,sz,oc  divx5 encoder VBV params (bitrate,size,occup.) [10000,192,36864]

 -c f1-f2[,f3-f4]    encode only f1-f2[,f3-f4] (frames or HH:MM:SS) [all]
 -t n,base           split output to base%03d.avi with n frames [off]
--dir_mode base      process directory contents to base-%03d.avi [off]
--frame_interval N   select only every Nth frame to be exported [1]

 -U base             process DVD in chapter mode to base-ch%02d.avi [off]
 -T t[,c[-d][,a]]    select DVD title[,chapter(s)[,angle]] [1,1,1]

 -W n,m[,file]       autosplit and process part n of m (VOB only) [off]
--cluster_percentage use percentage mode for cluster encoding -W [off]
--cluster_chunks a-b process chunk range instead of selected chunk [off]
 -S unit[,s1-s2]     process program stream unit[,s1-s2] sequences [0,all]
 -L n                seek to VOB stream offset nx2kB [0]

--import_v4l n[,id]  channel number and station number or name [0]

--pulldown           set MPEG 3:2 pulldown flags on export [off]
--encode_fields      enable field based encoding (if supported) [off]

--nav_seek file      use VOB navigation file [off]
--psu_mode           process VOB in PSU, -o is a filemask incl. %d [off]
--psu_chunks a-b     process only selected units a-b for PSU mode [all]
--no_split           encode to single file in chapter/psu mode [off]
--ts_pid 0xnn        transport video stream pid [0]

--a52_drc_off        disable liba52 dynamic range compression [enabled]
--a52_demux          demux AC3/A52 to separate channels [off]
--a52_dolby_off      disable liba52 dolby surround [enabled]

--print_status N[,r] print status every N frames / use CR or NL [1,1]
--progress_off       disable progress meter status line [off]
--color N            level of color in transcodes output [1]
--write_pid file     write pid of signal thread to "file" [off]
--nice N             set niceness to N [off]
--accel type         enforce IA32/AMD64 acceleration for type [autodetect]
--socket file        socket file for run-time control [no file]
--dv_yuy2_mode       libdv YUY2 mode (default is YV12) [off]
--config_dir dir     Assume config files are in this dir [off]
--ext vid,aud        Use these file extensions [.avi,.mp3]
--export_prof S      Export profile {vcd, svcd, xvcd,  dvd}[-pal|-ntsc|-secam]

 -q level            verbosity (0=quiet,1=info,2=debug) [1]
 -h                  this usage message
 -v                  print version


--------------------------------------------------------------------------------
Mon Apr 23 09:17:31 2007	Job 'Transcode video - title #1, pass 1' finished

```

---

