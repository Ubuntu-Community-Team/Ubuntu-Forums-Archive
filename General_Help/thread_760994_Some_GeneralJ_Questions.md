---
title: "Some GeneralJ Questions"
date: 2008-04-20
forum: General Help
---

### Post by MosMusy on 2008-04-20
Just got Ubuntu and I love it so far (I also have a duel platform XP/Ubuntu). And I just had some questions:

1) I want to type in Armenian script how do I do it?
2) There are two icons on my desktop (local data & disk) but cannot remove the icons for some reason. 
3)I have a tablet pc, is there a way to install a driver so I can write with my tablet pen?
4) I have seen people do this cool cube thing with the screen how do you do that?
5) Any other advice you have for me?

Thank you for your help

---

### Post by scragar on 2008-04-20
1. go system > administration > Language support and change the default, not everything will change though, these programs would either not support some languages, or have their own options.

2. anything mounted to /media appears on the desktop, it's possible to change the mount point thus avoiding the icons. Post feadback from ```
mount
``` and I'll provide steps(this will also remove them from the places menu, be warned).

3. not sure.

4. it's compiz, check system > preferences > appearance and the visual; effects tab too see if your graphics card supports it.

5. learn where the terminal is(Applications > Accessories > Terminal), other than that have fun.

---

### Post by brownknight on 2008-04-20
> **MosMusy said:**
> Just got Ubuntu and I love it so far (I also have a duel platform XP/Ubuntu). And I just had some questions:

1) I want to type in Armenian script how do I do it?

Maybe try: go to > System > Preferences > SCIM > Input Method Setup > Global Setup

> 2) There are two icons on my desktop (local data & disk) but cannot remove the icons for some reason. 


Do you mean you dont want the icons to show on the desktop? Open a terminal (Applications > Accessories > Terminal) and type:

gconf-editor

A window will pop-up. Go to >apps >nautilus >desktop and unclick Volume Visible

> 3)I have a tablet pc, is there a way to install a driver so I can write with my tablet en?

Yes you can install a driver to be able to use the tablet. I'll get back to you on what to do...

> 4) I have seen people do this cool cube thing with the screen how do you do that?
It is called 3D desktop effects. If your video card can handle this feature then you can enable this from > System > Preferences > Appearance... Go to tab Visual Effects and Choose normal. You will get the normal sliding desktops. Now to get the cube effects you need to install additional program: CCSM. 

To install this go to > Applications > Add/Remove and search for CCSM  (Advanced Desktop Effects Settings). Install this and go back to the Appearance tab and select Custom and you will see all these additional options.

[quote}5) Any other advice you have for me?

Thank you for your help[/QUOTE]

A great way to start is by reading the ubuntu help file from >Sytems > Help and Support

---

### Post by MosMusy on 2008-04-20
The thing is for the Armenian script is,

I cannot change it in the international menu because it's only set to English, and the input method setup does not have Armenian.

---

### Post by MosMusy on 2008-04-20
Every time I try to install a flash plugin, I download it, then after clicking on the file it takes me to it's code instead of installing it? Is there a way around this?

---

### Post by brownknight on 2008-04-20
> **MosMusy said:**
> The thing is for the Armenian script is,

I cannot change it in the international menu because it's only set to English, and the input method setup does not have Armenian.

There is an Armenian langugage pack in Synaptics. You can install it by going to > System > Administration > Synaptic Package Manager... Seach for "Armenian language" 

in the results listed, select and install

language-support-hy
language-pack-gnome-hy-base

other required packages will automatically be selected and installed. I hope this works for you.

---

### Post by MosMusy on 2008-04-20
> **brownknight said:**
> There is an Armenian langugage pack in Synaptics. You can install it by going to > System > Administration > Synaptic Package Manager... Seach for "Armenian language" 

in the results listed, select and install

language-support-hy
language-pack-gnome-hy-base

other required packages will automatically be selected and installed. I hope this works for you.

There the only language packs were English ones.

---

### Post by brownknight on 2008-04-20
> **MosMusy said:**
> Every time I try to install a flash plugin, I download it, then after clicking on the file it takes me to it's code instead of installing it? Is there a way around this?

Install "Ubuntu restricted extras" from >Applications > Add/Remove... Installing this package will pull in support for MP3 playback and decoding, support for various other audio formats (gstreamer plugins), Microsoft fonts, Java runtime environment, Flash plugin, LAME (to create compressed audio files), and DVD playback.
Please note that packages from multiverse are restricted by copyright or legal issues in some countries

---

### Post by brownknight on 2008-04-20
> **MosMusy said:**
> There the only language packs were English ones.

I dont know why it's not appearing in yours but it should like this photo attached:[IMG]http://img.auctiva.com/imgdata/4/6/6/8/9/2/webimg/126379535_o.png[/IMG]

---

### Post by rune0077 on 2008-04-20
Also, if it's just the keyboard you want, you should be able to change the keyboard layout in System > Preferences > Keyboard. Then select "add" and add the layout you want, and remember to make sure it is set as the default keyboard.

---

### Post by MosMusy on 2008-04-20
> **rune0077 said:**
> Also, if it's just the keyboard you want, you should be able to change the keyboard layout in System > Preferences > Keyboard. Then select "add" and add the layout you want, and remember to make sure it is set as the default keyboard.

Ok, thanks now that works (for word processing only though) now I have to get to work in a browser like firefox

---

### Post by brownknight on 2008-04-20
> **MosMusy said:**
> Ok, thanks now that works (for word processing only though) now I have to get to work in a browser like firefox

You can install a firefox add-on. I found this one from mozilla add-ons: Quick Locale Switcher

[https://addons.mozilla.org/en-US/firefox/addon/1333](https://addons.mozilla.org/en-US/firefox/addon/1333)

---

