---
title: "Poor quality downscaled images"
date: 2015-02-06
forum: General Help
---

### Post by AlexVargas on 2015-02-06
Hello! :)

I'm relatively new to Ubuntu, I've been using it for about 3 monsths now. Ever since I use it I've noticed that everytime an image is downscaled in Ubuntu, it gets distorted, no matter the application where it's being used. This also appears when switching desktops or previewing windows.

This is very anoying and represents a real problem for me because I am trying to use Ubuntu for my work as visual artist. Ubuntu is a great OS, but this issue has been bothering me and I can't seem to find a solution anywhere.


Here are some screenshots:

 [[IMG]http://s16.postimg.org/johnfwvsh/Screenshot_from_2015_02_06_05_32_21.jpg[/IMG]]("http://postimg.org/image/johnfwvsh/")  [[IMG]http://s16.postimg.org/g3lrwor8x/Screenshot_from_2015_02_06_05_34_24.jpg[/IMG]]("http://postimg.org/image/g3lrwor8x/")  [[IMG]http://s2.postimg.org/8vhrqhxrp/Screenshot_from_2015_02_06_06_09_55_CROPPED.jpg[/IMG]]("http://postimg.org/image/8vhrqhxrp/")



Same image with different zoom values. You can see the actual size of the image.
[[IMG]http://s16.postimg.org/ntsk1ttkh/Screenshot_from_2015_02_06_05_58_43.jpg[/IMG]]("http://postimg.org/image/ntsk1ttkh/")  [[IMG]http://s16.postimg.org/r70sojn5d/Screenshot_from_2015_02_06_05_59_19.jpg[/IMG]]("http://postimg.org/image/r70sojn5d/")  


My system's brief especifications.
[IMG]http://s16.postimg.org/u67pbnwmt/Screenshot_from_2015_02_06_06_00_13.png[/IMG]


I hope the description is understandable enough and that you can help me find a solution to this issue. 
Thank you so much for your help in advance.

---

### Post by Elfy on 2015-02-06
*Thread moved to **General Help**.*

---

### Post by kjohri on 2015-02-06
I suggest that you may open the image in Gimp. The resolution of image and that of the desktop might not be matching, hence the distortion. You might consider cropping the image to the aspect ratio of the desktop so that it is not distorted during display.

---

### Post by mcduck on 2015-02-06
There's not going to be any single solution. The scaling quality depends on the program doing the scaling, there's no universal scaling built into the OS that all your aplications, desktop and everything would use.

So, some image viewing programs and image editors will do better job at scaling images than others do. For the desktop effects scaling, there's a quality setting available in through CompizConfig Settings Manager, by default it's set to "fast" as far as I can rember.

---

### Post by AlexVargas on 2015-02-06
Oh I see... I guess you're right [**[COLOR=#000000]mcduck[/COLOR]**]("http://ubuntuforums.org/member.php?u=17309"), I opened the images in Gimp as [**[COLOR=#000000]kjohri[/COLOR]**]("http://ubuntuforums.org/member.php?u=733211")  suggested and the rendering quality was way much better, so I think it  is indeed related to the application and viewer I'm currently using.

 I'll try finding some other viewing applications and changing the settings in Compiz to see if the desktop quality improves...

Thank you so much for your help! :)

---

### Post by SeijiSensei on 2015-02-06
I've used GIMP to resize and rescale the image before trying to use it as, for instance, a desktop wallpaper.

---

