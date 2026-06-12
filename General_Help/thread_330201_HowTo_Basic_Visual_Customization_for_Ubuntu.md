---
title: "HowTo Basic Visual Customization for Ubuntu"
date: 2007-01-02
forum: General Help
---

### Post by fokuslee on 2007-01-02
This guide is written with edgy in mind.  I think it applies to dapper as well.  (UPDated)
Also most changes are gui based so no need to worry.  

1.  [http://www.gnome-look.org/](http://www.gnome-look.org/)  this website has many cool visual elements.  Another site is [http://art.gnome.org/](http://art.gnome.org/)

1. change the login.  on the main menu bar (located at the top assume you have default setup) follow 
System>Administration>Login  Now you can play around with it.  Get more Login themes from the sites above.  
also make sure you match Background color (at the immediate bottom) with your theme's main color, otherwise it looks ugly.  
alternatively open terminal (Applications>Accesorries>Terminal) and type [COLOR="Red"]gksu gdmsetup[/COLOR] 

2. change the ubuntu splash.  (the small background where all the icons load, says nautilus on the bottom) 
go to righclick the ubuntu icon on top left cornner of main menu bar.  
first dl some png pictures, save it in /usr/share/pixmaps/splash/  if you don't have write permission you can use sudo cp /location of your dl picture/blah.png /usr/share/pixmaps/splash/blah.png  
Select Edit Menus, drop down under System tools select Configuration Editor.   Now go to Applications>System Tool>Configuration Editor.  
Go to Apps>Gnome-Session>Options
click splash_image select Edit Key you change it to splash/blah.png  replace blah with wutever you want.  
Note if you don't see the splash after login you might have disabled it at System>Preference>Sessions
make sure you tick the Show Splash on Login checkbox.  

3.  Easiest of them all.  Change background
Select empy area of your desktop,  right click select Change Desktop Background
now change it to wutever picture you downloaded.  

4.(new)  Show the Computer, Home, and Trash desktop icons in GNOME
Open the Configuration Editor, by running the program gconf-editor (see the section called "Start a Program Manually")
Choose apps->nautilus->desktop.
Tick the box beside computer_icon_visible, home_icon_visible, and trash_icon_visible. The changes take effect immediately.

This Guide only shows you the very basic.  For more advanced options Consider Xgl+Compiz 
AIGLX+Beryl (which i use)  
I am also writing a post titled Ubuntu Survival 101 (a newbs guide written by newb (me) for newbs) 
: ) thx for the linky mlissner

So for now good luck  have fun and DO UBUNTU
Shout out to all the super nice pplz on forum and IRC who helped me survive my first encounter with Ubuntu.

---

### Post by neoflight on 2007-01-04
thanks... that was a quick reference guide.

---

### Post by mlissner on 2007-01-07
Here's the link promised to ubuntu 101: [http://www.ubuntuforums.org/showthread.php?t=330206&highlight=custom+kernel](http://www.ubuntuforums.org/showthread.php?t=330206&highlight=custom+kernel)

---

