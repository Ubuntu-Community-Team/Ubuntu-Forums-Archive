---
title: "Problem With Video After installation"
date: 2007-03-23
forum: General Help
---

### Post by kereetya on 2007-03-23
Hello All,

Ive searched through the forums and all over google and can not find any help on a issue im running into, so if any one can shed some light on this, I would be very great full. Im not that very Linux savy so if this has already been ask I apologies in advance.

I am trying to setup a virtual connection through Virtual PC version 7.0 with Ubuntu version 5.04.  My native Machine is a Windows XP Media Center Edition  with a P4 2.8gig, 1gig of Ram and a Nvidia GForce 7600 GTS.

I get through the install of Ubuntu perfectly fine but when i get to the login page the screen converts a Widescreen format, and the screen is pretty much black with a few discolored objects here and there.  I try to push Alt+enter to go to full screen but Virtual PC comes back stating that the layout is in a format that does not support Full screen.

I found some where to run for the command line:  sudo dpkg-reconfigure xserver-xorg.  ive tried that serveral times with no success.  If i let it autoconfig the video drivers i get the same results list above.  but is change the drivers over to another one, after the reboot it keeps comming up with an error stating that the KDM could not start and the XSERVER has the be turned off and it goes to the command line.   Also no matter what config i put in the XSERVER it still keeps it in a Widscreen format which i do not want.

If anyone knows the solution, if this is setup is even possible, or any other advice please let me know. 

thanks in advance

---

### Post by thelinuxguy on 2007-03-23
> **kereetya said:**
> Hello All,
I get through the install of Ubuntu perfectly fine but when i get to the login page the screen converts a Widescreen format, and the screen is pretty much black with a few discolored objects here and there.  I try to push Alt+enter to go to full screen but Virtual PC comes back stating that the layout is in a format that does not support Full screen.


I had the same problem when trying to install Red Hat Enterprise Linux (Server) 4 as well as Dapper on virtual PC 2004. For RHEL, I had to boot into runlevel 3 to get the terminal and then modify the video settings to use a default depth of 16 instead of 24. 

The page at [http://vpc.visualwin.com/](http://vpc.visualwin.com/) reports a similar solution for ubuntu. Its for Virtual PC 2004 but the problem is same as yours i.e. distorted GUI. So it **might** work on the version you have. Have a look at [http://weblogs.asp.net/pscott/archive/2005/10/13/427426.aspx](http://weblogs.asp.net/pscott/archive/2005/10/13/427426.aspx) as well.

Edit /etc/X11/xorg.conf and change 
```
DefaultDepth 24 
``` 
to 
```
DefaultDepth 16
```


Having said this, I would **strongly** recommend VMWare Server over Virtual PC. You can download it here: [http://www.vmware.com/download/server/](http://www.vmware.com/download/server/)

Hope this helps.

---

### Post by kereetya on 2007-03-23
thanks will check those links out and see if that resolves anything

---

