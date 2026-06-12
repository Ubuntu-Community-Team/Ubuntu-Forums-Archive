---
title: "File and folder's color in shell"
date: 2008-06-27
forum: General Help
---

### Post by rtsask on 2008-06-27
Hi, how can I see my file and directories in shell to be shown in different color based on their permission for example some in green and some in blue and .....

Thanks

---

### Post by x1a4 on 2008-06-27
Hi,

Make sure you have the following in your ~/.bashrc file
```

# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
    eval "`dircolors -b`"
    alias ls='ls -bF --color=always'
fi

```

And add the file [.dir_colors]("http://hex1a4.net/xubuntu/dotfiles/dir_colors/") to your home directory--this is where the colours are defined.  You can also set the LS_COLORS environment variable to set ls colours.  This is mine: 

```
LS_COLORS  'pi=40;33:bd=40;33;01:cd=40;33;01:or=01;05;37;41:mi=01;05;37;41:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.xbm=01;35:*.xpm=01;35:*.png=01;35:*.mng=01;35:*.tif=01;35:*.tiff=01;35:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tz=01;31:*.rpm=01;31:*.deb=01;31:*.cpio=01;31:*.7z=01;31:*.svg=01;35:*.xcf=01;35'
```

---

### Post by p_quarles on 2008-06-27
Moved to General Help.

---

