---
title: "AAC won't work even after i've installed gstreamer0.8-faac"
date: 2005-05-10
forum: General Help
---

### Post by rjs on 2005-05-10
after much heartache, i finnaly managed to get aptitude to work from behind my network, added hoary-extras, downloaded gstreamer0.8-faac.... but Rhythmbox  and totem, still cant play my freaking AACs (totem at least gives an error msg, Rhythmbox tries for about 5 secs, gives up then goes to the next, and the next and the next...)

Now yes, i know i should have all my stuff as ogg, and believe me i'd like to, but ive already paid apple $200 for my iPod, and so i need aac support, even to just be able to put new songs on there (its a shuffle, and before you say i paid too much they were AU$s).

does anyone have any ideas of what could be screwing up?

thanks,
rjs.

---

### Post by Xian on 2005-05-10
Does it have to be Rhythmbox or totem?

---

### Post by SepheeBear on 2005-05-10
Did you run `gst-register-0.8` after installing the gstreamer plugins? Also, you didnt mention, do you have gstreamer-faad as well? That's the one that actually decodes the aac for rhythmbox. faac would be used to encode an aac from something else.

---

### Post by rjs on 2005-05-10
oh god i feel so freaking stupid. RTFW indeed.
faad not faac, god *bangs head agianst wall*

it now works like a charm, thanks a million.

-rjs.

---

### Post by rjs on 2005-05-11
So close, yet so far....

Ok, i thought all was peachy, but aparently not...
Aparently Rhythmbox doesnt do iPod updates, so i had to get gtkpod instead, and while this managed to read all the stuff off my iPod (shuffle - took me a while to figure out that suffles live in a different space to where normal iPods live, and so i had to change that setting) but only the Mp3s from my library on the computer. Now since most of my library is in AACs, this isnt very helpful (and also since the shuffle is only a gig, the space difference is also very important).

it complained.
 
<quote>
Import of '/home/quijote/Desktop/music/6-09 Piano Concerto No. 1 i.m4a' failed: m4a/m4p/m4b not supported without the mp4v2 library. You must compile the gtkpod source together with the mp4v2 library
<quote>

But i cant seem to find this library anywhere, and i dont get why it could deal with the AACs no my iPod but not the ones in my library.

any ideas.

thanks,
-rjs

---

### Post by Martey on 2005-05-12
rjs, I am incidentally having the same problems with gtkpod and rhythmbox. The m4a files in my library work fine in totem (with the gstreamer framework), but are not imported into rhythmbox or muine (muine also does not import some MP3 files, though). I am using a regular 20 GB iPod.

---

### Post by vassie on 2005-05-12
FAAC is the encoder, you want gstreamer0.8-faad

Ben

---

### Post by Martey on 2005-05-12
I already have gstreamer0.8-faad and gtkpod-aac. totem-gstreamer can play m4a files, but everything else (gnome's "hover" preview, rhythmbox, muine, etc.) will neither play nor import m4a files.

---

### Post by monkman on 2005-05-27
as i'm new to ubuntu, just switched from gentoo i encouter the same problems.
in my case i think i have to add the correct source for the libc6 to upgrade it. but where do i get it?

```
root@chateau-de-monk:/home/monkman # apt-get install gstreamer0.8-faad
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gstreamer0.8-faad: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
E: Broken packages
root@chateau-de-monk:/home/monkman # apt-get install libc6
Reading package lists... Done
Building dependency tree... Done
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

THANK YOU

---

### Post by Martey on 2005-05-29
[QUOTE=monkman]as i'm new to ubuntu, just switched from gentoo i encouter the same problems.
in my case i think i have to add the correct source for the libc6 to upgrade it. but where do i get it?

```
root@chateau-de-monk:/home/monkman # apt-get install gstreamer0.8-faad
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gstreamer0.8-faad: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
E: Broken packages
root@chateau-de-monk:/home/monkman # apt-get install libc6
Reading package lists... Done
Building dependency tree... Done
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

THANK YOU[/QUOTE]
 If you install a Debian version of gstreamer-faad, you will need a debian version of libc6. Since several other Ubuntu packages depend on libc6, this could cause severe problems with dependencies. It you probably be better to get a gstreamer-faad package that was built with the Ubuntu version of libc6 as a dependency.

---

### Post by Zhukov on 2005-05-30
I did this to install gstreamer0.8-faad, so I dont know what worked

Comment the marillat reps (add a # before them on /etc/apt/sources.list)

add this

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports-staging main universe multiverse restricted

sudo apt-get update

sudo apt-get install gstreamer0.8-faad


Then you can undo what you've done.


Hope it works for you to.


 :grin:

---

### Post by SKLP on 2005-07-15
If you want to use Muine with AAC check out [this](http://ubuntuforums.org/showthread.php?t=33844).

If you use muine you can also compile ipod-sharp and muine-ipod from snorp.net.
I did that and now i have AAC support and automatic sync of my muine music library :)

---

