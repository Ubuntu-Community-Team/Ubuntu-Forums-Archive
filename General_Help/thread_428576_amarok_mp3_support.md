---
title: "amarok mp3 support"
date: 2007-04-30
forum: General Help
---

### Post by element_G on 2007-04-30
I just lost my mp3 playback in amarok (meaning that they were playing fine yesterday). So I did a bit of searching and found that the required packages for mp3 support are:
libxine1
libxine-extracodecs
libmand0
I checked, and had all installed so I completely removed them along with amarok, and then installed them again, still no luck. Amarok still complains that there is no mp3 support and when I click the 'install mp3 support' button nothing happens. All my other media players (juk, noatun, xmms) have lost their mp3 support too.
I'm running kubuntu fiesty. Is there a magical package that eludes me? Or am I missing something obvious?
Any help is muchly appreciated
thanks

---

### Post by Hairy_Palms on 2007-04-30
try installing ubuntu-restricted-extras package

---

### Post by strabes on 2007-04-30
install ubuntu-restricted-extras and libxine-extracodecs. That's all it should take.

```
sudo aptitude install ubuntu-restricted-extras libxine-extracodecs
```

---

### Post by element_G on 2007-04-30
Thanks for the quick replies, I have both those packages, but regarless I ran:
```
sudo aptitude install ubuntu-restricted-extras libxine-extracodecs
```
and got:
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  wine
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
```

I'm assuming this means I already have those packages installed.

---

### Post by patrickfromspain on 2007-04-30
make sure amarok is using xine engine.. it somewhere in the amarok options.

---

### Post by element_G on 2007-04-30
Thanks again for the quick response.
Tools>configure amarok>engine 
shows me I am using the xine engine.
Just to be sure I brought up synaptic which tells me I have amarok-xine 2:1.4.5-0ubuntu7
which is the latest version.

---

### Post by element_G on 2007-04-30
no more ideas anyone? :(

---

### Post by element_G on 2007-04-30
shameless bumping....

---

### Post by Tenicus on 2007-04-30
I had the same problem
It would say it was installed but when I tried to play an mp3 it would say please download support
I eventually just downloaded Exaile

---

### Post by Oki on 2007-04-30
Perhaps this thread can help:
[http://ubuntuforums.org/showthread.php?t=421527&highlight=amarok+%2B_sAm_](http://ubuntuforums.org/showthread.php?t=421527&highlight=amarok+%2B_sAm_)

---

### Post by element_G on 2007-04-30
thanks, Exaile! works for me, while this will do for now because I absolutely must be able to play my mp3's, I'd still like to amarok working again.

---

### Post by aalr1986 on 2007-04-30
I had the exact same problem. And, actually my XMMS didn't work properly, cause the eq didn't work at all.
I installed Beep Media Player, and it has an EQ, and it looks a lot like XMMS, or let's say, looks a lot like Winamp, also. It has an EQ, it has mp3 support, and for me, it works perfectly.

Give it a try.

---

### Post by Oki on 2007-04-30
Perhaps you didnt see my post, but in this thread([http://ubuntuforums.org/showthread.p...marok+%2B_sAm_](http://ubuntuforums.org/showthread.p...marok+%2B_sAm_)) are the solution to fix the problem with mp3 in amarok....

---

### Post by element_G on 2007-04-30
Oki, thanks for reminding me, I tried running that script as root, and as user and then starting amarok as root and then as user here's my result:
amarok will play MP3's as root
but not as user.

This is really puzzling. 
Just for kicks, I tried this with Noatun and I get the same result. No playback as user, but playback works as Root.

Edit: Sorry, Noatun and XMMS are behaving themselves, they can play mp3's as user.

---

### Post by element_G on 2007-04-30
another shameless bump...

---

### Post by element_G on 2007-04-30
and another shameless bump....
any ideas anyone? :(

---

### Post by element_G on 2007-04-30
another bump (ok, some shame this time)
but seriously any ideas? please?

---

### Post by strabes on 2007-04-30
Don't bump stuff for at least a few days.

---

### Post by element_G on 2007-05-01
understood, sorry for getting out of hand there ;)

---

### Post by strabes on 2007-05-01
I just thought of something. Have you tried purging amarok? sudo apt-get purge amarok

That will delete the configuration files and things. Then try to reinstall it. I have no idea if that wlil work, I just thought of it now.

---

### Post by element_G on 2007-05-01
Had to use aptitude to do the purge thing, 
Then I installed amarok, amarok-xine, kubuntu-desktop, and for good measure libxine-extracodecs,

I still have the same issue. Amarok will complain that it does not have mp3 support when started as user
but does not complain (and plays mp3's) when started as root.

---

### Post by element_G on 2007-05-05
Patiently waiting for some wisdom ;)

---

### Post by diablo69er on 2007-05-05
> **element_G said:**
> Patiently waiting for some wisdom ;)

And here it is, I just got mine working.  I am using 7.04 for the record.

In a terminal type

```
/usr/lib/amarok/install-mp3
``` *You have to restart Amarok at this point*

from there I typed in

```
 sudo apt-get install libxine-extracodecs
