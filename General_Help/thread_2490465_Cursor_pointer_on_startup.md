---
title: "Cursor pointer on startup"
date: 2023-09-05
forum: General Help
---

### Post by angel mike on 2023-09-05
Does anyone know how to change the cursor pointer on start-up before using any browser. Using Ubuntu 22.04

---

### Post by angel mike on 2023-09-05
Changes made to size using Accessibility do not work. I want to change the appearance as well as the size

---

### Post by dragonfly41 on 2023-09-05
Install Tweaks .. then Tweaks > Appearance >Themes > Cursor

---

### Post by angel mike on 2023-09-05
Thanks Dragonfly but I have used Tweaks but it only works when using a browser not on the startup homepage

---

### Post by vanadium on 2023-09-05
By the startup homepage, you mean the login screen?

---

### Post by angel mike on 2023-09-05
Yes the login screen

---

### Post by Dennis N on 2023-09-05
> **angel mike said:**
> Yes the login screen

Hmm. In your previous thread ("Desktop Cursor"), I thought you were already logged in. This is different. Here you are in the GDM (gnome display manager) environment. There is a utility that can change at least some things on the login screen. In a quick test, I changed the cursor theme from black to white, but I didn't immediately see a way to change the size of the cursor. Maybe it can't handle resizable cursors? 

If you want to experiment, it's a Flatpak (see the screenshot). I don't know what the other selections on the left side will do. There is a "reset settings" to reverse any changes.

```
dmn@Sydney-vm:~$ flatpak info io.github.realmazharhussain.GdmSettings/x86_64/stable
Login Manager Settings - Customize your login screen
          ID: io.github.realmazharhussain.GdmSettings
         Ref: app/io.github.realmazharhussain.GdmSettings/x86_64/stable
        Arch: x86_64
      Branch: stable
     Version: 3.3
     License: AGPL-3.0-or-later
      Origin: flathub
  Collection: org.flathub.Stable
Installation: system
   Installed: 529.9*kB
     Runtime: org.gnome.Platform/x86_64/44
         Sdk: org.gnome.Sdk/x86_64/44

```

---

### Post by angel mike on 2023-09-05
Thanks for perusing this Dennis.
 I found the web site for that Flat pack ([https://flathub.org/apps/io.github.realmazharhussain.GdmSettings](https://flathub.org/apps/io.github.realmazharhussain.GdmSettings)) but not sure how to use it.

---

### Post by #&amp;thj^% on 2023-09-05
> **angel mike said:**
>  but not sure how to use it.
To use:
```
flatpak run io.github.realmazharhussain.GdmSettings
```
EDIT:See Dennis N post below, I put the cart in front of the horse, you will need flatpak installed.
Ubuntu Faltpak:[https://flathub.org/setup/Ubuntu](https://flathub.org/setup/Ubuntu)

---

### Post by Dennis N on 2023-09-05
> **angel mike said:**
> Thanks for perusing this Dennis.
 I found the web site for that Flat pack ([https://flathub.org/apps/io.github.realmazharhussain.GdmSettings](https://flathub.org/apps/io.github.realmazharhussain.GdmSettings)) but not sure how to use it.

Go to **flathub.org**
Click on **Setup Flathub**
Click on Ubuntu Icon
Follow the 4 steps
Now you can install Flatpak applications

As explained in step 2, "Software" gets installed. You can use "Software" to install the flatpak. Search for "login" and install the one shown in the attached image!

---

### Post by angel mike on 2023-09-06
Thanks Dennis for those instructions- will follow themup. It's a pity that Ubuntu cannot improve  the cursor choice  through the Accessibility  function. 
Thanks once again.

---

### Post by angel mike on 2023-09-06
Thanks for those instuctions Dennis  and 1Fallen much appreciated.
 Have installed the flatpak but on running get the following error
app/io.github.realmazharhussain.GdmSettings/x86_64/master not installed

---

### Post by Dennis N on 2023-09-06
Lets remove it and reinstall with the terminal. It's important NOT to use sudo when installing or starting it.
1) Open "Software" to the application's page and click on the trash can (next to the "Open" button) to remove it.
2) After removal is completed, open your terminal and run:
```
flatpak install flathub io.github.realmazharhussain.GdmSettings
```
Restart Ubuntu to get everything settled.
Start the program from the Activities Overview search box (see screenshot #2).

-------------------------------
Further thoughts on the login screen cursor.
1) installing a cursor theme with only one size for cursors eliminates the problem of different sizes. These types of cursor themes do exist.
2) it should be possible to make a custom DMZ-white theme with the larger cursor only and use that on login screen. I will put that on my to-do list.

---

### Post by angel mike on 2023-09-07
Thanks Dennis for the tips - I cannot find the uninstall icon - is there a terminal command to do this

---

### Post by Dennis N on 2023-09-07
> **angel mike said:**
> Thanks Dennis for the tips - I cannot find the uninstall icon - is there a terminal command to do this
Sure.
```
flatpak uninstall io.github.realmazharhussain.GdmSettings
```
For reference, all the flatpak commands and options are shown by terminal command:
```
flatpak --help
```

Also, as to the two ideas in post #13:
> Further thoughts on the login screen cursor.
1) installing a cursor theme with only one size for cursors eliminates the problem of different sizes. These types of cursor themes do exist.
2) it should be possible to make a custom DMZ-white theme with the larger cursor only and use that on login screen. I will put that on my to-do list. 

