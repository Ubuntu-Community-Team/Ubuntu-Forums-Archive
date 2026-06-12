---
title: "CompizFusion woes"
date: 2008-05-27
forum: General Help
---

### Post by RussianRedScorpion on 2008-05-27
QQ!!

andrey@andrey-laptop:~$ compiz --replace
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with nVidia drivers...
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

Hello everyone!
I am new to these forums (and Linux in general), and am trying to get CompizFusion...
No luck so far. I have used the directions from this website:
[http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml](http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml)
I noticed I couldn't download something along the way...

What do you guys think?
Thanks in Advance

---

### Post by overdrank on 2008-05-27
> **RussianRedScorpion said:**
> QQ!!

andrey@andrey-laptop:~$ compiz --replace
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with nVidia drivers...
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

Hello everyone!
I am new to these forums (and Linux in general), and am trying to get CompizFusion...
No luck so far. I have used the directions from this website:
[http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml](http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml)
I noticed I couldn't download something along the way...

What do you guys think?
Thanks in Advance

HI and welcome, that "how to" is for feisty 7.04, what version of ubuntu are you using? What is the model of the graphics card on the system? You can locate by using the command ```
lspci 
``` in the terminal that is located under applications, accessories. Look for VGA

---

### Post by RussianRedScorpion on 2008-05-27
lol I am running 8.04...

whoopsie...I thought that Linux was more...compatible.

Well now that I know why that didn't work out, does anyone have a set of directions for installing CompizFusion for a total Ubuntu-n00b like me?

I am migrating from SLIzone forums, so I may use words like "n00b" and stuff (referring to myself for now).

BTW, I tried using Synaptic to install CompizFusion, but that didn't work out either...
Do I have to somehow configure it?

Thanks in Advance

---

### Post by issih on 2008-05-27
Compiz fusion is already installed in 8.04, by default. It comes with 2 preset setups utilising different plugins.

Open up System->Preferences->Appearance, and go to the Visual effects tab.

Simply select Normal for a lowish level of effects, or extra for lots of bells and whistles.

If you cannot enable either of these, then you almost certainly need to use different drivers for your video card, if thats the case, let us know the model and we can try to set you on the right path.

Assuming it does work, you can install the package compizconfig-settings-manager to allow you to tune the effects to your own personal taste.

Hope thats useful

---

### Post by RussianRedScorpion on 2008-05-27
Thanks for that.
I did have that enabled initially though (the windows wiggle and everything)...I just want to see the floating cube and stuff...and to have the apple-style tray at the bottom...
The Uber-bells-and-wistles...

Is that possible?
Thanks in Advance!

---

### Post by strabes on 2008-05-27
sudo aptitude install compizconfig-settings-manager

---

### Post by RussianRedScorpion on 2008-05-27
> **strabes said:**
> sudo aptitude install compizconfig-settings-manager

What did that do???

---

### Post by overdrank on 2008-05-27
> **RussianRedScorpion said:**
> What did that do???

Hi and that will let you configure your settings in compiz. It will be located under system, preference, advance desktop effect. If you added the Feisty repos as the "how to " instructed then I would advise to undo. It may cause serious issues.

---

### Post by RussianRedScorpion on 2008-05-27
Thanks a lot dudes!
This flipping-cube thing is awesome!
I'm pretty sure Linux will be my main OS once I get some games running!
TANGOO!

---

### Post by issih on 2008-05-27
I noticed that you want to have an apple style bar, in which case you'll want to install a "dock" application. Personally I use Avant Window Navigator, but there are also various others such as cairo dock and kiba dock.

Most of these are in the repositories, if you open add remove programs and search for dock you should find some of them..

Glad you got the cube working, it can be a bit confusing at first

---

### Post by RussianRedScorpion on 2008-05-28
Cool.
So far I installed the AWN program, but System > Preferences > Awn Manager does not open.

QQ

Any ideas why this is so?

Thanks in Advance

---

### Post by issih on 2008-05-29
You have to launch the actual awn dock at least once before you can open the manager, I think its launcher gets placed in Accessories. You do have to be running a compositing window manager (read compiz) for awn to work, but then, if you have the cube working, you are :)

---

