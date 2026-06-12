---
title: "Where can I find a deb with Gaim 2.0 beta 4?"
date: 2006-10-29
forum: General Help
---

### Post by Starlight on 2006-10-29
I found one in this thread--->[http://www.ubuntuforums.org/showthread.php?t=280739](http://www.ubuntuforums.org/showthread.php?t=280739) but when I try to download it, I get a 404 error... :(

---

### Post by _lynX on 2006-10-29
If you simply download one of the .rpm-format files off of the Gaim website, you can use a program called alien to convert it to a .deb file. 

To install alien:
```

sudo aptitude install alien

```

To convert the .rpm to .deb:
```

cd ~
wget http://easynews.dl.sourceforge.net/sourceforge/gaim/gaim-2.0.0-0.beta4.fc1.i386.rpm
alien -d gaim-2.0.0-0.beta4.fc1.i386.rpm

```

You should now have a file named gaim-2.0.0-0.beta4.fc1.i386.deb, or something similar to that.

---

### Post by PriceChild on 2006-10-29
Yeah i'm getting that error too.

May i ask what's wrong with beta3 in Edgy?

---

### Post by _lynX on 2006-10-29
> **PriceChild said:**
> May i ask what's wrong with beta3 in Edgy?

I haven't noticed anything. Some people just like to stay on top of updates though.

---

### Post by Robvdl on 2006-10-29
> **PriceChild said:**
> May i ask what's wrong with beta3 in Edgy?

Nothing wrong with BETA 3, I just like the single avatar for all your chat accounts, a very simple feature, but long overdue. I also like the fact that your avatar now shows up on the main window, although this is only cosmetic.

Anyway, I found the post by Kevin earlier on today, and already sent him a PM, asking if he could please kindly upload them to another server if he still has them.

There is another BETA 4 deb here:

[http://ubuntuforums.org/showthread.php?t=280488](http://ubuntuforums.org/showthread.php?t=280488)

...except the sound doesn't work in this build, the dropdown box for sound output, only has the options "Console Beep", "Commands", or "No Sound". Apparently you can fix this by using a command "aplay", but wouldn't that be slower, always calling an external program - sounds messy to me. There is also no matching gaim-data package for this build, so I am really hoping Kevin can upload his build again.

---

### Post by Kevin on 2006-10-30
Alright so I'm not sure what happened to those files on the other host, so I stuck them in a tar.gz file and tried another site (obviously you have to extract it first to get the debs...).  These are compiled from the debian sources, and you need to install gaim-data and gaim at the least.

[http://w10.easy-share.com/662567.html]("http://w10.easy-share.com/662567.html")

Let me know if it works, and if anyone can host them somewhere proper or knows of a place that's better, let me know.

---

### Post by shm on 2006-10-30
> **Kevin said:**
> Alright so I'm not sure what happened to those files on the other host, so I stuck them in a tar.gz file and tried another site (obviously you have to extract it first to get the debs...).  These are compiled from the debian sources, and you need to install gaim-data and gaim at the least.

[http://w10.easy-share.com/662567.html]("http://w10.easy-share.com/662567.html")

Let me know if it works, and if anyone can host them somewhere proper or knows of a place that's better, let me know.

It works! Thanks! i'm share it on my ftp server! [ftp://80.86.249.14/gaim](ftp://80.86.249.14/gaim)
also theare guifications gaim-guifications_2.13beta4-1_i386.deb (build with checkinstall)

---

### Post by Robvdl on 2006-10-30
> **Kevin said:**
> Alright so I'm not sure what happened to those files on the other host, so I stuck them in a tar.gz file and tried another site (obviously you have to extract it first to get the debs...).  These are compiled from the debian sources, and you need to install gaim-data and gaim at the least.

[http://w10.easy-share.com/662567.html]("http://w10.easy-share.com/662567.html")

Let me know if it works, and if anyone can host them somewhere proper or knows of a place that's better, let me know.

Great, this version works perfectly, sound works in this version, no longer need to to use the command "aplay %s" in this build, thanks for this.

Just a quick note to anyone that may be installing this, I installed using the following:

```

sudo dpkg -i gaim-data_2.0.0+beta4-1ubuntu0_all.deb gaim_2.0.0+beta4-1ubuntu0_i386.deb

```

However, gaim depended on libavahi-compat-howl0 >= 0.6.0, edgy has 0.6.13 in the repositories, but dpkg didn't install it for me, and I got a "broken packages" when trying to install gaim.

No problems, I quickly fixed the broken packages by reverting gaim and gaim-data back to 2.0 beta 3.1 using synaptic, and then tried again, this time installing libavahi-compat-howl0 first:

```

sudo apt-get install libavahi-compat-howl0
sudo dpkg -i gaim-data_2.0.0+beta4-1ubuntu0_all.deb gaim_2.0.0+beta4-1ubuntu0_i386.deb

```

Worked perfectly this time. Note to other readers, I also installed the guifications package found here:

[http://ubuntuforums.org/showthread.php?t=280488&page=2](http://ubuntuforums.org/showthread.php?t=280488&page=2)

(last post, by Davidios)

---

### Post by rpaller on 2006-11-01
> **PriceChild said:**
> May i ask what's wrong with beta3 in Edgy?

I have been having problems with GAIM 2.0 beta randomly crashing in Edgy and the previous release of Ubuntu. I had switched to Kopete for a while but would rather have a GNOME based client installed at this time.  ](*,)

---

### Post by bluenova on 2006-11-01
It's real easy to build from [source](http://prdownloads.sourceforge.net/gaim/gaim-2.0.0beta4.tar.gz?download)

Extract it
then:
```

./configure
make
sudo checkinstall
```
It'll then install as a .deb

---

### Post by pianoboy3333 on 2006-11-01
The only bad thing is if you have installed the gaim from the ubuntu main repositories, your dependencies will get messed up, since ubuntu splits the gaim package into gaim-plugins, gaim-dev, gaim, gaim-data, and the like.

---

### Post by mrgnash on 2006-11-02
Works like a charm for me. The avatar thing is really handy :D

---

### Post by Cannedbread on 2006-11-07
[http://cameronbergh.com/mirror/gaim_1:2.0.0+beta4.0-1_i386.deb](http://cameronbergh.com/mirror/gaim_1:2.0.0+beta4.0-1_i386.deb)

---

### Post by kOoLiNuS on 2006-11-11
Beta5 released yesterday:

[http://gaim.sourceforge.net/index.php?id=173](http://gaim.sourceforge.net/index.php?id=173)

any chance to see it {eventually also in backports for Dapper ?}

tnx

---

