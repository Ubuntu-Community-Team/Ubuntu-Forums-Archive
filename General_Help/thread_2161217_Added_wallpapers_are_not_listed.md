---
title: "Added wallpapers are not listed"
date: 2013-07-09
forum: General Help
---

### Post by nodnolse1 on 2013-07-09
Hi, I copied few downloaded wallpapers into '/usr/share/backgrounds/' this should be the default folder for Ubuntu Precise 12.04. After the copy all new wallpapers are correctly listed in 'nautilus' and in 'gnome terminal' but if I right click on the Desktop area clicking on 'Change desktop background' getting the 'Appearance' window, I see only the standard wallpapers, the system default. I rebooted, but again no way to get the new wallpapers icons inside the 'Appearance' window. I also tried to click on the 'plus' button and driving it to the folder '/usr/share/backgrounds/' there I selected few new wallpapers and pressed ok. Now I can see the ones I selected, very well, but at next reboot I get always the default ones and the new ones are always in the same folder but no way to get them listed as icons permanently into 'Appearance' window. I can't understand what I mistake, the OS is fresh installed and works correctly. I hope that someone can teach me how to fix this strange behavior. Thanks for reading, Paolo

P.S. Before to write this post, I searched on search engines and I was unable to find a solution for my specific case, it seems that this problem happens 'only to me'

---

### Post by deadflowr on 2013-07-09
For the wallpaper to get aded to the appearance section, you need to edit the xml file in 
/usr/share/gnome-background-properties.
Depending on which Ubuntu version, it could be precise-wallpapers.xml, or any other.
Here's a generic entry
```
     <wallpaper>    
    <name>whatever you want</name>
    <filename>file location</filename>
    <options>zoom</options>
    <pcolor>#000000</pcolor>
    <scolor>#000000</scolor>
    <shade_type>solid</shade_type>
     </wallpaper>



```

I would copy a clean version of the file first(put it somewhere in your home folder for safe keeping).

---

### Post by BreezyBrooke on 2013-07-09
It was easier to put them in your pictures folder, know that right? :)

---

