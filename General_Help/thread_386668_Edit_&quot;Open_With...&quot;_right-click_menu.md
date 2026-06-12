---
title: "Edit &quot;Open With...&quot; right-click menu"
date: 2007-03-17
forum: General Help
---

### Post by beastmaster on 2007-03-17
I know I can add programs to launch a specific file extension by going through the "Properties" menu, but it's not working in this instance. I want to be able to launch an .avi file with Totem by default, but Mplayer took over (and still resides as the default media app after I uninstalled it).

I guess what I would like to know is how to manually edit the "Open With..." part of the right click menu, and also the default applications for each file type.

---

### Post by chewearn on 2007-03-17
Right-click on the file > Properties > Open With tab.

---

### Post by beastmaster on 2007-03-17
Yeah, I tried that but I've got some sort of strange error going on:

In the right click menu, it says "Open with Mplayer" (which I uninstalled, clicking on this gives an error).
If I go to "Properties->Open with," the only item listed is Movie Player (totem), which is what I want to use.

Ideally, I would just like to gedit whatever file i need to in order to get totem to launch all video files.

---

### Post by strabes on 2007-03-17
Why on earth would you remove mplayer? Mplayer is MUCH better than totem, but I have to say that VLC is the best. 

Did you apt-get purge them? Did you apt-get clean?

I don't know if that will fix your problem but using the open with menu should change the preferences for all files of that type. Executables are located in /usr/bin

---

### Post by beastmaster on 2007-03-24
apt-get purge
apt-get clean

please elaborate on the function/use of these commands.

i've used apt-get to install new packages, but that's about it. i'm still fairly green to ubuntu.

---

### Post by chewearn on 2007-03-25
```
man apt-get
```> 
       clean  clean clears out  the  local  repository  of  retrieved  package
              files.   It   removes   everything   but   the  lock  file  from
              /var/cache/apt/archives/  and  /var/cache/apt/archives/partial/.
              When  APT is used as a dselect(8) method, clean is run automati&#8208;
              cally. Those who do not use dselect  will  likely  want  to  run
              apt-get clean from time to time to free up disk space.
> 
       --purge
              Use purge instead of remove for anything that would be  removed.
              An  asterisk  ("*") will be displayed next to packages which are
              scheduled to be purged. Configuration Item: APT::Get::Purge.
```
man dpkg
```> 
       purge  The package is selected to be purged (i.e.  we  want  to  remove
              everything, even configuration files).
Some descriptions:
[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-clean](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-clean)
[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-remove](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-remove)

---

