---
title: "Change the colors of symbolic linked directories?"
date: 2013-04-21
forum: General Help
---

### Post by altjx on 2013-04-21
I currently have a backup script that backs everything up to my /mnt/hgfs directory simply because using symbolic links for directories within my mnt/hgfs shows completely disgusting (like bright green background for directories, etc). 

However, if I change these colors in the gnome terminal settings, it also affect other things like my python script colors, etc. Anyone has a better solution to this?

---

### Post by Impavidus on 2013-04-21
You can change the colours used by ls.

From **man ls**:```

       Using color to distinguish file types is disabled both by  default  and
       with  --color=never.  With --color=auto, ls emits color codes only when
       standard output is connected to a terminal.  The LS_COLORS  environment
       variable can change the settings.  Use the dircolors command to set it.

```
Read the manual page for dircolors and dig a bit further. I have looked into this, but never actually tried it.

---

### Post by altjx on 2013-04-21
> **Impavidus said:**
> You can change the colours used by ls.

From **man ls**:```

       Using color to distinguish file types is disabled both by  default  and
       with  --color=never.  With --color=auto, ls emits color codes only when
       standard output is connected to a terminal.  The LS_COLORS  environment
       variable can change the settings.  Use the dircolors command to set it.

```
Read the manual page for dircolors and dig a bit further. I have looked into this, but never actually tried it.

Thanks man, I was able to get this fixed upon looking at this manual page as well as other online resources. For those who would also like to change the ugly symbolic link's subdirectory colors, I just added this line to the end of my .bashrc file:

```
export LS_COLORS='rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:ca=30;41:tw=30;42:[COLOR=#ff0000]**ow=01;34**[/COLOR]:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.lz=01;31:*.xz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.war=01;31:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.axv=01;35:*.anx=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.axa=00;36:*.oga=00;36:*.spx=00;36:*.xspf=00;36:'
```

The bold text in the text above is the actual numbers I had to change. The original numbers were 34;42, which meant green background with blue font color, which equals ugliness. In the above text, 01 means bold, and 34 means blue text. Thus, the background color is going to be determined by your regular terminal settings.

---

### Post by altjx on 2013-04-21
Um, this thread is solved, but I have no idea how to mark it. Nothing under thread tools...

---

### Post by Toz on 2013-04-21
The Mark as Solved plugin doesn't work yet with VB4 so you have to use the long method. Click "Edit Post" on your _original post_ in this thread, then click on the "Advanced" button and then changed the Prefix to [Solved].

---

### Post by altjx on 2013-04-21
Thanks. Marked as Solved.

---