### Post by nodnolse1 on 2013-07-10
Thanks for answering Deadflowr, I forgotten to specify that there is a sub-folder into backgrounds folder that has inside only a file ant it is an *.xml. Here the path '/usr/share/backgrounds/contest/precise.xml' and the content is here [http://paste.ubuntu.com/5861274/](http://paste.ubuntu.com/5861274/) I also checked the '/usr/share/gnome-background-properties/' folder and inside there are 3 files and all are *.xml. At the foot of the post there are filenames, paths and contents by pasting host. My hope is to find out a way to register the presence of new wallpapers automatically as it was into Ubuntu 10.04 Lucid for instance, or in m$ OS's. Anyway, if you have some suggestion to avoid the manual scripting it is very very welcome, maybe an 'apt-get install macig-wallpapers-xml-auto-registration' ;-) 

Thanks for helping, Paolo



/usr/share/gnome-background-properties/precise-wallpapers.xml  --->  [http://paste.ubuntu.com/5861285/](http://paste.ubuntu.com/5861285/)
/usr/share/gnome-background-properties/ubuntu-wallpapers.xml  --->  [http://paste.ubuntu.com/5861341/](http://paste.ubuntu.com/5861341/)
/usr/share/gnome-background-properties/adwaita.xml                --->  [http://paste.ubuntu.com/5861345/](http://paste.ubuntu.com/5861345/)

---

### Post by grahammechanical on 2013-07-10
There are 3 ways to do this. Two of the ways you have been told about.

1) put the images in the Pictures folder.
2) Edit precise-wallpapers.xml by adding additional sections at the bottom of the list, following the pattern.

[COLOR=#008000][B]<wallpaper>
[/B][/COLOR]    [COLOR=#008000]**<name>**[/COLOR]Winter Morning[COLOR=#008000][B]</name>
[/B][/COLOR]    [COLOR=#008000]**<filename>**[/COLOR]/usr/share/backgrounds/Winter_Morning_by_Shannon_Lucas.jpg[COLOR=#008000]**</filename>**[/COLOR] 
   [COLOR=#008000]**<options>**[/COLOR]zoom[COLOR=#008000][B]</options>
[/B][/COLOR]    [COLOR=#008000]**<pcolor>**[/COLOR]#000000[COLOR=#008000]**</pcolor>**[/COLOR] 
   [COLOR=#008000]**<scolor>**[/COLOR]#000000[COLOR=#008000][B]</scolor>
[/B][/COLOR]    [COLOR=#008000]**<shade_type>**[/COLOR]solid[COLOR=#008000][B]</shade_type>
[/B][/COLOR]  [COLOR=#008000]**</wallpaper>**[/COLOR]
[COLOR=#008000][B]<wallpaper>
[/B][/COLOR]    [COLOR=#008000]**<name>**[/COLOR]New Image[COLOR=#008000][B]</name>
[/B][/COLOR]    [COLOR=#008000]**<filename>**[/COLOR]/usr/share/backgrounds/New_Image_Name.jpg[COLOR=#008000]**</filename>**[/COLOR] 
   [COLOR=#008000]**<options>**[/COLOR]zoom[COLOR=#008000]**</options>**[/COLOR] 
   [COLOR=#008000]**<pcolor>**[/COLOR]#000000[COLOR=#008000][B]</pcolor>
[/B][/COLOR]    [COLOR=#008000]**<scolor>**[/COLOR]#000000[COLOR=#008000][B]</scolor>
[/B][/COLOR]    [COLOR=#008000]**<shade_type>**[/COLOR]solid[COLOR=#008000]**</shade_type>**[/COLOR] 
 [COLOR=#008000]**</wallpaper>**[/COLOR]

or use a utility such as Cortina

[https://help.ubuntu.com/community/Cortina](https://help.ubuntu.com/community/Cortina)

or Wallach

[http://wall-changer.sourceforge.net/](http://wall-changer.sourceforge.net/)

Both are in the software centre. Ubuntu developers allow space for Ubuntu users (community developers) to add functions to Ubuntu.

Regards.

---

### Post by nodnolse1 on 2013-07-10
> **grahammechanical said:**
> There are 3 ways to do this. Two of the ways you have been told about.

1) put the images in the Pictures folder.
2) Edit precise-wallpapers.xml by adding additional sections at the bottom of the list, following the pattern. [CUT] 

Hi grahammechanical, thanks for answering and to have been so detailed, is not usual in forums normally, but when I open a thread, my intention is to solve my problem obviously, but in main time I would like to leave a sort of 'how to' with all details as possible to leave to the people with the same question/problem a very effective, useful infos to debug and solve w/o loose time in millions of post word wild. Sorry for this introduction, but I needed to explain my intents. 

I tried to copy few wallpapers into '~/Pictures/' that are wallpapers copied from others OS's, all are *.jpg. So, basically I'd see themes into 'All settings/Appearance/Pitcures Folder', but no one is listed as icon, but clicking the 'plus' button and driving the wallpapers manager to the '~/Pictures/' folder and selecting all (CTRL+A), I get all the new wallpapers listed as icons into 'Appearance' window. It seems that all is solved, but at next reboot no icons listed again, the good news is that at least it remember the chosen wallpaper before reboot. I also appreciate the suggestion about wallpaper manager/slideshow, but I don't intend to install applications/services that stats at boot time decreasing the boot process also sucking a bit as well when the system is on. Basically are just decorations, nothing of essential or indispensable, but I find very 'bizarre' that Ubuntu developers have made a so complicate system to set and list available extra wallpapers, I use many different OS's since 20 years, and this is the first time that I find a so 'twisted' wallpapers management. Just an example close to Ubuntu, in Lubuntu 12.04 the behavior is like others OS's, so, as root/super user you copy all extra *.jpg you like and in seconds are listed normally as icons in the wallpapers manager. Very strange to me. Anyway, thanks for participating with interest, detailed and with your knowhow. At the moment I stop the thread here if really the only way is to compile manually an *.xml. Thanks again to all, Paolo

---

### Post by deadflowr on 2013-07-10
> [COLOR=#000000]I find very 'bizarre' that Ubuntu developers have made a so complicate system to set and list available extra wallpapers[/COLOR]

So do I, since it's actually a Gnome thing.
The Ubuntu devs tweak the setting with their own wallpapers and such, but the program is all Gnome.

---

### Post by nodnolse1 on 2013-07-11
Thanks for the hint, as soon is possible I'll try a different distro based on 'Gome 3.xx' because on 'Gnome 2.xx' the behavior is exactly as it was on Ubuntu 10.04 Lucid, 'OS X' ([http://tinyurl.com/cdam7af](http://tinyurl.com/cdam7af)) and m$. Probably the 95% of all OS's desktop environment (DE) in the world use the Ubuntu 10.04 way to add extra wallpapers. Anyway, as I already said, wallpapers are the last thing as importance in a OS 'IMHO', then, from now when I'll like to see a new image on desktop background, I'll just try to imagine it by fantasy, and in seconds I can change many images w/o to touch input devices just closing the eyes and let the fantasy works ;-) It is a just joke, not a provocation. Regards, Paolo

---

