---
title: "Laptop Webcam not working"
date: 2014-04-06
forum: General Help
---

### Post by Geoff_Lane on 2014-04-06
Folks,

I convinced a friend (6000 miles away) to install Ubuntu on her Gateway laptop due to major Windows7 problems.

She is delighted with it, overwrote the lot so just Ubuntu. I am able to assist with remote computer assistance and ssh.

The webcam however does not appear to work, tried with cheese, skype and vlc - all to no avail.

If I issue command ```

lsmod | grep videodev

```

  I get 107508  3 uvcvideo,videobuf2_core

On mine I get only one driver shown, uvcvideom so could this other driver be the problem and if so how do I change it?

Geffers

---

