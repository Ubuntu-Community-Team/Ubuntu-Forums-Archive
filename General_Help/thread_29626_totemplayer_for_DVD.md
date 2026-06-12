---
title: "totemplayer for DVD"
date: 2005-04-25
forum: General Help
---

### Post by maltje on 2005-04-25
I did :sudo apt-get install libdvdcss2
but DVD won't play with totemplayer.
How come?

---

### Post by codejunkie on 2005-04-25
[QUOTE=maltje]I did :sudo apt-get install libdvdcss2
but DVD won't play with totemplayer.
How come?[/QUOTE]

use sudo apt-get install totem-xine this worked for me the version of totem installed by default dosen't seem to do much.
i also had to install w32codecs and gstreamer0.8-mad hope this helps.

---

### Post by maltje on 2005-04-25
Won't work for me
 ](*,)

---

### Post by codejunkie on 2005-04-26
don't know if this helps but it's got lots of info on how to install DVD playback on ubuntu [http://www.ubuntulinux.org/wiki/RestrictedFormats](http://www.ubuntulinux.org/wiki/RestrictedFormats)

---

### Post by DutchLau on 2005-04-26
Scrap Totem man. Get VLC or Mplayer. As codejunkie said, the default version of Totem doesn't do very much, and even though you might have all the codecs installed, Totem still might not play the DVD/Movie. 

Take a look here at how to install Mplayer:

[http://ubuntuguide.org/#mplayer](http://ubuntuguide.org/#mplayer)

Cheers,

---

### Post by laue on 2005-04-27
I recommend using gxine, a gtk frontend to xine, which has a gui comparable to totem. It really integrates into the gnome desktop seamlessly. All video formats work with it, including dvd!

---

### Post by maltje on 2005-04-28
ok, I installed gxine and it plays well.
But how can I put it in my menu?
I can only start it from the commando window.
How can I get it to open automaticly when I click on a media file?
Now I only have the mossibility to save the file or open it with totem.

---

### Post by laue on 2005-04-28
> **maltje]ok, I installed gxine and it plays well.
But how can I put it in my menu?
I can only start it from the commando window.
[/QUOTE]

edit file /usr/share/applications/gxine.desktop
example:
```

[Desktop Entry]
Encoding=UTF-8
Type=Application
Name=gxine
Comment=A free video player
Exec=gxine
Icon=gxine-logo.png
Terminal=false
Categories=Application said:**
> 
How can I get it to open automaticly when I click on a media file?
Now I only have the mossibility to save the file or open it with totem.

rightclick on the media file, select properties and open the 'open with' tab. Add gxine and make it the default application (select the gxine radiobutton)

---

### Post by DutchLau on 2005-04-28
Hi Maltje, 

You get Gxine on the Applications list like this:

First, get Gnome Menu Editor like this: [http://ubuntuguide.org/#menu-editor](http://ubuntuguide.org/#menu-editor) (Follow ALL the steps)

Now go to Applications => System Tools => Menu Editor 

Make a new entry. Name = "Gxine" or something. Command = /usr/bin/gxine (For me it's this anyways)

Category: Sound & Video Now Save, Open up a terminal, and type in: killall gnome-panel

Applications => Sound & Video => Gxine 

Good Luck! 

Let us know if it worked,

Cheers, DutchLau

---

### Post by maltje on 2005-04-29
At this moment it won'twork %
I can't get it in my list "sound and video"
I got it in "aplication" "others"
When I do "new entry" nothing happens
I go with the cursor on "sound and video" and then I go to the right and fill the new program.So,Program is now in the list but not in video and sound.
Ask here also.
I deleted totemplayer,because I work now with the gxine.
When I got mail with a movie *.wmv I only can save the file.I do this and I double click on it.
I got an error and I have to save the file as an *asf file.If I do this then it works fine with gxine.
How can I get to play automaticly the fiel when I click on it in my mail?
Same with mpg files,I only can save them first and then play.

---

### Post by maltje on 2005-04-29
[QUOTE=laue]edit file /usr/share/applications/gxine.desktop
example:
```

[Desktop Entry]
Encoding=UTF-8
Type=Application
Name=gxine
Comment=A free video player
Exec=gxine
Icon=gxine-logo.png
Terminal=false
Categories=Application;AudioVideo

```



rightclick on the media file, select properties and open the 'open with' tab. Add gxine and make it the default application (select the gxine radiobutton)[/QUOTE]
 This solution works for me.
I missed this post at first.

---

### Post by DutchLau on 2005-04-29
Both are basically the same thing Maltje. 

My way was a little bit more "graphical" but they both should work. If you want to see streaming video you *have* to install Mplayer and the Mplayer plugin for Mozilla. You could also install VLC, but that plugin doesn't work for me :-|  Here's how to install Mplayer and the Mplayer plugin. It doesn't take up that much space. Also, if you want to change the default "openwith" rightclick on a file, properties, and then open with.

Here's the link: [http://ubuntuguide.org/#mplayer](http://ubuntuguide.org/#mplayer)

Good luck, 

Let us know if it worked. 

DutchLau

---

### Post by laue on 2005-04-29
[QUOTE=DutchLau]If you want to see streaming video you *have* to install Mplayer and the Mplayer plugin for Mozilla.[/QUOTE]

Please do not force people into using your favourite player. (I myself don't really care for mplayer that much) Gxine works great for playing streaming video for me. I do not have the time to post a howto right now, but i will try and look into it this weekend.

[QUOTE=DutchLau]My way was a little bit more "graphical" but they both should work.[/QUOTE]

Indeed, it _should_ have the same results. However, the gnome menu editor application does not seem to do what it should do with everyone. Respect for the developers of course, but using a commandline texteditor still seems to be the way to go :)

---

### Post by maltje on 2005-04-29
Mplayer won't work.
I open a file but then nothing happens and Mplayer freezes.
At first (new installation) I had the possibility (with evolution)To save afile or to play the file with totemplayer.
Because gxine works better I deleted totemplayer from my system.But now when I open a mail with a moviefile or mp3 I only have the possibility to save the file not to play it automaticly.

---

### Post by laue on 2005-04-29
Patience is a virtue :)

---

### Post by DutchLau on 2005-04-29
[QUOTE=laue]Please do not force people into using your favourite player. (I myself don't really care for mplayer that much) [/QUOTE]

Laue, as far as I know, there isn't a Gxine plugin for Mozilla Firefox. I myself use Gxine also, but unfortunately I have to use the Mozilla-Mplayer for streaming video on websites. That's what I meant. I didn't mean that he *has* to use Mplayer (I myself don't like it as much as Gxine  :razz:  )

Sorry about the confusion,

DutchLau

---

### Post by laue on 2005-05-02
a (very limited) how-to for using the gxine plugin in firefox can be found on [http://plugindoc.mozdev.org/](http://plugindoc.mozdev.org/)

I currently have it working in ubuntu. I copied it from my gentoo partition, where i had compiled gxine from source.

---

### Post by dewey on 2005-05-02
xine-ui has never failed me for DVD playback.
[http://ubuntuguide.org/#xine-ui](http://ubuntuguide.org/#xine-ui)

---

### Post by laue on 2005-05-03
[QUOTE=dewey]xine-ui has never failed me for DVD playback.
[http://ubuntuguide.org/#xine-ui](http://ubuntuguide.org/#xine-ui)[/QUOTE]

indeed, but i believe gxine integrates better into the gnome desktop

---

