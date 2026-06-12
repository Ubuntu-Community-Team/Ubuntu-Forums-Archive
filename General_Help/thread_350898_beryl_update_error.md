---
title: "beryl update error"
date: 2007-02-01
forum: General Help
---

### Post by wwuster on 2007-02-01
I just update beryl items with update manager. But I'm getting this error now:

E: /var/cache/apt/archives/beryl-plugins_0.1.9999.1~0beryl1_i386.deb: trying to overwrite `/usr/lib/beryl/libimgjpeg.so', which is also in package beryl-plugins-extra

I'm running edgy.

How can I fix this?

William

---

### Post by wwuster on 2007-02-01
Also, after rebooting I found that all of my windows have no edges (titlebar, frame), so I can't move them or re-size them.

William

---

### Post by bazcor on 2007-02-01
I had the same problems, I found that completely removing beryl and beryl core, then reinstalling all of the beryl components got it working again.

---

### Post by xpod on 2007-02-01
Having the same issues myself people.

Just did the complete removal\re-install thing.......all to no avail:( 
Seems theres a few others suffering the same kind of problems too though.

Mines worked at first but without the titlebars etc plus i could only right-click the beryl icon and there was no splash screen when i started beryl,or if i tried initiating the splash myself.
Now it just freezes the whole system bar my mouse pointer.

I usually leave such updates for a day or two so that`ll teach me:D
Cant complain as it`s the first real problem i`ve ever had with the thing

---

### Post by ronmarley1 on 2007-02-01
> **bazcor said:**
> I had the same problems, I found that completely removing beryl and beryl core, then reinstalling all of the beryl components got it working again.
This worked for me also.
Thanks.

---

### Post by wwuster on 2007-02-01
Using synaptic I 'completely removed' beryl and beryl-core. Then just reinstalled beryl and all is
OK again.

William

---

### Post by pyrforos on 2007-02-01
not working for me

---

### Post by vexeuz on 2007-02-01
Well.. I think the Beryl team just f-ed up again... They prob released another not fully tested update.

Here how to temporary fix it until they fix the update:

go to synaptic and look at history.

there you will find the pkges that have just been updated.

search for beryl and emerald (one at a time) and you should see those pkges.

mark for reinstallation of each of the pkges that was update to 0.1.9999.1
   -for each: go to Package tab -> select Force Version -> select the old 0.1.99.2 version instead of 0.1.9999.1

That should set it back to normal. Also, just ignore the update notice icon for a while.

---

### Post by xpod on 2007-02-01
Still no titlebars but the freezing has righted itself after a complete removal\re-install but i`ve just realised there are no themes in the emerald theme manager so thats probably something to do with why there aint no titlebars.

The new effects are pretty cool though,even without titlebars:D 
I still have my main setup in good working order and this is just one i mess about on so i`m happy to wait till it`s fixed.

---

### Post by wwuster on 2007-02-01
Although re-installing beryl from synaptic fixed my package error messages, I do see that beryl doesn't run as well as before:

1. when I turn on rain drops (shift f9) my entire screen dims and is barely readable.
2. when I click on the beryl-manager icon in the upper right corner of the screen, it doesn't run the dialog that lets you adjust beryl.

Next time I'll wait a couple of days before doing any beryl updates.

William

---

### Post by palmerthegeek on 2007-02-01
Hey fellow frustrated Beryl's ... I too had the update nightmare!   

Full removal and reinstall worked for me. 

Here is related thread....
[http://www.ubuntuforums.org/showthread.php?t=350892](http://www.ubuntuforums.org/showthread.php?t=350892)

---

### Post by DarkN00b on 2007-02-01
A complete removal and reinstall fixed it for me. I can't install beryl-plugins-extra now because I get the same error, but at least Beryl works. I'll miss the snow plugin...*sniff*

---

### Post by disturbedite on 2007-02-01
> **DarkN00b said:**
> A complete removal and reinstall fixed it for me. I can't install beryl-plugins-extra now because I get the same error, but at least Beryl works. I'll miss the snow plugin...*sniff*

i use kubuntu and this didn't work for me.  i read on one of these threads that beryl-plugins-extra may have been integrated into beryl-plugins, hence it not having an update available.  someone suggested to uninstall the beryl-plugins-extra first and then update, i didn't try that, since i reverted back to the previous version before i read that suggestion, but i might try it now...

---

### Post by ions on 2007-02-01
I'll miss the snow plugin as well.  :(

---

### Post by ions on 2007-02-01
I'm also getting the black application windows even with the Rendering Path set to 'copy'.  Otherwise it seems to perform a little better on my machine.

---

### Post by ions on 2007-02-01
To get snow back:

sudo apt-get install beryl-plugins-unsupported

---

### Post by DarkN00b on 2007-02-02
> **ions said:**
> To get snow back:

sudo apt-get install beryl-plugins-unsupported

Thank you! :)

---

### Post by fsando on 2007-02-02
What about the SVN version?
SVN is now at rc1.
I enabled the svn repositories and took (almost - see below) all updates - it is now running better than ever (ati x1600 on xgl).
Just af few problems: There was an conflict between beryl-plugins and beryl-plugins-extra, I then removed completely beryl-plugins-extra, installed only beryl-plugins. And only after that I installed plugins-extra and plugins-unsupported. That is I didn't install the three in one go.

Cheers and tons of kudos to the Beryl team.
Don't forget they are few and they are actually asking the community help them testing up till the 0.2 release here: [**_[COLOR="RoyalBlue"]Help us go through trac to get 0.2.0-ready[/COLOR]_**]("http://forum.beryl-project.org/viewtopic.php?f=34&t=1618")

---

### Post by shironeko on 2007-02-02
Same here.

Since I updated, the caps stopped working and everything is slower now.

---

### Post by reclusivemonkey on 2007-02-03
> **ions said:**
> To get snow back:

sudo apt-get install beryl-plugins-unsupported

...just another...

Thanks! :) 

I had just found these on gnome-look;

[http://www.gnome-look.org/content/show.php?content=50346](http://www.gnome-look.org/content/show.php?content=50346)

and was really missing snow!

---

