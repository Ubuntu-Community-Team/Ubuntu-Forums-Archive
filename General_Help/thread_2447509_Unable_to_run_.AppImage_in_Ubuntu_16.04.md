---
title: "Unable to run .AppImage in Ubuntu 16.04"
date: 2020-07-20
forum: General Help
---

### Post by tarutarak on 2020-07-20
Hello,


We need to run  a software through .AppImage file. For this we have set permission as execute (see [https://prnt.sc/ti8hrh](https://prnt.sc/ti8hrh)).


Then we are trying to run by double clicking the we are getting an error "cannot mount appimage check fuse setup". See [https://prnt.sc/ti8lyf](https://prnt.sc/ti8lyf)

We have looked up the [wiki article suggested]("https://github.com/AppImage/AppImageKit/wiki/FUSE") in the error message and same issue after executed following commands:


> sudo apt install fuse
sudo modprobe fuse
sudo groupadd fuse


user="$(whoami)"
sudo usermod -a -G fuse $user



Any suggestions would be appreciated.


Thanks in advance.

---

### Post by TheFu on 2020-07-20
Did you try the appimage-extract method?

---

### Post by tarutarak on 2020-07-20
Yes, its showing same error with this method also.

Please help

---

### Post by monkeybrain20122 on 2020-07-20
Is it just that one or do you have other appimages? I just tested it and it works on Ubuntu 16.04 (though it puts a file in my .config and .config/autostart which I had to delete after deleting the workcomposer appimage)

---

### Post by TheFu on 2020-07-20
I've had a few issues with AppImages refusing to run. They were:
[LIST]
[*]No support for remote X11. That may have been an X11 ssh forward issue, but xterms always worked and still work between those systems.
[*]Attempted to use a symlink from ~/bin/ to the /usr/local/vidcutter-appimage/VidCutter-6.0.0-x64.AppImage location. That failed, probably because the symlink breaks many shell scripts in a way they can't figure out what the actual directory is for themselves. To get around the symlink, I just made a tiny script 
```
#!/bin/bash
/usr/local/vidcutter-appimage/VidCutter-6.0.0-x64.AppImage $@

``` which works.
[/LIST]

The best way to troubleshoot these things is to open a terminal and run the program. Then all errors will be displayed on the terminal and you can web-search those exact errors AND post them here, without an image.  The hard part is that often the GUI libraries also throw a bunch of useless messages out and figuring out what is useful isn't easy.

---

### Post by tarutarak on 2020-07-20
Thank you for your response.

We can download said AppImage file again. Should we download again and try to run again?

Or should we have to delete "[COLOR=#000000] my .config and .config/autostart[/COLOR]" before run AppImage? If yes then how we can remove them from .AppImage file?

It will be great help if you please let us know the steps.

---

### Post by monkeybrain20122 on 2020-07-20
Ok, try the following. Create a new folder, call it test, for example (just to have a neat work folder instead of spilling things in your $HOME) , put the appimage in test

Run he following command in the terminal. It will extract the appimage to a folder called squashfs-root in test
```

cd test


./workcomposer-linux-installer.AppImage --appimage-extract 


```

Now in the same terminal instance
```

cd squashfs-root

```

Now run the app. In the same terminal instance, type

```
./Apprun
```

If it doesn't work it should output error messages to your terminal, post them here.

---

### Post by tarutarak on 2020-07-21
Thank you so much for the suggestion.

We have followed what you said. Now we are getting below:

> Failed to register AppImage in AppImageLauncherFS: could not open map file

---

### Post by monkeybrain20122 on 2020-07-21
Sorry, there was a typo, should be 

./AppRun

with capital R

---

### Post by tarutarak on 2020-07-24
Hello monkeybrain20122,

Thank you for the response and sorry for the delay from our end.

Now this software is showing under **Application**. But when we are trying to open this software then we are getting error.

Please refer to the screenshot via the link [https://prnt.sc/tnumqm](https://prnt.sc/tnumqm)

---

### Post by monkeybrain20122 on 2020-07-24
Can you extract the appimage?  Did you install something call appimagelauncher from a ppa? If so you should uninstall it.

---