I determined both of these ideas work. I pursued item #2 and made a change in DMZ-White so that the largest cursor size (48px) is now also used on the login screen. But, this task requires you have the Login Manager working, and also have GIMP installed. If you get these things done, I can explain the procedure.

---

### Post by angel mike on 2023-09-07
Not sure how I managed it but without doing any uninstalling of the Login Manager and its not been setup as far as I can tell -  but I now have a larger black cursor on the startup screen if I specify Yaru for all the settings in Tweks. If I change to DMZ-White the pointer reverts to the normal one - weird.

---

### Post by angel mike on 2023-09-07
Sorry Dennis missed your last post - will follow that and let you know the outcome. Thanks again for your time.

---

### Post by angel mike on 2023-09-07
Okay removed and reinstalled the login manager, The went to the Applications search for the login apps and changed the cursor setting to DMZ- white but had no effect on the large black pointer I am getting on the login screen. What now?

---

### Post by Dennis N on 2023-09-08
> **angel mike said:**
> Okay removed and reinstalled the login manager, The went to the Applications search for the login apps and changed the cursor setting to DMZ- white but had no effect on the large black pointer I am getting on the login screen. What now?

In the Login Settings Manager, be sure you click on "Apply" after selecting the theme or it won't change. Then logout, and the login screen should now have the cursor theme you selected - but only the smallest size will be used. Yours should behave this way. 

Once you  Login Settings Manager changes the theme, we can do a fix to make it use a specific size.

You mention Yaru cursor theme. It is only black. But it has larger sizes available than DMZ-White.

In Settings > Accessibility, Yaru has sizes up to "Largest". DMZ-White has sizes up to "Large". What cursor theme and size did you intend to use?

For reference:

GIMP displays sizes of cursors in pixels (px). 
Largest (the far-right selection) = 96px
Larger = 64px
Large (the middle selection) = 48px

---

### Post by angel mike on 2023-09-08
I have set the cursor to DMZ-White in the Login Manager and clicked on Apply. In Settings - Accessibility have changed cursor size to Large which is ok. In Tweks have changed to DMZ-White. Cursor on login screen shows white but normal size.

---

### Post by Dennis N on 2023-09-08
> **angel mike said:**
> I have set the cursor to DMZ-White in the Login Manager and clicked on Apply. In Settings - Accessibility have changed cursor size to Large which is ok. In Tweks have changed to DMZ-White. Cursor on login screen shows white but normal size.

This is the normal behavior, and Login Settings Manager is working correctly. Sometime after Ubuntu 20.04, it seems much of the login screen settings (like the background color) were coded into gnome-shell so no user changes are possible. But we still can change the cursor theme with the Login Settings Manager. 

You want the login cursor to match the cursor you use after login. You can fix this with GIMP. You need to install it if you haven't already.

How to fix:

To check everything, I did another theme mod in an Ubuntu 20.04 virtual machine. I logged each step in the process. All is shown below.


```
Terminal:
dmn@Sydney-vm:~$ mkdir -p ~/work/new-theme
dmn@Sydney-vm:~$ cd /usr/share/icons
dmn@Sydney-vm:/usr/share/icons$ cp -r DMZ-White ~/work/new-theme/
dmn@Sydney-vm:/usr/share/icons$ cd ~/work/new-theme
dmn@Sydney-vm:~/work/new-theme$ mv DMZ-White Custom-DMZ

Start GIMP
Open ~/work/new-theme/Custom-DMZ/cursors/left_ptr

In layers dialog (right side) delete layers showing 32px and 24px
Save the result to the same directory. It saves as left_ptr.xcf
File > Export as:
choose file type as "X11 Mouse Cursor". Save to the same directory. A dialog asks for input:
Hot Spot: 16 8
Size: 48px
I also selected: "Replace the size of all frames.."
It saves as left_ptr.xmc

Done with GIMP

Return to Terminal
dmn@Sydney-vm:~/work/new-theme$ cd Custom-DMZ/cursors  
dmn@Sydney-vm:~/work/new-theme/Custom-DMZ/cursors$ cp left_ptr.xmc left_ptr

In text editor:
 
Edit ~/work/new-theme/Custom-DMZ/cursor.theme to be:
[Icon Theme]
Inherits=Custom-DMZ

Edit ~/work/new-theme/Custom-DMZ/index.theme to be:
[Icon Theme]
Name=Custom DMZ

Return to Terminal
dmn@Sydney-vm:~/work/new-theme/Custom-DMZ/cursors$ cd ~/work/new-theme
dmn@Sydney-vm:~/work/new-theme$ sudo cp -r Custom-DMZ /usr/share/icons/

Open "Login Settings Manager" and select Custom DMZ as the cursor theme.
Click "Apply" button.
Close

Logout and Login 
48px cursor is now in use on login screen.

```

Comment: In Ubuntu 20.04, I was also also able to change the background of the login screen with the Login Settings Manager. Can't do that in 22.04.

---

