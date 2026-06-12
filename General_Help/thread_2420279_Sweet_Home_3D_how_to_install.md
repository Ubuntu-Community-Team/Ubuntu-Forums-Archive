---
title: "Sweet Home 3D: how to install?"
date: 2019-06-02
forum: General Help
---

### Post by lpalazzotto on 2019-06-02
I have been having problems with Sweet Home 3D. The version on Synaptic is outdated, and so is the one on Ubuntu Software.
I then went on their website and tried to follow the steps on the Download page to download the installer for Linux [http://www.sweethome3d.com/download.jsp](http://www.sweethome3d.com/download.jsp)
It says:

"*Uncompress the downloaded file and run SweetHome3D application found in the uncompressed directory, possibly using [this tip]("http://askubuntu.com/questions/286621/how-do-i-run-executable-scripts-in-nautilus") to launch it with a double click under Ubuntu. To install                     Sweet Home 3D, move the uncompressed directory in the one of your choice or read [this article]("https://howto-ubuntunew.blogspot.com/2017/10/how-to-install-sweet-home-3d-552.html") to create a launcher."*

The tip mentioned is to run executable scripts in Nautilus: not sure what I should do with that... If anyone knows, please help.

After downloading the software, I follow the steps of the article recommended, making sure to change all references from 5.2.2 to 6.1.2 version. At the very last step, it gives me an error with this message:

W: Failed to fetch [http://ro-mirrors.evowise.com/ubuntu/pool/universe/s/sweethome3d-furniture/sweethome3d-furniture_1.6.4-1_all.deb](http://ro-mirrors.evowise.com/ubuntu/pool/universe/s/sweethome3d-furniture/sweethome3d-furniture_1.6.4-1_all.deb)

Any idea of what I am doing wrong?

---

### Post by again? on 2019-06-02
> The tip mentioned is to run executable scripts in Nautilus: not sure what I should do with that... If anyone knows, please help.

This refers to the option in **nautilus > preferences > behaviour** to run executable text files. (safest to select "ask what to do" then choose run when required)
When enabled you just need to click on /SweetHome3D-6.1.2/SweetHome3D to run.

I downloaded and uncompressed the archive and sweethome3d starts but gives me an opengl error.
[ATTACH=CONFIG]283356[/ATTACH]

Repo version in 18.04 works with oracle java11.
[How to Install Oracle Java 11 in Ubuntu 18.04/18.10]("http://ubuntuhandbook.org/index.php/2018/11/how-to-install-oracle-java-11-in-ubuntu-18-04-18-10/")
[ATTACH=CONFIG]283357[/ATTACH]

---

### Post by mc4man on 2019-06-02
> **lpalazzotto said:**
> 

W: Failed to fetch [http://ro-mirrors.evowise.com/ubuntu/pool/universe/s/sweethome3d-furniture/sweethome3d-furniture_1.6.4-1_all.deb](http://ro-mirrors.evowise.com/ubuntu/pool/universe/s/sweethome3d-furniture/sweethome3d-furniture_1.6.4-1_all.deb)

Any idea of what I am doing wrong?
Try multiple times, that mirror is slow, eventually it'll work for that  .deb of libraries

(- 18.04 and newer has latest version in repos..

---

### Post by lpalazzotto on 2019-06-02
ok: thank you all. Java is installed, I restarted the process as follows:

[FONT=&amp][FONT=&amp][FONT=&amp][FONT=&amp][FONT=&amp][FONT=&amp]$ wget [https://sourceforge.net/projects/sweethome3d/files/SweetHome3D/SweetHome3D-5.5.2/SweetHome3D-5.5.2-linux-x64.tgz](https://sourceforge.net/projects/sweethome3d/files/SweetHome3D/SweetHome3D-5.5.2/SweetHome3D-5.5.2-linux-x64.tgz)

$ tar -zxvf SweetHome3D-6.1.2-linux-x64.tgz
[/FONT][/FONT][/FONT][/FONT][/FONT][/FONT][FONT=&amp][FONT=&amp][FONT=&amp][FONT=&amp][FONT=&amp][FONT=&amp]
*$ sudo mv SweetHome3D-6.1.2 /opt/*[/FONT][/FONT][/FONT][/FONT][/FONT][/FONT]

[I]mv: cannot move 'SweetHome3D-6.1.2' to '/opt/SweetHome3D-6.1.2': Directory not empty
[/I]
Anyone knows how to empty the repository?

---

### Post by lpalazzotto on 2019-06-02
ok: here is what I did to bypass the issue:

[I]$ sudo rsync -a SweetHome3D-6.1.2/ opt/
$ sudo gedit /usr/share/applications/sweethome3d-6.1.2.desktop

** (org.gnome.gedit:): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-spell-language not supported

** (org.gnome.gedit:): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-encoding not supported

** (org.gnome.gedit:): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-position not supported

$ cd /opt/SweetHome3D-6.1.2 /opt/SweetHome3D-6.1.2
$ cp SweetHome3DIcon.png /usr/share/icons/
cp: cannot create regular file '/usr/share/icons/SweetHome3DIcon.png': **Permission denied**[/I]

Why?

---

### Post by The Cog on 2019-06-02
I think you may have just copied everything in your home SweetHome3D-6.1.2/ to /opt, not to a directory in /opt. I think you should not have put a trailing slash on the source folder name.Have a look to check.
Beware that sudo rsync -a will copy the ownership too, leaving the files in /opt owned by you. I would have used sudo cp which would have changed the ownership to root.

as for "cannot create regular file '/usr/share/icons/SweetHome3DIcon.png", this is because you are trying to copy to a system folder - you need to use "sudo cp" to elevate your privileges.

---

### Post by lpalazzotto on 2019-06-02
Thank you for the explanation. How can I erase anything related to Sweet Home 3D from the system and home and start from scratch? I think I have some legacies to get rid off...

---

### Post by again? on 2019-06-03
The repo version of sweethome3d doesn't install to /opt and won't conflict with the downloaded version.
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] dpkg -L sweethome3d**
/.
/usr
/usr/bin
/usr/lib
/usr/lib/mime
/usr/lib/mime/packages
/usr/lib/mime/packages/sweethome3d
/usr/share
/usr/share/applications
/usr/share/applications/sweethome3d.desktop
/usr/share/doc
/usr/share/doc/sweethome3d
/usr/share/doc/sweethome3d/README.Debian
/usr/share/doc/sweethome3d/changelog.Debian.gz
/usr/share/doc/sweethome3d/copyright
/usr/share/icons
/usr/share/icons/hicolor
/usr/share/icons/hicolor/128x128
/usr/share/icons/hicolor/128x128/apps
/usr/share/icons/hicolor/128x128/apps/sweethome3d.png
/usr/share/icons/hicolor/16x16
/usr/share/icons/hicolor/16x16/apps
/usr/share/icons/hicolor/16x16/apps/sweethome3d.png
/usr/share/icons/hicolor/22x22
/usr/share/icons/hicolor/22x22/apps
/usr/share/icons/hicolor/22x22/apps/sweethome3d.png
/usr/share/icons/hicolor/48x48
/usr/share/icons/hicolor/48x48/apps
/usr/share/icons/hicolor/48x48/apps/sweethome3d.png
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/sweethome3d.1.gz
/usr/share/mime
/usr/share/mime/packages
/usr/share/mime/packages/sweethome3d.xml
/usr/share/sweethome3d
/usr/share/sweethome3d/sweethome3d.jar
/usr/share/sweethome3d/sweethome3d.sh
/usr/bin/sweethome3d
```

But if you want to remove sweethome3d installed from repositories...
```
sudo apt purge sweethome3d
```

To remove your manual installation you will just have to revert what you did.
Your previous rsync command would have created an opt directory in the same directory as the source.
You do not show the command prompt so not sure what directory you ran it from.

Look in /opt and delete sweethome3d related files folders.
Opt should only have directories not loose files.
[ATTACH=CONFIG]283366[/ATTACH]


You do not need to move the extracted SweetHome3D-6.1.2 directory to /opt
You can run it from anywhere in your home directory by clicking on the file SweetHome3D in the extacted folder.
[ATTACH=CONFIG]283368[/ATTACH]


You can also create a launcher with gedit which will show in the Unity dash.
Save as **sweethome3d-latest.desktop** to ~/.local/share/applications/
```
[Desktop Entry]
Version=1.0
Name=Sweet-home3d-latest
Exec=[COLOR="#FF0000"]/home/glen/Downloads/SweetHome3D-6.1.2/SweetHome3D[/COLOR]
Icon=[COLOR="#FF8C00"]/home/glen/Downloads/SweetHome3D-6.1.2/SweetHome3DIcon.png[/COLOR]
StartupNotify=true
Terminal=false
Type=Application
Categories=Graphics;2DGraphics;3DGraphics;
```
[COLOR="#FF0000"]Use your path to SweetHome3D file.[/COLOR]
[COLOR="#FF8C00"]Use your path to SweetHome3DIcon.png[/COLOR]

Tested in Ubuntu/unity 16.04 live cd.
[ATTACH=CONFIG]283367[/ATTACH]

The repo version and the latest downloaded version can exist on the same machine.
The downloaded sweethome3d.tgz archive comes bundled with java.
The repo sweethome3d version uses your system default java or if java is not installed it will install openjdk.

---

### Post by lpalazzotto on 2019-06-03
Thank you guber2: I think I did what you recommend. When I click on SweetHome3D
and run it in Terminal this is what I get:

[I]Exception in thread "main" java.lang.ExceptionInInitializerError
    at javax.media.j3d.GraphicsConfigTemplate3D.isGraphicsConfigSupported(GraphicsConfigTemplate3D.java:348)
    at com.eteks.sweethome3d.j3d.Component3DManager.createGraphicsConfigurationTemplate3D(Unknown Source)
    at com.eteks.sweethome3d.j3d.Component3DManager.<init>(Unknown Source)
    at com.eteks.sweethome3d.j3d.Component3DManager.getInstance(Unknown Source)
    at com.eteks.sweethome3d.SweetHome3D.addComponent3DRenderingErrorObserver(Unknown Source)
    at com.eteks.sweethome3d.SweetHome3D.init(Unknown Source)
    at com.eteks.sweethome3d.SweetHome3D.main(Unknown Source)
Caused by: com.jogamp.opengl.GLException: Profiles [GL4bc, GL3bc, GL2, GLES1] not available on device null
    at com.jogamp.opengl.GLProfile.get(GLProfile.java:1039)
    at com.jogamp.opengl.GLProfile.get(GLProfile.java:1050)
    at com.jogamp.opengl.GLProfile.getMaxFixedFunc(GLProfile.java:803)
    at javax.media.j3d.JoglPipeline.initialize(JoglPipeline.java:131)
    at javax.media.j3d.Pipeline.createPipeline(Pipeline.java:92)
    at javax.media.j3d.MasterControl.loadLibraries(MasterControl.java:858)
    at javax.media.j3d.VirtualUniverse.<clinit>(VirtualUniverse.java:267)
    ... 7 more
[/I]
It gets stuck there. What am I missing? Java, GLE?

---

### Post by lpalazzotto on 2019-06-03
Ok: I think I know what I am missing now:

[I]Java 3D: implicit antialiasing enabled
Java 3D ERROR : GLX extension is not supported
    GLX version 1.3 or higher is required
Gtk-Message: 23:46:53.643: Failed to load module "canberra-gtk-module"
Exception in thread "AWT-EventQueue-0" java.lang.NullPointerException
[/I]etc.

The problem is that I do not have the GLX installed, and most likely need to uninstall something before. Any advice?

---

### Post by again? on 2019-06-03
May be due to your gfx driver/opengl renderer being used.
Post your gfx details.
I'm not on top of java and glx but others may know.

Inxi is a script in the repos that makes it easier.
```
sudo apt install inxi
```

Then post the output of 
```
inxi -G
```
eg
```
glen@Bionic:~$ inxi -G
Graphics:  Card: NVIDIA GF116 [GeForce GTX 550 Ti]
           Display Server: x11 (X.Org 1.19.6 ) driver: nvidia Resolution: 1680x1050@59.88hz
           OpenGL: renderer: GeForce GTX 550 Ti/PCIe/SSE2 version: 4.6.0 NVIDIA 390.116
```

Please use code blocks...see sig below.

---

### Post by mastablasta on 2019-06-04
start the java version. it will work.

run the java file. the other one doesn't seem to work so i stopped bothering with it. not sure why it doesn't work. i tried oracle java, opensource java...

---

### Post by again? on 2019-06-04
> **mastablasta said:**
> start the java version. it will work.

run the java file. the other one doesn't seem to work so i stopped bothering with it. not sure why it doesn't work. i tried oracle java, opensource java...

Hi mastablasta,
what's the main difference between these 2 start scripts.
First one gives me the opengl error.

---

### Post by lpalazzotto on 2019-06-04
Hi guber2,
Here it is:

Graphics:
  Device-1: Intel UHD Graphics 630 driver: i915 v: kernel 
  Device-2: NVIDIA GP107M [GeForce GTX 1050 Ti Mobile] driver: nvidia 
  v: 390.116 
  Display: x11 server: X.Org 1.20.4 driver: intel resolution: 1920x1080~60Hz 
  OpenGL: renderer: N/A v: N/A 

@mastablasta : what package of Java should I download? There are billions and I do not understand the differences.
Is there anything easy that I can download from the Repository?
p.d. I tried the java version and it gives me the same error as the other one. And I think I have Oracle Java installed already.

---

### Post by again? on 2019-06-04
So neither of the start scripts shown in my previous post pic work?

---

### Post by lpalazzotto on 2019-06-04
Oh, yeah, sorry. Here is the result:

$ sudo apt-get update

Hit:1 [http://ro-mirrors.evowise.com/ubuntu](http://ro-mirrors.evowise.com/ubuntu) disco InRelease
Hit:2 [http://ppa.launchpad.net/linuxuprising/java/ubuntu](http://ppa.launchpad.net/linuxuprising/java/ubuntu) disco InRelease
Hit:3 [http://ro-mirrors.evowise.com/ubuntu](http://ro-mirrors.evowise.com/ubuntu) disco-updates InRelease             
Ign:4 [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) disco InRelease          
Get:5 [http://ro-mirrors.evowise.com/ubuntu](http://ro-mirrors.evowise.com/ubuntu) disco-backports InRelease [88.8 kB]
Err:6 [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) disco Release            
  404  Not Found [IP: 91.189.95.83 80]
Hit:7 [http://ro-mirrors.evowise.com/ubuntu](http://ro-mirrors.evowise.com/ubuntu) disco-security InRelease
Hit:8 [http://ro-mirrors.evowise.com/ubuntu](http://ro-mirrors.evowise.com/ubuntu) disco-proposed InRelease
Hit:9 [http://gm.archive.ubuntu.com/ubuntu](http://gm.archive.ubuntu.com/ubuntu) bionic InRelease    
Ign:10 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:11 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release
Reading package lists... Done
E: The repository 'http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu disco Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

$ sudo apt-get install oracle-java11-installer
E: Could not get lock /var/lib/dpkg/lock-frontend - open (11: Resource temporarily unavailable)
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), is another process using it?

---

### Post by lpalazzotto on 2019-06-04
Neither of the start script work.

---

### Post by lpalazzotto on 2019-06-04
Btw: I think Java-12 is installed, according to Synaptic.

I still do not understand this GLX 1.3 thing: it has something to do with the drive I guess.

---

### Post by again? on 2019-06-04
> **lpalazzotto said:**
> Hi guber2,
Here it is:

Graphics:
  Device-1: Intel UHD Graphics 630 driver: i915 v: kernel 
  Device-2: NVIDIA GP107M [GeForce GTX 1050 Ti Mobile] driver: nvidia 
  v: 390.116 
  Display: x11 server: X.Org 1.20.4 driver: intel resolution: 1920x1080~60Hz 
  OpenGL: renderer: N/A v: N/A 

I would say your issue is most likely due to having 2 gfx devices.
Inxi shows "OpenGL: renderer: N/A v: N/A".
Don't know if this is a fault with inxi or your gfx/drivers.

Only ever having the single nvidia gfx card I don't know how to work through the issue.
Maybe your GP107M gfx device is not being used by default? Bumblebee? 
Post the output of 
```
inxi -b
ubuntu-drivers devices
cat /var/log/gpu-manager.log

```
and others more familiar with your hardware may be able to guide you.

---

### Post by mastablasta on 2019-06-05
> **guber2 said:**
> Hi mastablasta,
what's the main difference between these 2 start scripts.
First one gives me the opengl error.

I think one uses some old java  or something. not sure exactly anymore, but they have it written in one of the documentation files. but in some cases the launcher didn't work while the older one does. the java one uses some libraries that are supplied with the program i believe.  i believe that in case of this java launcher you might also need to assign maximum RAM usage manually. or are you saying neither of them works?

> **lpalazzotto said:**
> Hi guber2,
Here it is:

Graphics:
  Device-1: Intel UHD Graphics 630 driver: i915 v: kernel 
  Device-2: NVIDIA GP107M [GeForce GTX 1050 Ti Mobile] driver: nvidia 
  v: 390.116 
  Display: x11 server: X.Org 1.20.4 driver: intel resolution: 1920x1080~60Hz 
  OpenGL: renderer: N/A v: N/A 

@mastablasta : what package of Java should I download? There are billions and I do not understand the differences.
Is there anything easy that I can download from the Repository?
p.d. I tried the java version and it gives me the same error as the other one. And I think I have Oracle Java installed already.

intel should work just fine. if you render more complex images i think the CPU is then used (because mine does it really slow)

i would suggest to go with oracle java if the opensource one is not working. unfortunately it is not so easy to install anymore, because Oracle closed the license or requires some registering or something. before we would just add a PPA and install it.
ver 11:
[https://tecadmin.net/install-oracle-java-11-ubuntu-18-04-bionic/](https://tecadmin.net/install-oracle-java-11-ubuntu-18-04-bionic/)

or 12:
[https://www.linuxuprising.com/2019/03/how-to-install-oracle-java-12-jdk-12-in.html](https://www.linuxuprising.com/2019/03/how-to-install-oracle-java-12-jdk-12-in.html)

i would need to investigate a bit more at home, but i do remember that installer and all that didn't really work.

---

### Post by lpalazzotto on 2019-06-05
@mastablasta

That's what it was, darn Oracle! the license! I had Java already installed (11), then upgraded via Synaptic to 12, that does not warn you about the license issue. I then did it from the terminal, that specifically ask to accept the license and refers to the link you just posted [https://www.linuxuprising.com/2019/03/how-to-install-oracle-java-12-jdk-12-in.html](https://www.linuxuprising.com/2019/03/how-to-install-oracle-java-12-jdk-12-in.html)
(see below). Now both start scripts work, although when I run them in terminal I still receive a weird message:

[I]Java 3D: implicit antialiasing enabled
Gtk-Message: 13:00:22.515: Failed to load module "canberra-gtk-module".
[/I]
that does not prevent the software to open though.

I have not tried yet to actually create anything, so I am not sure if there will be bugs or issues, but at least it opens...

Here is the part that from Synaptic you would miss, for reference to other users that may read this thread in the future:
[h=2]How to auto-accept the Oracle Java 12 license[/h]
Want to automatically accept the Oracle Java 12 license? This may be  useful for automation - running the Oracle JDK 12 installer in a script,  etc. You can accept the license by using this command:

echo oracle-java12-installer shared/accepted-oracle-license-v1-2 select true | sudo /usr/bin/debconf-set-selections
If that doesn't work, you may also want to try this to auto-accept the Oracle Java 12 license:

echo oracle-java12-installer shared/accepted-oracle-licence-v1-2 boolean true | sudo /usr/bin/debconf-set-selections

---

### Post by lpalazzotto on 2019-06-05
@guber2
Here is what I get if I follow your commands.
It does show the two gfx, I think... If there is anything I should correct, let me (or others) know.

Thank you for all the support so far!
We should report to Oracle about all this non-sense...

luca@luca-XPS-15-9570:~$ inxi -b
System:
  Host: luca-XPS-15-9570 Kernel: 5.0.0-16-lowlatency x86_64 bits: 64 
  Desktop: Gnome 3.32.1 Distro: Ubuntu 19.04 (Disco Dingo) 
Machine:
  Type: Laptop System: Dell product: XPS 15 9570 v: N/A 
  serial: <root required> 
  Mobo: Dell model: 0D0T05 v: A00 serial: <root required> UEFI: Dell 
  v: 1.10.1 date: 04/26/2019 
Battery:
  ID-1: BAT0 charge: 53.8 Wh condition: 93.2/97.0 Wh (96%) 
CPU:
  6-Core: Intel Core i7-8750H type: MT MCP speed: 900 MHz 
  min/max: 800/4100 MHz 
Graphics:
  Device-1: Intel UHD Graphics 630 driver: i915 v: kernel 
  Device-2: NVIDIA GP107M [GeForce GTX 1050 Ti Mobile] driver: nouveau 
  v: kernel 
  Display: x11 server: X.Org 1.20.4 driver: intel resolution: 1920x1080~60Hz 
  OpenGL: renderer: Mesa DRI Intel UHD Graphics 630 (Coffeelake 3x8 GT2) 
  v: 4.5 Mesa 19.0.2 
Network:
  Device-1: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter 
  driver: ath10k_pci 
  Device-2: Qualcomm Atheros type: USB driver: btusb 
Drives:
  Local Storage: total: 238.47 GiB used: 29.87 GiB (12.5%) 
Info:
  Processes: 353 Uptime: 1h 17m Memory: 7.44 GiB used: 2.47 GiB (33.2%) 
  Shell: bash inxi: 3.0.33 
luca@luca-XPS-15-9570:~$ ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd00001C8Csv00001028sd0000087Cbc03sc02i00
vendor   : NVIDIA Corporation
model    : GP107M [GeForce GTX 1050 Ti Mobile]
driver   : nvidia-driver-390 - distro non-free
driver   : nvidia-driver-418 - distro non-free recommended
driver   : xserver-xorg-video-nouveau - distro free builtin

== /sys/devices/pci0000:00/0000:00:1f.3 ==
modalias : pci:v00008086d0000A348sv00001028sd0000087Cbc04sc03i80
vendor   : Intel Corporation
model    : Cannon Lake PCH cAVS
driver   : oem-audio-hda-daily-dkms - third-party free

luca@luca-XPS-15-9570:~$ cat /var/log/gpu-manager.log
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/5.0.0-16-lowlatency/updates/dkms
Looking for amdgpu modules in /lib/modules/5.0.0-16-lowlatency/updates/dkms
Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is intel loaded? yes
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is amdgpu versioned? no
Is amdgpu pro stack? no
Is nouveau loaded? yes
Is nouveau blacklisted? no
Is nvidia kernel module available? no
Is amdgpu kernel module available? no
Vendor/Device Id: 8086:3e9b
BusID "PCI:0@0:2:0"
Is boot vga? yes
Vendor/Device Id: 10de:1c8c
BusID "PCI:1@0:0:0"
Is boot vga? no
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card1", driven by "nouveau"
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card1", driven by "nouveau"
Skipping "/dev/dri/card0", driven by "i915"
Found "/dev/dri/card1", driven by "nouveau"
Number of connected outputs for /dev/dri/card1: 0
Found "/dev/dri/card0", driven by "i915"
output 0:
    card0-eDP-1
Number of connected outputs for /dev/dri/card0: 1
Does it require offloading? yes
last cards number = 2
Has amd? no
Has intel? yes
Has nvidia? yes
How many cards? 2
Has the system changed? No
Intel IGP detected
Desktop system detected
or laptop with open drivers
Nothing to do

---

### Post by mastablasta on 2019-06-05
i was sort of correct. The Java3d-1_5_2 launches the older and packaged java 3D 1.5.2 instead of the default java 3D 1.6.
for some reason Ubuntu with Nvidia Chip can not run 1.6. so using the other launcher could solve the issue. at least it does for me. here is some more info: 
[http://www.sweethome3d.com/support/forum/viewthread_thread,8073_lastpage,yes;jsessionid=F678B48CA1E30EB8477489126650EE33](http://www.sweethome3d.com/support/forum/viewthread_thread,8073_lastpage,yes;jsessionid=F678B48CA1E30EB8477489126650EE33)

however both options seem that they should run fine on Intel drivers.

@ lpalazzotto you are using only the intel chip. it should work fine for this application. i use intel on Windows PC with this java based program.

However you also have an option of installing ```
nvidia-driver-418 - distro non-free recommended
```

since you have a two chip setup you will then use optirun or bumblebee to switch between the chips. as i understand in windows the chips switch automatically based on how GPU demanding the application is. But in linux you would run the nvidia chips manually when you need it's power. at least thatis how i understand it becuase nvidia didn't bring the optimus feature to linux or at least not in the same way as they did in windows.

someone with more experience in dual chip should advise you here. i can see on internet that after 18.04 some people are having new issues with these setups on ubuntu.

problem with an optional solution: [https://devtalk.nvidia.com/default/topic/1032482/optimus-on-ubuntu-18-04-is-a-step-backwards-but-i-found-the-first-good-solution/](https://devtalk.nvidia.com/default/topic/1032482/optimus-on-ubuntu-18-04-is-a-step-backwards-but-i-found-the-first-good-solution/)
another option: [https://medium.com/@agathver/nvidia-gpu-optimus-prime-and-ubuntu-18-04-woes-f52e7f850f3d](https://medium.com/@agathver/nvidia-gpu-optimus-prime-and-ubuntu-18-04-woes-f52e7f850f3d)

---

