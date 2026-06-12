---
title: "Nvidia Quadro Card driver"
date: 2008-06-06
forum: General Help
---

### Post by raylistic87 on 2008-06-06
Hello, 
Can anyone guide me on how to install the quadro card driver on my ubuntu OS? I been trying out but no avail. I am not familiar with how the whole linux/ubuntu works. If someone can proved me a brief tutorial, that would be cool. 
[http://www.nvidia.com/object/linux_display_ia32_173.14.05.html](http://www.nvidia.com/object/linux_display_ia32_173.14.05.html)

Hopefully someone can make this as my welcome present to this forum, haha!

Thanks a million!
-Ray

---

### Post by PmDematagoda on 2008-06-06
Have you tried installing the driver through Hardware Drivers in System>Administration>Hardware Drivers?

---

### Post by raylistic87 on 2008-06-06
I tried, doesn't seem to work as it is still prompting error in my card. Maybe I have to install the package provided by nvidia? Can someone shed more light on this? :D

---

### Post by PmDematagoda on 2008-06-06
> **raylistic87 said:**
> I tried, doesn't seem to work as it is still prompting error in my card. Maybe I have to install the package provided by nvidia? Can someone shed more light on this? :D

What's the error you are getting?

---

### Post by raylistic87 on 2008-06-10
I tried to follow instructions on nvidia website and i end up getting this error.

```
raylistic@raylistic-desktop:~$ sudo sh NVIDIA-Linux-x86_64-173.14.05-pkg2.run
sh: Can't open NVIDIA-Linux-x86_64-173.14.05-pkg2.run
```

Anyone face this issue before?

---

### Post by PmDematagoda on 2008-06-10
> **raylistic87 said:**
> I tried to follow instructions on nvidia website and i end up getting this error.

```
raylistic@raylistic-desktop:~$ sudo sh NVIDIA-Linux-x86_64-173.14.05-pkg2.run
sh: Can't open NVIDIA-Linux-x86_64-173.14.05-pkg2.run
```

Anyone face this issue before?

Could you please post the error message you are getting? Perhaps if that could be figured out then we don't have to install the Nvidia driver manually.

---

### Post by skymera on 2008-06-10
How about making the file executeable first?

```
 sudo chmod +x FILE.run 
```

Have you tried Envy?

---

### Post by raylistic87 on 2008-06-10
-PmDematagoda 

It is not really error. It is just that the driver is not working really well. I got opengl issues in my 3d software: maya. 

Thanks for the prompt reply!

---

