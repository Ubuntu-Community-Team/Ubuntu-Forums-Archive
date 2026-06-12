---
title: "Five buttoned mouse?"
date: 2008-02-04
forum: General Help
---

### Post by Dojan5 on 2008-02-04
I have a five buttoned mouse.
Left middle and right click, and two other buttons for going forward and backward in webbrowser and so on.
The problem is that i can only use the middle the left and the right.
I would like to enable the rest, but how do i do that?
I also have two scrolling wheels, one for going vertical and the other for going horizontal. The one for going horizontal don't work either.
But plugged in to windows all the buttons (and scrollwheels) work...
So how do i configure the mouse that much in Ubuntu Gutsy?
Thanks in advance
/
Joel

---

### Post by mlissner on 2008-02-04
I have the logitech revolution mx, and I used btnx to get it up and running. It takes a bit of work, but look around on the forums. I know there are a couple of good tutorials.

---

### Post by jsnelli2 on 2008-02-04
btnx is definitely the way to go.  It's a breeze to run.

---

### Post by Dojan5 on 2008-02-04
Okay... Synaptic to find it?
And, where are the tutorials?

---

### Post by zero-9376 on 2008-02-04
i dont think btnx is in the repos but im quite sure there are debs on the site
[http://www.ollisalonen.com/btnx/](http://www.ollisalonen.com/btnx/)

---

### Post by Dojan5 on 2008-02-04
I think i have trouble installing [http://www.ollisalonen.com/btnx/binaries/btnx_0.4.4-1_i386.deb](http://www.ollisalonen.com/btnx/binaries/btnx_0.4.4-1_i386.deb)
It gives me an error about that the file or the catalog diesnt excist...
Very strange

---

### Post by Dojan5 on 2008-02-05
Nope it isnt in the repository...
Is there any other place to download the file. Perferably a .DEB package since im still unused to other packages.

---

### Post by mlissner on 2008-02-05
Linux's Achiles heel is dependency problems, which occur when one package assumes you have something installed that you don't. Unless I'm mistaken, .deb files have no way to remedy dependencies before they try to install themselves, so if this happens, you will indeed get an error.

What's the error you're getting when you try installing with the file above? If it's something to the tune of, "cannot locate XXX," or "XXX not installed", you might be able to remedy the error yourself with an:
```
apt-get install XXX
```

Hope that helps.

---

### Post by zero-9376 on 2008-02-05
Hmmm, seems there must have been some problem with my post, it hasn't come through. Anyway the jist of it was that the package you referred to installed fine on my gutsy/7.10 system after downloading and then installing with gdebi. Might be helpful to note that I have universe and multiverse enabled. You will also require btnx-config package on the site to configure the mouse via the gu, the btnx package is the daemon.

Debs will not install with unsatisfied dependencies and will try to resolve dependencies automatically, GDebi will tell you that a pakage requires others to be installed.

---

### Post by Dojan5 on 2008-02-05
It doesn't say anything about missing dependencies.

---

### Post by Dojan5 on 2008-02-05
What it says is:
```

(Reading the database ... 199550 files and catalouges are installed.)
Unpacking btnx (from /tmp/btnx_0.4.4-1_i386.deb) ...
dpkg: btnx warning - the configuration file "etc/rc0.d" is not a common (usual) file or a symbolic link (= "/etc/rc0.d")
dpkg: btnx warning - the configuration file "etc/rc2.d" is not a common (usual) file or a symbolic link (= "/etc/rc2.d")
dpkg: btnx warning - the configuration file "etc/rc4.d" is not a common (usual) file or a symbolic link (= "/etc/rc4.d")
dpkg: btnx warning - the configuration file "etc/rc6.d" is not a common (usual) file or a symbolic link (= "/etc/rc6.d")
dpkg: error when handling /tmp/btnx_0.4.4-1_i386.deb (--install):
 could not create ".etc/btnx/events": The file or te catalouge (directory) does not excist

```

I couldn't copy/paste it, i dunno why. And if i could you wouldnt be able to read it since it is in swedish, so i wrote it down translated instead. sorry...

---

### Post by lakersforce on 2008-02-05
Go to the[ [COLOR="SandyBrown"]Ubuntu wiki[/COLOR]]("https://help.ubuntu.com/community/ManyButtonsMouseHowto"). That's all!

---

### Post by Dojan5 on 2008-02-05
Isnt it
```
sudo gedit etc/X11/xorg.conf
```
???
It wont let me open the file, or well, after opening the file is blank...
And when navigating through it in Nautilus i can't seem to save, thus i am the computer administrator...
Ok, solved it....
The real code is:
```
sudo gedit /etc/X11/xorg.conf
```
Quite irritating, missing one lil clammer

---

### Post by Dojan5 on 2008-02-05
Thanks for the wikithingamojig...
Thus it was to hard to configure it...

Okay, so i realised that i didnt do anything wrong in xorg.conf but it is the forward and backward thingy that dont work...
How do i configure imwheel to do that?

A lil not for the future:

Use the firefox code for imwheelrc with alt| something, probably found on the first page...
Save.
Save all your work so there wont be any data losses and
Control+Alt+Backspace
Login to your account and the mouse should work if installed properly.
Thanks everyone, got it working now.
Cheers
/
Joel

---

### Post by lakersforce on 2008-02-06
You should get used to using gksudo when launching graphical applications.

Try and copy and paste this into your xorg.conf replacing your original part of the file. Please note that the order matters!

```
Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device"                "/dev/input/mice"
        Option      "Protocol"              "ExplorerPS/2"
        Option      "Emulate3Buttons"       "false"
        Option      "Buttons"               "7"
        Option      "ZAxisMapping"          "4 5"
        Option      "ButtonMapping"         "1 2 3 6 7 4 5"
EndSection
```

---

