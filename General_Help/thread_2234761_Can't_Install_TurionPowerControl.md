---
title: "Can't Install TurionPowerControl"
date: 2014-07-16
forum: General Help
---

### Post by junior4 on 2014-07-16
Hello, I need help installing TurionPowerControl (overclock/undervolt tool). I've downloaded the tool from here [https://code.google.com/p/turionpowercontrol/](https://code.google.com/p/turionpowercontrol/) as a tar.gz file. I've followed the instructions on how to install tar.gz files, but I still get errors, claiming "No such file or directory"

---

### Post by oldos2er on 2014-07-16
Moved to General Help.

I can see a couple problems with the [wiki installation instructions]("https://code.google.com/p/turionpowercontrol/wiki/CompilationAndInstallation"), at least as far as Ubuntu is concerned. First you'll need to install the build-essential package ```
sudo apt-get update && sudo apt-get install build-essential
``` If you've already extracted the tar.gz, we'll need to "cd" into the folder it created, so something like ```
cd Downloads/Folder/
``` I don't know the name of the "Folder" so you'll need to provide that info. 

Once you're in the right folder, run ```
make
``` If make completes successfully you'd run ```
sudo make install
```

---

