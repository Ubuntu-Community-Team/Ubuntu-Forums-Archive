---
title: "Project looking glass"
date: 2005-06-24
forum: General Help
---

### Post by RadixLecti on 2005-06-24
Has anyone tried Sun's Project looking glass?
I saw the video demo a few months back, and been curious since.

---

### Post by z-two on 2005-06-24
I have to say it looks pretty cool. I would like to try it sometime but i expect it would be stupidly slow on my pc.

I'll definately be keeping an eye on it from now on too.

---

### Post by theToolman on 2005-06-28
[QUOTE=RadixLecti]Has anyone tried Sun's Project looking glass?
I saw the video demo a few months back, and been curious since.[/QUOTE]
 I just installed it and it runs fine on my modest hardware; still tuning to get it to work 100% but the demo (lg3d-dev) works well on my athlon 2600 with a fx5200.

---

### Post by michealm on 2005-07-07
[QUOTE=theToolman]I just installed it and it runs fine on my modest hardware; still tuning to get it to work 100% but the demo (lg3d-dev) works well on my athlon 2600 with a fx5200.[/QUOTE]
 how did you get it to work Ive tried everything I keep getting this error:
bash: ./lg3d-dev: /bin/tcsh: bad interpreter: No such file or directory

---

### Post by Jleviaguirre on 2005-11-12
You need to install the tcsh package. I did it from [http://mirror.isp.net.au/ftp/pub/ubuntu/pool/main/t/tcsh/](http://mirror.isp.net.au/ftp/pub/ubuntu/pool/main/t/tcsh/)

After installing tcsh I came up with another isse about the X11 path. I solved it by creating a symbolic link to the right X11 library path or by modifying the lg3d-dev parameters to point to the right path.

---

