---
title: "totem wont play divx/xvid anymore"
date: 2005-08-26
forum: General Help
---

### Post by glandula on 2005-08-26
my totem worked just fine until last night. this morning it wont play xvid or divx anymore. the error message is " totem could not play file whatever.avi - video codec 'XviD format' is not handled. you might need additional plugins etc" - i got this message playing the exact same avi i sucessfully played last night.

firstly this was working until last night, it must have become broken overnight somehow. i have all the codecs and win32 codecs listed over at ubuntuguide, and also totem-xine. i have now uninstalled all these codecs and reinstalled them but its still broken. have also rebooted and tried other avis, makes no difference.

everything works in vlc but i prefer totem. any idea what might be wrong?

---

### Post by lorenzo on 2005-08-26
Actually you can now use totem-gstreamer. If you follow the guidelines in the ubuntu guide:

sudo apt-get install gstreamer0.8-plugins
sudo apt-get install gstreamer0.8-lame
sudo apt-get install gstreamer0.8-ffmpeg <<
sudo apt-get install w32codecs
sudo apt-get install libdivx4linux
sudo apt-get install lame
sudo apt-get install sox
sudo apt-get install ffmpeg
sudo apt-get install mjpegtools
sudo apt-get install vorbis-tools
gst-register-0.8

is should work correctly. Does it? I have switched yesterday from totem-xine to totem-gstreamer and had no problems...

---

### Post by glandula on 2005-08-26
yeah it works with gstreamer isntead of totem-xine, so i guess its totem-xine that wasnt working properly. but the problem with gstreamer is that the quality of the video is really poor, looks like its skipping frames and its all rather jumpy :( with totem-xine (while it was working) it was way better

---

### Post by ankush_jhalani on 2005-11-17
I agree with glandula, even after applying all the codec updates, i find mplayer cant play many  files, and although totem plays all the files, it seems like dropping a lot of frames, and the sound and video go out of sync..
  Someone help..

---

