---
title: "Mapping Network Stream to a video adaptor"
date: 2013-09-02
forum: General Help
---

### Post by mrahsanahmad on 2013-09-02
Hi

I have a video stream that I get at the address [http://localhost:8080/stream?topic=/uvc/camera/image_color](http://localhost:8080/stream?topic=/uvc/camera/image_color). I want to import this video stream in matlab. Unfortunately, matlab captures video stream only from video devices installed on the machine it is running. 
I am looking for a way to map this video stream to a virtual video device and import it in matlab. In easy words, I want to create a virtual video device (webcam) which outputs whatever is being streamed on the address [http://localhost:8080/stream?topic=/uvc/camera/image_color](http://localhost:8080/stream?topic=/uvc/camera/image_color). And this video device should behave just like any other ordinary installed webcam.

I tried to test v4l2vd software however i cannot build it because it requires linux/videodev.h which is not included in the linux headers which I am using. I would appreciate if I could be helped on this issue too. Still, v4l2vd will just allow me to create a virtual video device. I still dont know how can I map the video stream to this virtual video device.

My version of linux is :
Linux ahsanahmad-P6816 3.5.0-39-generic #60~precise1-Ubuntu SMP Wed Aug 14 15:38:41 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux.

My version of matlab is :
R2012b

Thankyou and regards
Ahsan Ahmad

---

