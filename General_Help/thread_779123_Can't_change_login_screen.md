---
title: "Can't change login screen"
date: 2008-05-02
forum: General Help
---

### Post by maxclimber1w on 2008-05-02
Hello. My problem is this: I dual boot Ubuntu and Kubuntu (which I installed first), but I am tired of the KDE blue login screen. However, when I go to system/admin/login screen, I get an error that says:

"GDM (GNOME Display Manager) is not running. You might be using a different display manager, such as KDM (KDE Display Manager), CDE login (dtlogin), or xdm. If you wish to use this feature, then your system will need to be configured to use GDM instead."

how do I change this?

---

### Post by GOROSSI on 2008-05-02
You will need to edit the kdmrc file located in /etc/kde3(IF YOUR RUNNING KDE4 it might be kde4)/kdm

COPY and Paste the kdmrc to your desktop first

to do this you will need to type in konsole the folowing cd /etc/kde3/kdm/

then sudo kate kdmrc (type password when promted


It should look like this

[PHP][General]
ConfigVersion=2.3
ConsoleTTYs=tty1,tty2,tty3,tty4,tty5,tty6
PidFile=/var/run/kdm.pid
ReserveServers=:1,:2,:3
ServerVTs=-7
StaticServers=:0

[Shutdown]
BootManager=None
HaltCmd=/sbin/poweroff
RebootCmd=/sbin/reboot

[X-*-Core]
AllowNullPasswd=false
AllowRootLogin=false
AllowShutdown=Root
AutoReLogin=false
ClientLogFile=.xsession-errors-%s
Reset=/etc/kde3/kdm/Xreset
Session=/etc/kde3/kdm/Xsession
Setup=/etc/kde3/kdm/Xsetup
Startup=/etc/kde3/kdm/Xstartup

[X-*-Greeter]
AntiAliasing=true
ColorScheme=
EchoMode=OneStar
FaceSource=AdminOnly
FailFont=Sans Serif,10,-1,5,75,0,0,0,0,0
GUIStyle=
GreetFont=Sans Serif,22,-1,5,50,0,0,0,0,0
GreetString=Welcome to Kubuntu at %n
GreeterPos=50,50
HiddenUsers=
Language=en_US
LogoArea=Logo
LogoPixmap=
MaxShowUID=29999
MinShowUID=1000
Preloader=/usr/bin/preloadkde
SelectedUsers=
ShowUsers=NotHidden
SortUsers=true
StdFont=Sans Serif,10,-1,5,50,0,0,0,0,0
Theme=/usr/share/apps/kdm/themes/kubuntu-no-userlist
UseBackground=true
UseTheme=true
UserCompletion=false
UserList=true

[X-:*-Core]
AllowNullPasswd=true
AllowShutdown=All
NoPassEnable=false
NoPassUsers=
ServerArgsLocal=-nolisten tcp
ServerCmd=/usr/bin/X -br

[X-:*-Greeter]
AllowClose=true
DefaultUser=neal
FocusPasswd=false
LoginMode=DefaultLocal
PreselectUser=None

[X-:0-Core]
AutoLoginAgain=false
AutoLoginDelay=0
AutoLoginEnable=false
AutoLoginLocked=false
AutoLoginUser=neal
ClientLogFile=.xsession-errors

[Xdmcp]
Enable=false
Willing=/etc/kde3/kdm/Xwilling
[/PHP]

Under the section **[X-*-Greeter]**
find the line "theme" then extract the theme you want to use to the directory in my example code then
change the name to the login you want to use

hope this helps

---

### Post by GOROSSI on 2008-05-02
Sorry I hadn't read your post properly 

try reinstalling gdm through synaptic package manager (by searching for gdm and selecting it for reinstallation) and also do the same to remove kdm if you want
 
as my first solution only tells you how to change the kdm theme sorry, but it may fix your problem anyway

---

### Post by Zorael on 2008-05-03
Opinion, but I would suggest you leave kdmrc alone and instead edit **/etc/default/kdm.d/20_kubuntu_default_settings**; upon start of the login manager, it'll import the settings defined there which override duplicate settings in that kdmrc file. Makes things more legilible.

DO NOTE that, for the import to work, the **Theme=** line under the **[X-*-Greeter]** heading in /etc/kde3/kdm/kdmrc *must* say:
```
Theme=@@@ToBeReplacedByDesktopBase@@@
```
And likewise, the **Wallpaper=** line in **/etc/kde3/kdm/backgroundrc** *must* say:
```
Wallpaper=default_blue.jpg
```

Explanation: **/etc/init.d/kdm** checks for these lines in the mentioned files (kdmrc and backgroundrc in /etc/kde3/kdm/), and if the Wallpaper and Theme settings differ, it doesn't import the kubuntu-specific settings under **/etc/default/kdm.d/**.

This means that if you at any point try to change wallpaper in the Login Manager section in system settings, it'll change the Wallpaper= line, which'll break the importing. If you at any point wish to change the wallpaper, make the appropriate changes to backgroundrc *as well as* the .xml file in the theme you're using, which are usually located in **/usr/share/apps/kdm/themes/**.

---