```


Hope this helps.

---

### Post by pyromithrandir on 2007-05-09
element_G: I was having a similar problem. Amarok lost mp3 playback for me. It was because of the xine backend. I first actually noticed it when I was trying to watch an .avi in xine, which didn't work, then neither did .mp3s. Running xine as root allowed me to play stuff, and I could play .mp3s and .avis with other non-xine backed players like mplayer and xmms.  Here's how I fixed mine:

> $mkdir ~/.xine/plugins/
$cp -r /usr/lib/xine/plugins/1.1.4/ ~/.xine/plugins/
Just copy all of the xine codec things into the plugins directory (which you may have to make) in the .xine directory in your home directory and everything should work out. It did for me.

---

### Post by element_G on 2007-05-12
Thank you pyromithrandir, works quite nicely ;) I'm now enjoying amarok again. I don't really think there are any viable replacements to this program.

---

### Post by eldersoares on 2007-05-13
thanks a LOT!!!!!!!!! i had the same problem today and this last trick worked for me too!!!! amarok is really unreplaceble. even thoug my xmms was working, i couldnt live w/out amarok! :)

---

### Post by akudewan on 2007-05-16
Thanks a lot mate! :) I was having the same problem. I just made symlinks instead of copying.

---

### Post by pyromithrandir on 2007-05-16
Oh, man! What a good idea. I hadn't even thought to use symlinks. Really, though, you only need one symlink. Just > ln -s /usr/lib/xine/plugins/ ~/.xine/plugins
 That will even keep it up to date through new versions and codecs, in case any files move.

---

### Post by karachuonyo on 2007-06-08
> **pyromithrandir said:**
> Oh, man! What a good idea. I hadn't even thought to use symlinks. Really, though, you only need one symlink. Just  That will even keep it up to date through new versions and codecs, in case any files move.

Great post man. I just realised i've lost mp3 support for 2 of the worlds greatest multimedia apps and that little trick worked like magic. Probably should be added somewhere in the guide. So if you lost mp3 support and previously had it , then should do the trick.:D
  code
  ln -s /usr/lib/xine/plugins/ ~/.xine/plugins

---

### Post by hieronymous on 2007-08-20
Many, many thanks for this. I think I would have gone insane had I had to continue using xmms. Any idea what causes the xine disruption?

---

### Post by Nigro on 2007-09-05
Hi people! this forum has just been a great help to me with Ubuntu 7.04... I'm new to Ubuntu, have worked a bit with RedHat but I find this the best... I was using Rhythm Musicbox but didnt like the way it worked, I love my music, in this forum I came across Amarok installed it using synaptic and it complained that it had no MP3 support.. I just installed libxine-extracodecs and in the command line  /usr/lib/amarok/install-mp3 and it worked fine.......

---

### Post by buks on 2008-02-13
Hi Everyone, 
Thanx for all your help. Here is what I had to do to get it working in Kubuntu Hardy Alpha 4:
1) Installed the restricted packages as suggested.
```
sudo apt-get install ubuntu-restricted-extras libxine-extracodecs
```
2) Create a symlink to the xine plugins
```
ln -s /usr/lib/xine/plugins/ ~/.xine/plugins
```
3) Installed the libxine-extracodecs, which has been replaced by libxine1-ffmpeg in hardy :KS
```
sudo apt-get install libxine1-ffmpeg
```

---

### Post by koji on 2008-05-01
In case it helps somebody in the future.

Today my amarok in kubuntu Hardy complained about the same problem. It was working ok some days ago and I haven't removed any package in the meantime, so I knew I had the right xine plugins installed.

Before start reinstalling packages and linking the plugins directory try deleting the file ~/.xine/catalog.cache It can eventually be corrupted and crash some xine capabilities.

Actually linking the plugins directory forces xine to re-create the file which is what did the trick for me.

I can't swear it 100% because when I realized about this I already had followed all the suggestions in this thread, but now I have deleted the plugins link in ~/.xine and amarok is happily playing mp3's

---

### Post by itmanvn on 2008-05-14
> **koji said:**
> In case it helps somebody in the future.

Today my amarok in kubuntu Hardy complained about the same problem. It was working ok some days ago and I haven't removed any package in the meantime, so I knew I had the right xine plugins installed.

Before start reinstalling packages and linking the plugins directory try deleting the file ~/.xine/catalog.cache It can eventually be corrupted and crash some xine capabilities.

Actually linking the plugins directory forces xine to re-create the file which is what did the trick for me.

I can't swear it 100% because when I realized about this I already had followed all the suggestions in this thread, but now I have deleted the plugins link in ~/.xine and amarok is happily playing mp3's

You're right! Just delete the file ~/.xine/catalog.cache then amarok will playing mp3's:lolflag:

---

### Post by JDVyska on 2008-05-14
For the record, I just built a new Hardy machine last night and had these Amarok problems this afternoon.

Amarok popped up asking me to install MP3 support, I hit OK, it complains that I need to install libxine1-ffmpeg manually.

I jump to terminal, try to
```
sudo apt-get install libxine1-ffmpeg
```
No dice, it complains.

So, I went into Synaptic, Settings, Repositories.  I checked:
 * Community-maintained Open Source Software (universe)

I then tried the above install again, and it worked fine.  Quick restart of Amarok - everything was fine.  No cache zapping, no symbolic links, etc.    In theory, one could go enable that Repo and let Amarok do the install for you as well, as it would now work.

Hope this simple solution helps some folks out.   (Yay, my first "this worked for me" post!)

---

### Post by tomm3h on 2008-07-20
> **koji said:**
> In case it helps somebody in the future.

Today my amarok in kubuntu Hardy complained about the same problem. It was working ok some days ago and I haven't removed any package in the meantime, so I knew I had the right xine plugins installed.

Before start reinstalling packages and linking the plugins directory try deleting the file ~/.xine/catalog.cache It can eventually be corrupted and crash some xine capabilities.

Actually linking the plugins directory forces xine to re-create the file which is what did the trick for me.

I can't swear it 100% because when I realized about this I already had followed all the suggestions in this thread, but now I have deleted the plugins link in ~/.xine and amarok is happily playing mp3's
You're a legend. Same thing had happened to me this morning.. I couldn't remember installing/changing anything yesterday (and my apt logs confirmed this) so I found this thread.

Random corruption would certainly explain it, I think. Running as root was fine (probably just for a fresh catalog.cache), and the plugins symlink did the trick too.

But I removed the symlink and nuked catalog.cache.. Worked a treat, thanks! :)

---

