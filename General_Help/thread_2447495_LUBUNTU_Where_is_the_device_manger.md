---
title: "LUBUNTU Where is the device manger ?"
date: 2020-07-20
forum: General Help
---

### Post by aug7744 on 2020-07-20
I am new to Ubuntu. Where is the device manager for I see all device drivers installed ?

---

### Post by guiverc on 2020-07-20
You haven't provided your release details, so I cannot know if you're using *legacy* Lubuntu using LXDE, or *modern *Lubuntu using LXQt.

To see if additional drivers are available on your system, use **Software Sources**, found in the Lubuntu manual at [https://manual.lubuntu.me/stable/4/4.3/software_sources.html](https://manual.lubuntu.me/stable/4/4.3/software_sources.html) (scroll down to the **Proprietary ****Drivers** section).

Sorry I don't know what you mean by *device manager*, but if I wanted to look at how my hardware was recognized, I'd use a command.

```
sudo lshw
``` 

will list your hardware (`sudo` elevates privileges as my user account won't be able to get detailed results without raised privileges).  If I wanted to limit the results to a specific class, for example 'video' hardware only, I'd use

```
sudo lshw -C video
```

There are GUI tools that will display that detail too, but personally I find commands faster (paging or searching the result as appropriate).

---

### Post by aug7744 on 2020-07-29
My Lubuntu is the latest version.
Have any tool in Linux that look and work how Windows Device Manager in view devices and install drivers ?
Thanks for reply.

---

### Post by guiverc on 2020-07-29
Please tell me what you mean by the latest version.

The last two people who told me they were using the *latest* version of Lubuntu, were in fact using a *End of Life* release of Lubuntu, but because they didn't download it from a Lubuntu, or Ubuntu site, didn't realize they had installed a EOL version of Lubuntu, despite the web site they downloaded it from stating it was the latest.

---

### Post by GhX6GZMB on 2020-07-29
> **aug7744 said:**
> My Lubuntu is the latest version.
Have any tool in Linux that look and work how Windows Device Manager in view devices and install drivers ?
Thanks for reply.

Forget the "Device Manager".
You really need to open your mind and understand that Lubuntu isn't Windows. A lot of people (myself included) have grown up with all the messy M$ "solutions" and need to think new.

The terminal command "lshw" is the way to go.

---

### Post by rbmorse on 2020-07-29
I kind of have a feeling I know where this is going to end up, so why don't you just tell us which piece of hardware you're thinking about and we can answer the question more directly.

---

### Post by pbear42 on 2020-07-29
> **aug7744 said:**
> My Lubuntu is the latest version.
Sigh, you could have answered the question in fewer keystrokes.  Whereas "latest version" (you know about) conveys no information.
> Have any tool in Linux that look and work how Windows Device Manager in view devices and install drivers ?
The premise of the question suggests a misunderstanding of how Linux works.  Your system doesn't have a bunch of drivers installed.  The drivers are in the kernel.  The appropriate ones are loaded as the system brings itself up and detects hardware.  There is a section in Software Sources for Additional Drivers (can be accessed from Menu under either name, as it happens), but usually that will be empty or have only one or two items (which you would have added yourself post-installation).

Anyhoo, are you just curious?  Or is there a particular problem you're trying to solve?

---

### Post by HermanAB on 2020-07-30
In general, if your machine works, then you have no reason to worry about 'device drivers' - these are modules permanently linked with, or dynamically loaded into the kernel, as needed.  

If you want to learn all about Linux device drivers, there is an excellent book written by Mr Croah-Hartman [https://www.oreilly.com/library/view/linux-device-drivers/0596005903/](https://www.oreilly.com/library/view/linux-device-drivers/0596005903/)

Last I dabbled in device drivers, this book wasn't written yet...

---

### Post by aug7744 on 2020-07-30
Thanks for all replies. Using Lubuntu 20.04. I want to use an GUI to see more easy all devices installed. Have devices not installed and not working being GeForce GT 640, Realtek HD Audio and MODEM Huawei E173. Video card drivers was downloaded, but I want to install drivers proprietary.

---

### Post by HermanAB on 2020-07-30
You can list all kernel modules with lsmod.

A GUI makes simple things more difficult.

---

### Post by aug7744 on 2020-07-31
I wait an GUI to see displayed in an tree view all devices. I understand that command line is fast, but is an wrong that Linux not make some tasks more simple. Have devices that look how not having drivers installed (USB3, MODEM, etc).

---

### Post by mc4man on 2020-07-31
Install hardinfo
```
sudo apt install hardinfo
```

---

### Post by aug7744 on 2020-08-02
@pbear42
"Anyhoo, are you just curious? Or is there a particular problem you're trying to solve?"
I need to install an MODEM 3G Huawei E173.

@HermanAB
"A GUI makes simple things more difficult."
Only wait to see devices in an tree view.

---

### Post by HermanAB on 2020-08-02
Devices are not a tree.  They don't depend on each other.  So lsmod and lsusb are all you need.

---

### Post by TheFu on 2020-08-02
> **aug7744 said:**
> Thanks for all replies. Using Lubuntu 20.04. I want to use an GUI to see more easy all devices installed. Have devices not installed and not working being GeForce GT 640, Realtek HD Audio and MODEM Huawei E173. Video card drivers was downloaded, but I want to install drivers proprietary.

Linux isn't Windows.  There is a different philosophy, completely.  To my knowledge, there isn't any "device manager".  There are tools to gather information.  

To install the current driver for the GT 640 and other connected proprietary hardware, use  **sudo ubuntu-drivers autoinstall**
If the GeForce GT 640 isn't supported by nvidia drivers on 20.04, you'll need to use the F/LOSS drivers or buy a newer GPU.  My 7200 GS became unsupported for 16.04 and, at the time, the F/LOSS video drivers didn't provide the resolution I wanted. I bought a newer, cheap, GPU.

If the autoinstall doesn't work (you'll need to reboot for any GPU driver stuff), then
```
sudo apt install nvidia-driver-390 
``` should get the correct driver for 20.04.

A few strong suggestions.
[LIST]
[*]Don't go looking for drivers from any vendor's website for Linux.  These are usually not needed and definitely haven't been vetted by Canonical. Often, those installations will turn out badly.
[*]Only install software using the _package manager_ on the system.  Don't go looking to download software "packages" from websites.  Use the package manager which gets updated daily with a list of all 60K packages available. The package manager has categories of software to help humans find the packages more easily.
[*]Any software added through the package manager is automatically maintained whenever an "update/upgrade" is performed. You can manually do that or you can setup your flavor to do it daily, weekly, or bi-weekly automatically.  **Any software loaded outside the package manager doesn't get updates.**  This is a key difference between the Windows-way and the Linux way (for most Linuxen).
[/LIST]

The realtek audio should just be working. If Lubuntu uses Pulse Audio, then the built-in audio controls should be sufficient. If you need more control, **pavucontrol** can be used. If it isn't working, there is a sub-forum here for audio issues. Post there after running through the audio troubleshooting script.  

There is probably a GUI program so show the system hardware too.  I just don't use GUIs enough to remember the menu name.  Look for *System Information* in the Admin or Systems menu.  [https://itsfoss.com/hardinfo/](https://itsfoss.com/hardinfo/) is one option. Appears that **hardinfo** is in the 20.04 repos. A quick install.  **sudo apt install hardinfo** gets it. Should be in the menu now.

As others have said, the **lshw** command will provide detailed information about the system, devices, and drivers. It isn't a GUI. By saving the output to a file, you can refer to it later, update it, or run comparisons from time to time. Open a terminal to run it.

And perhaps the Lubuntu User's Guide would be helpful.  [https://manual.lubuntu.me/stable/](https://manual.lubuntu.me/stable/)  Lots of answers for "how" in there, but not many "why" answers, sadly.

---

### Post by Yellow Pasque on 2020-08-03
> **aug7744 said:**
> I need to install an MODEM 3G Huawei E173.

Is it being detected as CD/Storage?: [https://rnavagamuwa.com/open-source/setup-usb-modem-on-ubuntu/](https://rnavagamuwa.com/open-source/setup-usb-modem-on-ubuntu/)

---

### Post by aug7744 on 2020-08-03
sudo ubuntu-drivers autoinstall
and
sudo apt install nvidia-driver-390

both commands use internet access or only allow install proprietary drivers ?

---

### Post by TheFu on 2020-08-03
Package managers use internet.

---

### Post by aug7744 on 2020-08-13
@mc4man
Using HardInfo.
Thanks very much.

@Yellow Pasque
MODEM is working. Thanks for your help.

Thanks for all replies :)

---

