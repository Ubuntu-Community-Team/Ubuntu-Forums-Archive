---
title: "Mouse cursor size"
date: 2015-06-19
forum: General Help
---

### Post by scott101 on 2015-06-19
Hello,

I am brand new to Ubuntu, and I am just setting up the OS to my liking.

I am trying to change my cursor size, since I was used to a larger cursor in Windows.

I read through quite a few posts, tellintlg me to do quite a few things, that I didn't really understand.


But pretty much all of them said I should install dconf-editor.....so I did.


In dconf-editor I navigated to org>gnome>desktop>interface.


There I changed the cursor size to a variety of different sizes, pressed enter, and rebooted. Unfortunately for me, the cursor never once changed size.

Is there something I am missing here?

---

### Post by Elizine on 2015-06-19
What all have you tried? Please list at least few things. Still I would suggest you to go through this video tutorial on YouTube - [https://www.youtube.com/watch?v=Yxfa2fXJ1Wc](https://www.youtube.com/watch?v=Yxfa2fXJ1Wc)

---

### Post by v3.xx on 2015-06-19
That link is for 12.04; scott has not said what he is running.  My guess is unity, which I do not run, but take a look here.

 [http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=unity+Mouse+cursor+size+&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=unity+Mouse+cursor+size+&sa=Search&cof=FORID:9)

---

### Post by scott101 on 2015-06-20
I am running unity. Whatever is the current main release.

---

### Post by CantankRus on 2015-06-20
When using the default DMZ-White cursor (24 pixels) in 14.04, you can change the size to 32 pixels with this terminal command...
```
echo "Xcursor.size:32" > ~/.Xresources && gsettings set com.canonical.Unity.Interface cursor-scale-factor 1.35
```

or 48 pixels.....
```
echo "Xcursor.size:48" > ~/.Xresources && gsettings set com.canonical.Unity.Interface cursor-scale-factor 2
```
Log out to complete change.

---

