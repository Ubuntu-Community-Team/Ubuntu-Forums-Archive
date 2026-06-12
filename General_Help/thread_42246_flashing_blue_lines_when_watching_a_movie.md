---
title: "flashing blue lines when watching a movie"
date: 2005-06-16
forum: General Help
---

### Post by flamarro on 2005-06-16
Hi,
I've got a ATI and i manage do use the new drivers althoug i get 3200 in glxgears.
I have installed using unofficial ubuntu guide all the codecs. I have mplayer, totem xine and vlc to watch the movies, but all of them show some blue lines flashing in the bottom of the screen, no matter what is the player i use.
Does anyone see this too?? I tried to capture a frame to show you, but, funny or not, the image i capture dosen't have the lines, even when i am in a pause and see the lines, when i capture the frame, they disapper.

---

### Post by intangible on 2005-06-17
[QUOTE=flamarro]Hi,
I've got a ATI and i manage do use the new drivers althoug i get 3200 in glxgears.
I have installed using unofficial ubuntu guide all the codecs. I have mplayer, totem xine and vlc to watch the movies, but all of them show some blue lines flashing in the bottom of the screen, no matter what is the player i use.
Does anyone see this too?? I tried to capture a frame to show you, but, funny or not, the image i capture dosen't have the lines, even when i am in a pause and see the lines, when i capture the frame, they disapper.[/QUOTE]
 Try this:

**System->Preferences->Multimedia Systems Selector** Select the **Video** tab and try changing the **Default Sink**.  Try different settings there, restarting totem between each change and see if that makes a difference.  If it does, then look into the more advanced settings for the other programs you have and find the Sink they use and change it to match the one you chose for totem.

SDL does what you describe on my system, but XWindows Xv works fine.

---

### Post by flamarro on 2005-06-19
thanks intangible for your reply.
the problem persists, but i'm a newbie, so it must be me who the problem is  :smile: 
I've done the changes that you said in totem the lines just appears sometimes now, in the other applications stays the some.
I forget to say that, i have avidemux too, and as it gaves me an error of codecs, i installed xvid codec, as wmv has no sound i've done as our forum said, changed the priority to 7. Do you think this has something to do with my problem

Once again, sorry about y english...

---

### Post by intangible on 2005-06-20
Sorry, not sure what else for you to try... you could try reinstalling the codec packages: **sudo apt-get --reinstall install w32codecs**  If that doesn't help... sorry, I'm out of ideas? :confused:  Hopefully someone else can help you out with this problem.

---

### Post by flamarro on 2005-06-21
I have a ATI Radeon with tv out, and could it be that becouse of when ubuntu start i always have tv out activated and in clone mode??
I cant change this part becouse it says that i must start Xserve to changes take ffect. First, i dont know how do i do this, maybe ctrl+alt+backspace?????
When i do  it it stays the some, tv out on, and clone mode.....

---

### Post by intangible on 2005-06-21
Perhaps, I think it will automatically disable the TV out if you unplug the TV cord from the card and log out then back in... But I don't know for sure, I have a nvidia card.

The renderaccel option is for nvidia cards, so you don't need that.

Try doing this and see if it helps: [http://www.ubuntuforums.org/showthread.php?t=24557](http://www.ubuntuforums.org/showthread.php?t=24557)

---

### Post by flamarro on 2005-06-22
maybe this is a very stupid thing that i'm going to say....
Tryed a few divx, but the lines are only showed in the films that has AC3, the others with mp3, mp2 i don't see the lines.
Could it be it?   :?

---

### Post by intangible on 2005-06-22
It's possible, have you tried watching the same files on another computer, one with windows and another with ubuntu?

---

