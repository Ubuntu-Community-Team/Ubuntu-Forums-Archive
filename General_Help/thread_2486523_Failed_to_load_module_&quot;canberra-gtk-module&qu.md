---
title: "Failed to load module &quot;canberra-gtk-module&quot;"
date: 2023-05-03
forum: General Help
---

### Post by lovenguyen on 2023-05-03
When I run the file filename.AppImage on the terminal, I get the following error:
Failed to load module "canberra-gtk-module"
appDataDir: /home/loveng/.config/filename
userData: /home/loveng/.config/&#21518;&#32703;&#37319;&#38598;&#22120;
userData does not exist, do nothing
ENOENT: no such file or directory, scandir '/home/loveng/.config/filename'
Segmentation fault (core dumped)
So how can I fix the above error?

---

### Post by zebra2 on 2023-05-03
sudo apt install libcanberra-gtk3-module

---

### Post by lovenguyen on 2023-05-03
It still shows the old error after I run this command line.

---

### Post by monkeybrain20122 on 2023-05-03
You need libcanberra-gtk-module instead of libcanberra-gtk3-module.

---

### Post by lovenguyen on 2023-05-04
After i run sudo apt install libcanberra-gtk-module and ./filename.AppImage , I get the following error:
appDataDir: /home/loveng/.config/filename
userData: /home/loveng/.config/&#21518;&#32703;&#37319;&#38598;&#22120;
userData not exist, do nothing
Segmentation fault (core dumped)

---

### Post by idmbe on 2023-05-04
try this
```
 sudo apt install libcanberra-gtk-module libcanberra-gtk3-module
```

After that if you still see this msg:
[COLOR=#ff0000]Segmentation fault (core dumped)[/COLOR]         

Then follow this like:
[https://www.javatpoint.com/segmentation-fault-core-dumped-ubuntu](https://www.javatpoint.com/segmentation-fault-core-dumped-ubuntu)

---

### Post by Holger_Gehrke on 2023-05-04
libcanberra is probably completely unimportant in this case. It's a library that enables programs to make the system play system sounds at specific events. By using libcanberra all programs produce the same sound for the same event - all errors in all programs using canberra make the same sound, the completion of a long running background task sounds the same for all programs and so on. libcanberra is normally completely optional, I've never seen a program that wouldn't run without it.

Without knowing what the program is we can only guess what's going wrong. My guess is that either it's looking for a configuration in ~/.config/filename, not finding one and assuming some defaults that don't work on your system and crashes or the appimage just can't work on your system because it doesn't include a library it needs and uses one your system provides that's different from what the program expects. I'd take a long hard look at the documentation of the program.

Holger

---

### Post by ActionParsnip on 2023-05-04
I'd also maybe run
```

touch /home/loveng/.config/filename

```

---

### Post by lovenguyen on 2023-05-06
I ran this command and nothing happened, it didn't show any information

---

### Post by lovenguyen on 2023-05-06
I followed the link:[https://www.javatpoint.com/segmentation-fault-core-dumped-ubuntu](https://www.javatpoint.com/segmentation-fault-core-dumped-ubuntu)
BUT:
When I enter the code sudo dpkg -1 | grep ^..r | apt-get purge shows the following error
dpkg: error: unknown option -1

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use 'apt' or 'aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through 'less' or 'more' !
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

So what should I do?

---

### Post by oldos2er on 2023-05-08
> When I enter the code sudo dpkg -1

That should be a letter l (ell), not a numeral 1.

---

### Post by lovenguyen on 2023-05-10
I follow you no more "unknown option -1" error but when I run command ./filename.AppImage the old error comes up again:
appDataDir: /home/loveng/.config/filename
userData: /home/loveng/.config/&#21518;&#32703;&#37319;&#38598;&#22120;
userData not exist, do nothing
Segmentation fault (core dumped)
---
For this fix from the paragraph: "A great way which always will work is as follows apart from the command line" (at the link [https://www.javatpoint.com/segmentation-fault-core-dumped-ubuntu](https://www.javatpoint.com/segmentation-fault-core-dumped-ubuntu)) 
I don't understand how to do in this paragraph: "Now, we have two ways to resolve segmentation fault GUI and CLI. Sometimes, it might also happen that the command, i.e., apt is not working due to the segfault, so the CLI method will not implement. In that situation, do not worry because the GUI method will always work for us." 
What should I do now?

---

### Post by idmbe on 2023-05-12
Pass to next steps as show in link.

after finish all steps in the link and still not work, type this:
```
 sudo apt search libcanberra
```

and see the results and make sure all those modules below already installed in your system:
[COLOR=#008000]gnome-session-canberra
libcanberra-gtk-module
libcanberra-gtk0
libcanberra-gtk3-0
libcanberra-gtk3-module
libcanberra-pulse
libcanberra0
libgsound0

[/COLOR]Or share the results here with us[COLOR=#008000]
[/COLOR]

---

### Post by lovenguyen on 2023-05-14
after finish all steps in the link ([https://www.javatpoint.com/segmentation-fault-core-dumped-ubuntu](https://www.javatpoint.com/segmentation-fault-core-dumped-ubuntu)) and still not work, type this:
 	Code:
 	 sudo apt search libcanberra 
and I get results like 3 attached pictures.
---
So how to fix the above error because I see everything is already installed.

---

