---
title: "Installed MPlayer, how to make it default (and other questions)"
date: 2005-07-19
forum: General Help
---

### Post by DerMika on 2005-07-19
I installed MPlayer on my Ubuntu box. But would like it if I double-clicked a video file, it would automatically start in MPlayer (same for DVD video's if that's possible). Now they seem to start in Totem. 

Also, when MPlayer is already running and I doubleclick another video file, i'd like the file to load in the running MPlayer, now it opens a second MPlayer. 

Can all of this be done? ;)

---

### Post by NeoChaosX on 2005-07-19
First problem can be fixed by right-clicking on the file, going to the "Open With" tab, and selecting MPlayer from there. If it's not listed, hit the Add button and add it to the list of programs.

Can't help you on the second problem, there doesn't seem to be an option for it in MPlayer, either in the GUI preferences or the command line options. Sorry.

---

### Post by DerMika on 2005-07-20
[QUOTE=NeoChaosX]First problem can be fixed by right-clicking on the file, going to the "Open With" tab, and selecting MPlayer from there. If it's not listed, hit the Add button and add it to the list of programs.

Can't help you on the second problem, there doesn't seem to be an option for it in MPlayer, either in the GUI preferences or the command line options. Sorry.[/QUOTE]
 Yes ik know i can use "open with", but then I have to do this with every single file. Is there no way to set MPlayer as "default videoplayer"?

---

### Post by emoui on 2005-07-20
DerMika

concerning your first question, you can right-click on a file you want to view, open "Properties" window and go to tab "Open With" and specify application you want to use. This might not be the most comfortable way, because you need to repeat the same procedure for files with different extensions that you want to open with mplayer. However, I don't know any other way.

Don't know the answer on your second question.

emoui

---

### Post by DerMika on 2005-07-20
[QUOTE=emoui]DerMika

concerning your first question, you can right-click on a file you want to view, open "Properties" window and go to tab "Open With" and specify application you want to use. This might not be the most comfortable way, because you need to repeat the same procedure for files with different extensions that you want to open with mplayer. However, I don't know any other way.

Don't know the answer on your second question.

emoui[/QUOTE]
 It doesn't seem to work. 

I did what you said, i selected Mplayer to open .mpg files, i close the file again, i open another .mpg file and it opens in Totem again... Can I be doing something wrong? I get the same with trying to open .jpg's in Gwenview.

---

### Post by jiyuu0 on 2005-07-20
your answer to your first question...

```

gconftool-2 --type string --set /desktop/gnome/volume_manager/autoplay_dvd_command "gmplayer dvd://"

sudo cp /usr/share/applications/defaults.list /usr/share/applications/defaults.list_backup

sudo sed -e 's/totem.desktop/mplayer.desktop/g' /usr/share/applications/defaults.list_backup > /tmp/defaults.list

sudo mv /tmp/defaults.list /usr/share/applications/defaults.list

```

---

### Post by emoui on 2005-07-20
[QUOTE=DerMika]It doesn't seem to work. 

I did what you said, i selected Mplayer to open .mpg files, i close the file again, i open another .mpg file and it opens in Totem again... Can I be doing something wrong? I get the same with trying to open .jpg's in Gwenview.[/QUOTE]

Strange... It should work. Are you sure that you selectedmplayer in the "Open With"? 
If so I apologise for doubts, but the above procedure works for me without any problems. The only thing that come to my mind is to see whether these two files are of the same type (use file command in terminal). Despite the same extension, they can be of a different type. What about the first file if you double-click it?

emoui

---

### Post by DerMika on 2005-07-20
[QUOTE=jiyuu0]your answer to your first question...

```

gconftool-2 --type string --set /desktop/gnome/volume_manager/autoplay_dvd_command "gmplayer dvd://"

sudo cp /usr/share/applications/defaults.list /usr/share/applications/defaults.list_backup

sudo sed -e 's/totem.desktop/mplayer.desktop/g' /usr/share/applications/defaults.list_backup > /tmp/defaults.list

sudo mv /tmp/defaults.list /usr/share/applications/defaults.list

```[/QUOTE]
 OK i did all those commands, do i have to restart something now before this comes in effect, because it's still f*ing totem ;)

---

### Post by jiyuu0 on 2005-07-20
oh, forgot this,

killall nautilus

---

### Post by NeoChaosX on 2005-07-20
Er, whoops. I meant in my original properties to right click on the file, go to **Properties**, and then select the Open With tab. Absentmindedness, I guess.

---

### Post by DerMika on 2005-07-20
[QUOTE=jiyuu0]oh, forgot this,

killall nautilus[/QUOTE]
 OK this works now!!! Great!

Thanks a lot guys :)


And now i'll try pushing my luck... Does anyone know the second question?
> Also, when MPlayer is already running and I doubleclick another video file, i'd like the file to load in the running MPlayer, now it opens a second MPlayer.

or should i just  :-# and be happy with what i've got now? ;)

---

