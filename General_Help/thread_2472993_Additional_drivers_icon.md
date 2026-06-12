---
title: "Additional drivers icon"
date: 2022-03-20
forum: General Help
---

### Post by cam17 on 2022-03-20
A icon called "additional drivers" shows in my show applications button. I did not install this application and when I go to "Ubuntu store" it shows the option to install that application meaning it is not installed on my on my Ubuntu 20.04 04 LTS. If i click on the icon it reports "Software & Updates Software & Updates are ready"

What is this app should it be removed?

---

### Post by MAFoElffen on 2022-03-20
No. Is a part of Ubuntu-Desktop... Actually... Previous to version 20.04, it used to be it's own program. Since, it is a part of the "Software & Updates" application as a Tab in that App.

What it is, is something that looks at your hardware and determines if there is anything there that would benefit from a third party hardware driver, should as a video driver for a video card, such as from NVidia, if you had and NVidia Graphics card, or a wireless card driver... And gives you a chance to install that if you desire to. 

Since it also it wrapped up in another application now, that helps with your software sources and such, (and has some other things tied into it under that covers) you just can't delete or uninstall it without causing other havoc, if you do not know what you are doing.

It is safe and should be left alone.

---

### Post by deadflowr on 2022-03-20
> What is this app should it be removed?
It's part of the software-properties-gtk package,
and no it should not be removed.
You can try hiding it though
Try
```
cp /usr/share/applications/software-properties-drivers.desktop ~/.local/share/applications/
echo 'NoDisplay=true' | tee -a ~/.local/share/applications/software-properties-drivers.desktop
```
This moves a copy of the launcher's desktop file into your home folder.
The reason for doing this is this will keep the changes regardless of whether or not the package gets updates at some point.
(An update would overwrite the changes of the file in the /usr directory, but will not change the file in your home folder)

And the second line commands will append the file with the NoDisplay setting, making it always hidden from you and your desktop.

---

