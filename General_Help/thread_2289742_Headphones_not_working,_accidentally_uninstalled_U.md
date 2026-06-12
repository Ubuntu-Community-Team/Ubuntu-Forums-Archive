---
title: "Headphones not working, accidentally uninstalled Unity Control Center"
date: 2015-08-06
forum: General Help
---

### Post by benjamin34 on 2015-08-06
My headphone jack wasn't working, so I looked up some guides on how to fix it. One suggested reinstalling Alsa and PulseAudio, which I did following the instructions on this site: ([http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/](http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/)).

This included the --purge option, which uninstalled Unity Control Center (and also didn't fix the headphone problem). I tried to reinstall it via the software center and was given a connection error ("Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/unity-control-center/unity-control-center_14.04.3+14.04.20140922-0ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/unity-control-center/unity-control-center_14.04.3+14.04.20140922-0ubuntu1_amd64.deb) 404  Not Found [IP: 2001:67c:1562::13 80]").

I also tried installing it via command line and got the same error:
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/unity-control-center/unity-control-center_14.04.3+14.04.20140922-0ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/unity-control-center/unity-control-center_14.04.3+14.04.20140922-0ubuntu1_amd64.deb)  404  Not Found [IP: 2001:67c:1562::16 80]



I tried downloading the package here ([https://launchpad.net/ubuntu/+source/unity-control-center/14.04.3+14.04.20140410-0ubuntu1](https://launchpad.net/ubuntu/+source/unity-control-center/14.04.3+14.04.20140410-0ubuntu1)) and was unable to install from there, either, being told in the README to refer to the non-existent INSTALL file for instructions. I'm not an idiot, but I'm fairly new to using Ubuntu and would appreciate some help both in getting the control center back and my headphone jack working. Thank you.

---

### Post by ajgreeny on 2015-08-06
I do not use unity and Ubuntu but I think you may solve the problem you have by running command ```
sudo apt-get install ubuntu-desktop
```

---

### Post by benjamin34 on 2015-08-06
I get the same error message: E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/unity-control-center/unity-control-center_14.04.3+14.04.20140922-0ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/unity-control-center/unity-control-center_14.04.3+14.04.20140922-0ubuntu1_amd64.deb)  404  Not Found [IP: 2001:67c:1562::16 80]

---

### Post by benjamin34 on 2015-08-06
I fixed the problem with Unity Control Center by running apt-get upgrade and apt-get dist-upgrade. Still working on the headphones.

---

