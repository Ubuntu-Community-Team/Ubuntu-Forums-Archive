---
title: "Feh with arguments...."
date: 2019-01-23
forum: General Help
---

### Post by Furycd001 on 2019-01-23
HIHI. This might be a silly / stupid question, but I couldn't find anything when searching. Anyway.. Is it possible to have feh always open & scale images to fit screen ?? At the moment I can either open an images & press **"/"** to scale the image leaving an ugly area showing, or I can open via a terminal & use the arguments **"feh --scale-down --auto-zoom"**. Many thanks in advanced for replying & helping....

---

### Post by Holger_Gehrke on 2019-01-23
You might want to take a look at the man page of feh, especially the section on themes. Themes in feh are named sets of options. Create a theme with the options you want. Then create a symbolic link to feh with the name of the link the same as the name of the theme. Calling that link will run feh with that set of options. For best results the link should be in a directory that is in your PATH, I use ~/bin (which is automatically added to the PATH if it exists).

Holger

---

### Post by Furycd001 on 2019-01-23
> **Holger_Gehrke said:**
> You might want to take a look at the man page of feh, especially the section on themes. Themes in feh are named sets of options. Create a theme with the options you want. Then create a symbolic link to feh with the name of the link the same as the name of the theme. Calling that link will run feh with that set of options. For best results the link should be in a directory that is in your PATH, I use ~/bin (which is automatically added to the PATH if it exists).

Holger

Thanks for the info. Going to take a look at the man page now....

---

### Post by Furycd001 on 2019-01-23
I just read the themes section of the man page and don't fully understand what I'm meant to do. Sorry for being stupid.. I created /home/jonny/.config/feh/themes/ & then inside that folder created a file with nano called autoscale. Inside the file I put feh --scale-down --auto-zoom & then saved the file. I'm not sure if that was right or not & I'm really not sure how to use the ln command now....

---

### Post by Holger_Gehrke on 2019-01-23
Create a **file** named themes in /home/jonny/.config/feh/. Put this in it:
```

autoscale --scale-down --auto-zoom

```
To test it, run
```

feh -Tautoscale Pictures/*

```
create a link to feh named autoscale in ~/bin
```

ln -s $(which feh) ~/bin/autoscale

```
Now when you run 'autoscale Pictures/*' feh will be executed and load that theme.

A theme I've been using for a while:
```

slides --fullscreen --auto-zoom --recursive --scale-down --slideshow-delay 5

```
(fullscreen slideshow of all images in a directory and its subdirectories, Pictures change every 5 seconds)

Holger

---

### Post by Furycd001 on 2019-01-23
> **Holger_Gehrke said:**
> Create a **file** named themes in /home/jonny/.config/feh/. Put this in it:
```

autoscale --scale-down --auto-zoom

```
To test it, run
```

feh -Tautoscale Pictures/*

```
create a link to feh named autoscale in ~/bin
```

ln -s $(which feh) ~/bin/autoscale

```
Now when you run 'autoscale Pictures/*' feh will be executed and load that theme.

A theme I've been using for a while:
```

slides --fullscreen --auto-zoom --recursive --scale-down --slideshow-delay 5

```
(fullscreen slideshow of all images in a directory and its subdirectories, Pictures change every 5 seconds)

Holger

Thank you so very much for the detailed explanation. I managed to understand everything that you said & got it working.

---

