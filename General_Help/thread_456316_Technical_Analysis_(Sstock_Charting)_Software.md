---
title: "Technical Analysis (Sstock Charting) Software"
date: 2007-05-27
forum: General Help
---

### Post by ravisghosh on 2007-05-27
I have been searching for a good technical analysis (stock charting) software that run on linux. I tried qtstalker, merchant of venice, aiotrader, eclipsetrader, but none come close to TA softwares running on windows like metastock, amibroker, tradestation. 

Could you guys suggest something. Looking for suggestions

Thanks in advance.

---

### Post by sinfree on 2007-05-27
Out of curiosity, what specific program or programs in Windows are you referring to that have the features you want (for comparison).  Also, is running one of these programs through wine or virtualization (such as VirtualBox, or VMWare) an ok solution, or do you require a linux native app?

---

### Post by ravisghosh on 2007-05-29
Window specific software are metastock, amibroker, tradestation, advance get, etc.

With virtual machine, one is able to run any window software and tried VMware, but with that my 1-ghz 256-mb ram system is so slow that its better not running at all.

With wine, I was not able to install metastock but got success in amibroker but having trouble getting it working, trying solutinos though. 

A native linux app is always preferable than using wine or anything else. Isnt it?

---

### Post by ravisghosh on 2007-05-29
I installed amibroker over wine on a linux box. After few issues with dll, I was able to get it starting, but now when I try to get data using [COLOR="#ff0000"]File>Import Wizard>PIck files>define fields [/COLOR]and when i click "finish" I get this error:

[COLOR="Red"]cannot open or write to format defition file. Check read-only flags.[/COLOR]

I have checked the attributes of contents of [COLOR="#ff0000"]"~/.wine/drive_c/Program Files/AmiBroker/Formats/"[/COLOR] and they are not read only.

I am confused. This works well on windows. Any suggestinos guys.

---

### Post by ravisghosh on 2007-05-29
Instead of writing the whole path of exe, I went into the Amibroker folder in a console by doing cd and then ran 

[COLOR="Red"]wine Broker.exe[/COLOR]

Then Amibroker worked fine. I dont know why. but its working. 

however, it gives this error in console

[COLOR="#ff0000"]Warning: could not find DOS drive for current working directory '/home/shantanu', starting in the Windows directory.
err:module:import_dll Library qpdll.dll (which is needed by L"C:\\Program Files\\AmiBroker\\Plugins\\QP2.dll") not found
err:module:import_dll Library FastTrack.dll (which is needed by L"C:\\Program Files\\AmiBroker\\Plugins\\FT.dll") not found
[shantanu@bluehead ~]$ [/COLOR]

On searching my windows directory, I could not find anything like qpdll.dll or FastTrack.dll. On searching web also, I could not find anything like qpdll.dll, but FastTrack.dll seems to be a malware!!!

---

### Post by newbiehardy on 2008-05-22
I've been searching for years in vain for ways to migrate over to Linux but was held back because I need to use Metastock for charting.

Upon the release of Hardy Heron, I've spent a full week experimenting with it. The good news is that I've finally figured out a way to get Metastock Professional 8 to work flawlessly in it.

Check out the screenshot here : [http://img521.imageshack.us/img521/3587/metastockusingvirtualboys5.png]("http://img521.imageshack.us/img521/3587/metastockusingvirtualboys5.png")

Here is a video demonstration of it in YouTube : [http://www.youtube.com/watch?v=PEIupV0jMIQ]("http://www.youtube.com/watch?v=PEIupV0jMIQ")

The graphics is just a tad slower (almost imperceptible) than when using Metastock in Windows XP, but for the convenience of being able to use Linux as the host operating system, this deal is hard to beat. Also, unlike gamers, that speed difference is immaterial to most chartists.

With the Windows XP operating as a virtual machine inside your Linux desktop, your usual data provider's software should work as if it were operating within Windows XP. However, I've noticed that the speed of my daily EOD data updates is not as fast since that data has to be written to a virtual harddisk. Nevertheless, it is still at an acceptable speed.

To get this setup working, you'll need to download a free open-sourced virtualisation software called [VirtualBox]("http://www.virtualbox.org/"). Then install Windows XP into it, followed by Metastock and your data provider's software.

Note that the free Sunbelt Personal Firewall 4 works fine inside the virtual Windows XP, while Comodo Firewall Version 3.0 crashes that virtual system.

A significant advantage of using VirtualBox is that you can take "snapshots" of your virtual machine, which in this case is Windows XP. The snapshot will save everything in your virtual PC up to that particular point in time. If you mess up your system with bad installs, or get infected with a virus, you can always recover back to a previous saved point in time without having to reformat your PC's harddisk and reinstall all the software again. It's a real time saver!

Below are the detailed steps for the installation and setup for Hardy Heron.

Instructions on how to get and install VirtualBox version 1.5.6 are here :
[http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html]("http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html")

To key in those commands, start the Terminal mode by clicking on [Applications],[Accessories],[Terminal]. Then copy the relevant text and paste it into the terminal. Remember to press the [ENTER] key after pasting the text. 

Some broken packages may exist but that can be taken care of by clicking on the Red arrow at the desktop panel which is beside the date and time. Alternatively, Synaptic Package Manager can fix those broken packages. It can be accessed from [System],[Administration], [Synaptic Package Manager]

After the software is installed, you can access it from [Applications][System Tools]. Before you start the software, you need to add yourself to the vboxusers group before VirtualBox allows you to access it. [Steps : click on - System,Administration, Users & Groups, your account name, Unlock, enter password, add your account name to vboxusers.] Logoff, then login again and VirtualBox will grant you access.

Once VirtualBox is up and running, click on the [NEW] button and a wizard will appear to guide you through your Windows XP installation. Just follow the instructions accordingly. You'll need to have your Windows XP installation disc available in order to perform this installation.

After installing Windows XP into VirtualBox, run the virtual Windows XP and you can now install Metastock, your data provider's software, your firewall and any other relevant software in the same way that you would install them in Windows XP.

However, for an optimal experience, do complete these last 2 steps from the taskbar of the virtual window:

1. To free up the mouse pointer to move freely between the guest and host desktops, click on [Devices], [Install Guest Additions]

2. To get seamless integration with your linux desktop, click on [Machine], [Seamless Mode].

Hope this is of help to fellow traders who want to migrate over to Linux.

;)

---

