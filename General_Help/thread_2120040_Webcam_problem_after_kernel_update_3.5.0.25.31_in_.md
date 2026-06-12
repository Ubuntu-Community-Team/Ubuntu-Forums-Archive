---
title: "Webcam problem after kernel update 3.5.0.25.31 in 12.10"
date: 2013-02-25
forum: General Help
---

### Post by dfarthur on 2013-02-25
I've been running Ubuntu for a couple of months now and just encountered my first real problem.

Cheese, skype & google hangouts are all unable to display the webcam image after the kernel update 3.5.0.25.31

The webcam was working before - and still works if I boot using my older kernels - but don't know what to do to make it work when using the latest kernel update (or how to report the bug).

The webcam is a BisonCam NB Pro.

Thanks.

---

### Post by kclark on 2013-02-25
How did you upgrade the kernel, did you apt-get it for your system or install a generic kernel?

---

### Post by dfarthur on 2013-02-25
Just by using the updates from the Ubuntu Software Center.

---

### Post by dfarthur on 2013-02-25
Just tested it with GUVCViewer and it works perfectly. Still nothing with any other app though :-S

---

### Post by jedsled on 2013-02-27
Exactly the same problem. guvcview works but skype and cheese do not work.

PC: Lemur Ultra 4
Camera: BisonCam NB Pro

---

### Post by dfarthur on 2013-03-18
Problem has been resolved on my machine with the 3.5.0-26-generic update.

---

