---
title: "File explorer apps not using embedded/tagged/custom thumbnail for MP4 files"
date: 2024-05-06
forum: General Help
---

### Post by xanizen on 2024-05-06
I've used various apps, such as:
[TagEditor]("https://github.com/Martchus/tageditor")
MusicBrainzPicard

To confirm the MP4 file is embedded with the desired thumbnail file.
I also emptied the contents in the directory: 
```
~/.cache/thumbnails/
```

The file explorers, default Nautilus, and Dolphin, are using randomly generated thumbnails.
How may I overcome this?

Edit: I followed the suggestion [here]("https://forum.manjaro.org/t/show-embedded-cover-as-a-thumbnail-for-videos/98907"),

I opened the following file with gedit text editor:
```
sudo gedit /usr/share/thumbnailers/ffmpegthumbnailer.thumbnailer
```

I placed '-m' in the front of directive Exec=ffmpegthumbnailer :

```
[Thumbnailer Entry]TryExec=ffmpegthumbnailer
Exec=ffmpegthumbnailer -m -i %i -o %o -s %s -f
MimeType=video/jpeg;video/mp4;video/mpeg;video/quicktime;video/x-ms-asf;video/x-ms-wm;video/x-ms-wmv;video/x-ms-asx;video/x-ms-wmx;video/x-ms-wvx;video/x-msvideo;video/x-flv;video/x-matroska;application/mxf;video/3gp;video/3gpp;video/dv;video/divx;video/fli;video/flv;video/mp2t;video/mp4v-es;video/msvideo;video/ogg;video/vivo;video/vnd.divx;video/vnd.mpegurl;video/vnd.rn-realvideo;application/vnd.rn-realmedia;video/vnd.vivo;video/webm;video/x-anim;video/x-avi;video/x-flc;video/x-fli;video/x-flic;video/x-m4v;video/x-mpeg;video/x-mpeg2;video/x-nsv;video/x-ogm+ogg;video/x-theora+ogg
```

It seems to work for now, but only in Nautilus, nothing shows up in Dolphin.

---

