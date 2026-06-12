---
title: "Minitab 14 In Feisty"
date: 2007-08-03
forum: General Help
---

### Post by dean.mcniven@gmail.com on 2007-08-03
This is my first post here and i hope it can help somebody else.

This post details how to install Minitab 14 under wine in Ubuntu Feisty.

Firstly install wine if you have not already done so.
```
sudo apt-get install wine
```

Next, Configure wine to emulate Windows XP.
```
System -> Preferences -> Wine Configuration
Under the "Applications", change the "Windows" combobox to "Windows XP"
```

Now to Install Minitab open a new terminal
```
Applications -> Accessories -> Terminal
```

Place the Minitab installation cd in the cdrom drive, then navigate to the setup application. In my case this was
```
cd /media/cdrom0
cd Minitab_14
```

Run the setup application with wine and follow the on-screen instructions. In my case ...
```
wine setup.exe
```

At this point Minitab is installed however it will not launch. This is because Minitab 14 Relies on Internet Explorer. To install M$ IE, goto the downloads section of the Microsoft website and search for "Internet Explorer 6" and download the installer to your desktop.
Then the Terminal we used earlier type
```
wine ~/Desktop/ie6setup.exe
*Note!* Change the filename to the one you downloaded
```

When the Internet Explorer setup is complete, Minitab should launch and run without any issues.

---

