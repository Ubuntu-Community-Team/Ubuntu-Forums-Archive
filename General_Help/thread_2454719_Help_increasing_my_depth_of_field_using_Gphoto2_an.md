---
title: "Help increasing my depth of field using Gphoto2 and a Canon DSLR"
date: 2020-12-04
forum: General Help
---

### Post by goemonburo on 2020-12-04
Hi, at long last I've successfully gotten my Canon 7D dslr working with my Lubuntu 20.04LTS system using Gphoto2 (v 2.5.23) from the command line.  I plug in the camera, "eject" it from the file manager, make sure the proper module is loaded, and then type the following:

    gphoto2 --stdout --capture-movie | ffmpeg -i - -vcodec rawvideo -pix_fmt yuv420p -threads 0 -f v4l2 /dev/video0

It works just fine overall; however, I'm noticing that it has an extremely shallow depth of field and thus I have to be very careful to stay fixed in the same spot during my web conference.  If I lean too far forward or too far back, I'm blurry.  I know this is a DSLR, so obviously not the same as a webcam, but does anyone know if there's a setting, either using the camera itself or Gphoto2 cli, that will run the camera yet allow for a wider depth of field?  It seems that even if I set the camera manually for a certain aperture and f-stop, as soon as I start up Gphoto2 it is totally lost.  

I have an important conference later today and would love to fix this beforehand.  Thank you if you know what I can do!  :-)

---

