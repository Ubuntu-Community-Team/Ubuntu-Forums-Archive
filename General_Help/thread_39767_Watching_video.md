---
title: "Watching video"
date: 2005-06-06
forum: General Help
---

### Post by bleakcabal on 2005-06-06
Ok, I installed Ubuntu yesterday. 

I can't watch any of my videos. When I try Totem complains about missing plugins.

When I go in options then add plugins, Totem opens a window with of a directory and that's it ( wow that was useful ),

I searched in Synaptic for totem plugins and didn't find any. 

I searched in Synaptic for mplayer but it wasn't there. So im kinda stuck right now.

---

### Post by tread on 2005-06-06
[http://ubuntuguide.org](http://ubuntuguide.org) has a lot of helpful information about adding codecs etc.

---

### Post by bleakcabal on 2005-06-06
I think my packages may not be up to date I entered the command the guide tells you to but the 3 commands brought package not found messages.

So I opened synaptic and searched for the packages without the version numbers. One was already installed and the other 2 weren't in Synaptic.

---

### Post by az on 2005-06-06
You need to enable your universe repository.

---

### Post by bleakcabal on 2005-06-06
I did not know about Universe. I enabled it and still those packages aren't there.

---

### Post by angkor on 2005-06-06
Did you do a 'sudo apt-get update' (or whatever its called in synaptic) after adding universe?

Mplayer is definately in the repos:

```
apt-cache search mplayer
mga-vid-source - Kernel driver for the back-end scaler on Matrox cards (source)
acidrip - ripping and encoding DVD tool using mplayer and mencoder
libpostproc0 - Mplayer postproc shared libraries
mencoder-586 - MPlayer's Movie Encoder
mencoder-custom - MPlayer's Movie Encoder
mencoder-k6 - MPlayer's Movie Encoder
mozilla-mplayer - MPlayer-Plugin for Mozilla, Konqueror and OpenOffice.org
mplayer-386 - The Ultimate Movie Player For Linux
mplayer-586 - The Ultimate Movie Player For Linux
mplayer-686 - transitional dummy package which can be safely removed
mplayer-custom - The Ultimate Movie Player For Linux
mplayer-doc - Documentation for mplayer
mplayer-fonts - Fonts for mplayer
mplayer-k6 - The Ultimate Movie Player For Linux
mplayer-k7 - transitional dummy package which can be safely removed
mplayer-nogui - The Ultimate Movie Player For Linux
xmms-xmmplayer - XMMS plugin that uses MPlayer to play video files
```

And so is xine. Xine should work with most formats.

---

### Post by veritas366 on 2005-06-06
This is sometimes complicated.  do a search on w32 in synaptic.  It's in the marillat repos, which is one of the ones included, I believe in the "enable all repositories" entry of the Ubuntu guide, but is not "universe".

That said, I and others could use additional info.  I got totem-xine to play streaming media with something called "mozplugger."  You can read the thread that provides these instructions [here](http://ubuntuforums.org/showthread.php?t=17727&highlight=mozplugger+xine) .

Changing the various entries on mozplugger is very confusing, and the author of the above thread simply made a copy of his.  Follow these steps and you'll have some luck, I think.  I wish I understood the details better, because I still can't get wmv files to play and I think that's because they are assigned to mplayer in the mozplugger configuration.  However, I'm afraid to mess with anything as most video works for me.  I did venture into fixing it so that evince, a pdf reader, would be my pdf reader by default, but I think I simply erased the lines about pdf and then the first time I came to one, firefox asked me which program would I like to use to open it.  Sometimes it will do this for video, but not for streaming content, which is the real problem issue.

In addition, you can look in your browser by adding the url: "about:plugins". However, this doesn't tell you what program plays each of these media types.  Or at least not directly in a way that makes sense to me.  It will tell you what kinds of media can be played (mine lists wmv files, which, as  I said, don't work for me.)  It may simply be that this is the way the about:plugins works with mozplugger handling things.  If you want to try this after you have made some changes, you have to go into your .mozilla file and erase a file called "plugin.dat" and then restart firefox.  The dot in front of mozilla (which should be in your home directory) means it is a hidden file, so you have to click on "view" and select "show hidden files" in order to access it.  

The first part of my file dealing with multimedia, with mozplugger setup, looks like this:

>     Configuration file:	/etc/mozpluggerrc
    Helper binary:	mozplugger-helper
    Controller binary:	mozplugger-controller

MIME Type 	Description 	Suffixes 	Enabled
video/mpeg 	MPEG animation 	mpeg, mpg, mpe 	Yes
video/x-mpeg 	MPEG animation 	mpeg, mpg, mpe 	Yes
video/x-mpeg2 	MPEG2 animation 	mpv2, mp2ve 	Yes
video/msvideo 	AVI animation 	avi 	Yes
video/x-msvideo 	AVI animation 	avi 	Yes
video/fli 	FLI animation 	fli, flc 	Yes
video/x-fli 	FLI animation 	fli, flc 	Yes
application/x-mplayer2 	Windows Media 	wmv,asf,mov 	Yes
video/x-ms-asf 	Windows Media 	asf,asx,wma,wax,wmv,wvx 	Yes
video/x-ms-wmv 	Windows Media 	wmv 	Yes
application/x-quicktimeplayer 	Quicktime animation 	mov 	Yes
image/x-macpaint 	Quicktime animation 	pntg,mov 	Yes 

Sorry for the poor formating, but it's just to give you an idea.

I know that in opera, you could go to a gui configuration file and simply pick what program opens what type of media content.  I'm not sure why it's so hard in Mozilla-Firefox, but I didn't like Opera.

---

### Post by jagguars on 2005-06-06
don't take that too serious, noob awnser, but why do you want to use this totem?
i had no problem watching videos wether they were avi or mpeg, even from external ntfs with kaffeine 0.6. Guess you know this and know that is installed in hoary.

tried wmv files now. that is quite curious. some files play the video, some just audio. if there is just an audio stream i get a xine message which  says 
> A problem occur while loading a library or a decoder: wmvdmod.dll

so maybe did not realy got the question but at least it works :D

---

### Post by veritas366 on 2005-06-06
I can't swear to it, but I think I tried streaming content before I put totem in.  Actually, since it was in Synaptic, I first tried mplayer, but it consistently stops at "99%" (of what...is that a cache size?) and then just sits there.  It did this in FC3 so it doesn't like something on my machine.

Also, while in FC3 I found that only totem-xine would play cd's.  No other program would...some would recognize that there was one playing, some wouldn't even do that.  

Anyway, I went with what worked.  As it stands, I don't really understand all that's going on under the hood, so when I have problems, like the wmv files, I don't have much luck sorting them out.

---

### Post by bleakcabal on 2005-06-07
[QUOTE=jagguars]don't take that too serious, noob awnser, but why do you want to use this totem?
i had no problem watching videos wether they were avi or mpeg, even from external ntfs with kaffeine 0.6. Guess you know this and know that is installed in hoary.

tried wmv files now. that is quite curious. some files play the video, some just audio. if there is just an audio stream i get a xine message which  says 


so maybe did not realy got the question but at least it works :D[/QUOTE]

Because it came with Ubuntu and I don't see either mplayer of xine in synaptic.

As for kaffeine it's missing plugins so it won't play many formats.

I have another post on the kde ubuntu forrums about kaffeine and didnt get any awnsers. 

I have never had so much trouble trying to play a video under linux.

---

### Post by veritas366 on 2005-06-07
xine is in synaptic, under "totem-xine" and mplayer is definitely there.  Make sure you have all the repos enabled as per the guide.  then search under totem-xine and mplayer.

---

### Post by semgok on 2006-04-24
Hi,
I installed w32codec and i have totem movie player but its not play mpg and mpeg formats.its shut down when I try to play mpeg,mpg files.Its only play mp3,wmv and avi files.What is wrong ? 

if you help me,i will be happy.

Thanks.

---

