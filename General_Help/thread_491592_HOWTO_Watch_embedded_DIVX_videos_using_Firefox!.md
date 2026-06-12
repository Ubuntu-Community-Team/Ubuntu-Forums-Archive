---
title: "HOWTO: Watch embedded DIVX videos using Firefox!"
date: 2007-07-03
forum: General Help
---

### Post by Palmyra on 2007-07-03
This is a much needed tutorial since not being able to watch embedded DIVX videos right in Firefox has driven me nuts.  Just installing mplayer-plugin is not sufficient at all, because even after doing that, I was still not able to play embedded DIVX videos.

Anyhow, follow this:

1.  Download the file on the following download site, and save it to your desktop (click on the link that says "Download file"):

[http://www.4shared.com/file/17647095/47518ec7/pluginstar.html](http://www.4shared.com/file/17647095/47518ec7/pluginstar.html)

2.  Uncompress the file you've just downloaded.  Right-click, and "extract."  In this newly created directory, copy all the Firefox extensions from this folder.  Right-click and select "copy."    

2.  Press ALT-F2, and type gksudo nautilus (no quote marks).  This will give you administrative privileges when handling the file manager after you enter your password.

3.  Browse to /usr/lib/firefox/plugins.  In this directory, copy all the Firefox extensions from the folder you earlier uncompressed.  You should paste in this directory all the extensions you have downloaded earlier.  If Ubuntu warns you that you are overriding a certain extension, skip that particular extension, because you already have it!  Just paste the ones you don't already have.

It shouldn't matter if Firefox is open or not, but just in case you're having any problems, restart Firefox (don't restart your computer, just Firefox, if necessary).  

You will need mplayer-plugin for this to work correctly, as far as I know, you will not be able to use mplayer-plugin along with other similar plugins (e.g. mozilla-vlc-plugin, totem-mozilla, etc.).  Once you've completed this guide, Epiphany should be able to play embedded DIVX video too.  

All credit goes to the PCLinuxOS community, and more specifically, vampirefo.  I realize this guide is quite watered down, but it useful in not excluding newbies.

---

### Post by frodon on 2007-07-04
No need to bother with this, if you are using firefox you have an extension made for this purpose, click 3 times and it is done :
[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

---

### Post by r3bol on 2007-07-04
Thanks Palmyra, I've been wanting to do this for ages! I like this method much better than running external players and it also supports the DownloadHelper plugin.
:popcorn:

---

### Post by Palmyra on 2007-07-04
> **frodon said:**
> No need to bother with this, if you are using firefox you have an extension made for this purpose, click 3 times and it is done :
[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

The difference between what you have posted and what I posted is pretty big.  I posted a plugin, and you posted an extension.  If you already have mplayer-plugin, what I posted correctly works with it.  This is different from external extensions, which can be a pain sometimes, including the one you posted.  Furthermore, extensions frequently require setting up preferences (as is with your case), which is not necessary with plugins.

I would recommend people use my guide, because it should be a lot easier for you in the long run.  Also, what happens when your extension becomes outdated with a new Firefox version?  You'll have to wait till the developers get a new version.

Save yourself the headache. 

May I ask why this guide is not in Tutorials and Tips?  I can modify the post to follow forum rules.

---

### Post by frodon on 2007-07-04
> **Palmyra said:**
> The difference between what you have posted and what I posted is pretty big.  I posted a plugin, and you posted an extension.  If you already have mplayer-plugin, what I posted correctly works with it.  This is different from external extensions, which can be a pain sometimes, including the one you posted. Arguments based on fact maybe ?

The extension i posted just open the stream with the player of your choice it don't require anything to install, based on the fact that it is one of the often used firefox extension it don't think it will be outdated as long as firefox exist and is used.

About what the Tips & Tricks section rules just read the sticky of this section.

---

### Post by sefs on 2007-07-05
How can i improve the buffereing using mediaconnetor thing and totem.  Every few seconds it buffers and runs buffers and runs, as opposed to divx webplayer in windows which buffers until it has buffered enough to play to the end without stopping.

We need intelligent buffering, how to achieve this.

Aslo in divx windows version there is the little progress bar you can drag backwards if you missed something...i can't seem to do this in totem.  are they any other linux players that can do these things?

---

### Post by Manowar721 on 2007-07-15
[https://bugs.launchpad.net/ubuntu/+source/mplayerplug-in/+bug/112055](https://bugs.launchpad.net/ubuntu/+source/mplayerplug-in/+bug/112055)

I found the instructions, per that link, very easy to follow.  

[B]You must have mozilla-mplayer installed.  If you don't, type:
$ sudo apt-get install mozilla-mplayer[/B]

[B]I opened a console and typed:
$ cd /usr/lib/firefox/plugins
$ sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
$ sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt

I restarted firefox and retried the divx video and it worked embedded.[/B]

Hope this helps,
Manowar721

---

### Post by ubun2dragon on 2007-07-17
Manowar, followed your easy 1-2-3, embedded divx on Stage6.divx.com plays and downloads in firefox perfectly.  Thanks!

---

### Post by krul on 2007-07-17
> **Manowar721 said:**
> 
...
 Manowar721

This did the trick for me as well!

Please note for Swiftfox users, you have probably to create the links in this location:

/opt/swiftfox/plugins

e.g.[B]
$ cd /opt/swiftfox/plugins
[/B]** $ sudo ln -s /opt/swiftfox/plugins**[B]/mplayerplug-in-dvx.so
$ sudo ln -s /opt/swiftfox/plugins[/B]**/mplayerplug-in-dvx.xpt**

---

### Post by Nessa on 2007-07-17
Worked for a bit. Firefox crashes when it's paused.

---

### Post by fearevilleet on 2007-07-17
I prefer watching streaming divix videos through VLC, it is actually pretty easy. Lets say I want to watch the latest version of Naruto, from[ http://www.tv-links.co.uk/link.do/3/211/4178/49082/71530]("http://www.tv-links.co.uk/link.do/3/211/4178/49082/71530") but it's a divix file. Go to the page and view the source. Find the divx file, it should look something like:

[http://www1.tv-links.co.uk/link.do/3/211/4178/49082/71530/once/271d22ff3f963202424ca98985d2195b354c498/go.divx](http://www1.tv-links.co.uk/link.do/3/211/4178/49082/71530/once/271d22ff3f963202424ca98985d2195b354c498/go.divx)

Open up vlc (or any other media player) go to file, then open file, and paste in the url you took from the page source. It might give you an error about the index being broken, just ignore it.The video should start playing. 

I prefer to watch the videos from vlc sop I can control brightness and and settings via the extended GUI.

---

### Post by dmorand on 2007-07-18
I've gone through all of the steps.  When I go to stage6 it's still showing that I need to download a plugin to watch the movies.  Mplayer does open up movies from other websites, and I've validated that Mplayer can open up the divx movie if I open it from the terminal.

Any ideas?  Am I missing codecs or something?  I've looked in my plugins folder and I have those two files for the divx in there.

---

### Post by dmorand on 2007-07-18
I was messing around with MediaPlayerConnectivity and then all of a sudden I could watch divx movies on stage6, but on tv-links they just sit there trying to load.  Any suggestions?

---

### Post by dmorand on 2007-07-20
any ideas?

---

### Post by Vietman on 2007-07-27
Solution:

[http://stage6.divx.com/forum/722/3893/](http://stage6.divx.com/forum/722/3893/)

But no progress bar. Any takers?

---

### Post by Kralizec on 2007-07-27
I'm having an apparently new problem. I've downloaded and set up mplayerplug-in and DivX video plays wonderfully. Sound, however, is screwy. The regular audio is there, but a horrible screeching noise overlays it. I have the plugin configured to use ALSA. With the exception of ESD, all other sound options have no sound at all. ESD also has the horrible screeching noise. Any ideas?

---

### Post by CupofDice on 2007-08-05
Thanks Palmrya. The mozilla plugin and media player connectivity wasn't working for me. Only problem is I can't view from tvlinks.

Edit - I tried fearevilleets's way, but the two links in the source with go.divx in it didn't work. I just came across [this site]("http://feelingtea.com/decode/google/") which gives me the link to the video so I can play it in vlc or you can download it. Hope it helps.:)

---

### Post by 5h4rk on 2007-08-17
Hi, with the firefox extension, do you guy get the progress bar when the external player is lunched?

---

### Post by pmagill on 2007-08-28
bump

---

### Post by anthortic on 2007-09-03
1st post is perfect and simple. recommended technique

---

### Post by ashishgoel on 2007-09-04
i'm able to view embedded divx, but how to download the divx video??

---

### Post by pmagill on 2007-09-04
That would be a different thread altogether...

Although normally when the video is playing you have the option to right click the playing video window (provided your using the mplayer plugin) and click 'save as...' You may have to wait for the movie to download in the background (buffer) Or another way to download is to copy the url (web address) of the video ending .divx and use your favourite download manager. (Downloader for X and Gwget are both great)

And finally you can also make use of the 'unplug' firefox extension which is another easy way to download them see the unplug website for more details

Paddy_EIRE

---

### Post by ashishgoel on 2007-09-05
thanx alot man...

---

### Post by blumagic on 2008-01-13
I just had had to reply to thank you very much. I have been spending the better part of this weekend trying to get this working with stage6 videos. This has been a very good tutorial.

thanks,
blumagic

---

