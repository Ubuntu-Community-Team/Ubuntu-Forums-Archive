---
title: "Three Questions About .desktop Files And The Launcher"
date: 2017-06-28
forum: General Help
---

### Post by SBTlauien on 2017-06-28
0. I have a program that runs using Mono([http://www.mono-project.com/](http://www.mono-project.com/)) and when I click on my launcher to open the program, it creates an additional icon on the launcher for the running program.  I would like this program to not open an additional icon and instead just use the icon that is already on the launcher(like all launcher programs do).  Below is the .desktop file.

```


[Desktop Entry]
Name=RH
Exec=/usr/bin/mono /home/sbt/.RH/RH.exe -home /home/sbt/.RH
Type=Application
StartupNotify=true
Path=/home/sbt/.RH
Icon=/home/sbt/.RH/rh.png
MimeType=application/sla;text/gcode;application/wavefront-obj;application/x-amf;


```

1. Is it possible to request a password for root privileges by clicking the icon on the launcher, for a terminal application?  For instance, if I add GParted to my launcher and then click on it, a password prompt will pop up asking me for my password.  Can I do this with a terminal app using a .desktop file and if so, how?

2. When I click on the TOR icon on my launcher to run the TOR browser bundle, it appears on the launcher as if it opened another instance of FireFox(which it technically has) but I'd like it to stay contained to the actual TOR icon rather than my FireFox icon.  How can I do this?

Thanks in advance.

---

### Post by monkeybrain20122 on 2017-06-28
To get rid of the duplicate icons, you may want to add a line for StartupWMClass to your .desktop file [https://askubuntu.com/questions/367396/what-represent-the-startupwmclass-field-of-a-desktop-file](https://askubuntu.com/questions/367396/what-represent-the-startupwmclass-field-of-a-desktop-file)

For displaying a text box to ask for password. Here is one way. First write a script to ask for password, let's call it askpswd.sh
```
#!/bin/bash
zenity --password --title=Authentication

```

Store the file somewhere, say in a Scripts folder in your home and make it executable (chmod +x /path/to/script or right click > Properties > allow to execute)
now you can write another script which 1) invokes askpswd.sh 2) then executes a  sudo command
Something like
```
#!/bin/bash

export SUDO_ASKPASS="/path/to/askpswd.sh"

sudo launch/your/application


```


Again make it executable, let's give it a  name, say "my-app-as-root", again store it somewhere, say, in $HOME/bin (bin does not exist, create it)

Then you can write a desktop file with Exec=my-app-as-root (if you put my-app-as-root in $HOME/bin you don't need to specify the full path since $HOME/bin is in your path, you can check ~/.profile)

There are other ways to do it, but this is simple and you can reuse askpswd.sh for many different applications.

---

### Post by igdfpm on 2017-06-28
Don't know about your duplicate icon problems - sorry, but displaying a gui password box for a sudo app is pretty trivial...

You will need to create an additional script and point the existing .desktop file to launcher that instead of the original binary. See example below.

```


cat /usr/bin/uefitow10_starter 

#
# /usr/bin/uefitow10_starter provides as gui sudo password box
# via pkexec for terminal app /usr/sbin/uefitow10 (which is also a script - but it could be any terminal app that requires sudo privileges)

#!/bin/bash
if [ $(which pkexec) ]; then
	pkexec --disable-internal-agent "/usr/sbin/uefitow10"
fi


cat /usr/share/applications/uefirebootw10.desktop 

#
# Standard .desktop file that fires uefitow10_starter 
#

[Desktop Entry]
Encoding=UTF-8
Terminal=false
Type=Application
StartupNotify=false
Version=0.1
Type=Application
Name=UEFI reboot to W10
TryExec=/usr/bin/uefitow10_starter
Exec=/usr/bin/uefitow10_starter
Icon=windows
GenericName=Reboot to W10
Categories=Utility;System;Windows;Accessories;
GenericName=Reboot to W10 via UEFI


```

---

### Post by SBTlauien on 2017-06-28
Alright, the last two issues have been resolved but I'm having trouble with the first one.

If I run "xprop WM_CLASS" and click on the window of the application I get "WM_CLASS:  not found."

So I try to add it by running "xprop -f WM_CLASS 8s -set WM_CLASS "RH"" and clicking on the window.  This seems to work.

I then check it by again running "xprop WM_CLASS" and click on the window of the application, and now I get "WM_CLASS(STRING) = "RH"".

But when I run "xprop -name "RH" -f WM_CLASS 8s -set WM_CLASS "RH"" I get "xprop: error: No window with name RH exists!".

So it seems as if I'm not doing something correctly...

---

### Post by monkeybrain20122 on 2017-06-28
Maybe the last line of this post would help?

[https://bbs.archlinux.org/viewtopic.php?id=185440](https://bbs.archlinux.org/viewtopic.php?id=185440)

---

### Post by SBTlauien on 2017-06-28
> **monkeybrain20122 said:**
> Maybe the last line of this post would help?

[https://bbs.archlinux.org/viewtopic.php?id=185440](https://bbs.archlinux.org/viewtopic.php?id=185440)

That is the exact same line that I posted in my post above yours.  It didn't seem to work.

---

### Post by SBTlauien on 2017-07-02
Bump.

---

