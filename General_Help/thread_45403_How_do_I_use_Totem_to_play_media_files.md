---
title: "How do I use Totem to play media files?"
date: 2005-06-30
forum: General Help
---

### Post by tzutolin on 2005-06-30
Hello everyone,


I'm a totally newbie in multimedia area and I would like to enable Totem playing .avi .wma .ra .mpeg files.

Could anyone please tell me which packages will I need? Are totem-xine, w32codec enough?

Thank you very much!

Best Regards,
tzutolin

---

### Post by tristan on 2005-06-30
Hi tzutolin

Totem-gstreamer is unfortunately not particulalry capable at this point in time.

Have a look at the ubuntuguide [http://www.ubuntuguide.org](http://www.ubuntuguide.org), which has detailed instructions on how to get totem-xine (and various codecs to make it useful) up and running, and a lot more useful info as well..

sudo apt-get install gstreamer0.8-plugins
sudo apt-get install gstreamer0.8-lame
sudo apt-get install gstreamer0.8-ffmpeg
sudo apt-get install w32codecs
sudo apt-get install libdivx4linux
sudo apt-get install lame
sudo apt-get install sox
sudo apt-get install ffmpeg
sudo apt-get install mjpegtools
sudo apt-get install vorbis-tools

---

### Post by tzutolin on 2005-06-30
Thanks for your quick reply, tristan! I am going to try this out :-)

---

