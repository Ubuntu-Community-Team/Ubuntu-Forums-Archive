---
title: "Changing boot animation"
date: 2015-05-25
forum: General Help
---

### Post by Ben_Shaver on 2015-05-25
Hello, as I'm a bit of a noob with Linux, and only recently figured out how to theme Ubuntu, I was wondering if it was possible to change the boot animation/splash screen (I think it's called?). To something like... This: [http://youtu.be/apx_HyxFqjA](http://youtu.be/apx_HyxFqjA)
its the first-boot animation from the Ubuntu edition XPS 13 Dell, I know adding something like this will prolong boot times, but hey, I could show it off to friends as something to brag about. ;) Any ideas or suggestions would be greatly appreciated, thanks in advance!

---

### Post by dino99 on 2015-05-25
plymouth (the booting splash) is deeply implemented and cant be themed

---

### Post by Dennis N on 2015-05-25
I would respectfully disagree that Plymouth can't be themed. There are many Plymouth themes available. I currently use one on Ubuntu 12.04 and Xubuntu 14.04. 

Where do you find them? In the Ubuntu repositories search for plymouth-theme and several will show up. The one called plymouth-theme-solar is the best looking one in there. More and better can be found if you go to gnome-look.org. In the categories on the left of their main page, look for "Splash Screens". 

I am using Earth-sunrise:  

[http://gnome-look.org/content/show.php/Earth+Sunrise+Plymouth+Theme?content=137171](http://gnome-look.org/content/show.php/Earth+Sunrise+Plymouth+Theme?content=137171)

Quite spectacular.

---

### Post by RobGoss on 2015-05-25
> **Dennis N said:**
> I would respectfully disagree that Plymouth can't be themed. There are many Plymouth themes available. I currently use one on Ubuntu 12.04 and Xubuntu 14.04. 

Where do you find them? In the Ubuntu repositories search for plymouth-theme and several will show up. The one called plymouth-theme-solar is the best looking one in there. More and better can be found if you go to gnome-look.org. In the categories on the left of their main page, look for "Splash Screens". 

I am using Earth-sunrise:  

[http://gnome-look.org/content/show.php/Earth+Sunrise+Plymouth+Theme?content=137171](http://gnome-look.org/content/show.php/Earth+Sunrise+Plymouth+Theme?content=137171)

Quite spectacular.


They looks amazing are they easy to install I would not mind installing one to see how it looks. thanks

---

### Post by Dennis N on 2015-05-25
> They looks amazing are they easy to install I would not mind installing one to see how it looks. thanks 

There is a README file inside the tar.gz archive of Earth-sunrise (you don't need the .deb)

In case you pick one without instructions, this is from that README:

> 
...extract the contents of the zip to your home or Desktop folder, then open a terminal and run this (firstly navigate to the folder where you extracted it using a terminal; if you extracted it on your Desktop, that would be: cd ~/Desktop):

```
sudo cp -R Earth-sunrise/ /lib/plymouth/themes/
sudo update-alternatives --install /lib/plymouth/themes/default.plymouth default.plymouth /lib/plymouth/themes/Earth-sunrise/Earth-sunrise.plymouth 100
sudo update-alternatives --config default.plymouth
sudo update-initramfs -u

```
Reboot and ready... should be running the new theme.


At step #3 in the quoted code, choose the number of the theme you want to use then hit enter.
Of course, if you choose a different theme, substitute its name in place of 'Earth-sunrise'

---

### Post by RobGoss on 2015-05-25
If you don't mind me asking how do you like the splash themes?

Question? I need to run those commands from my terminal?

I don't want to break anything..

---

### Post by Dennis N on 2015-05-25
> **robert159 said:**
> If you don't mind me asking how do you like the splash themes?
Question? I need to run those commands from my terminal?
I don't want to break anything..
The Earth-sunrise is excellent. It runs perfectly on the two systems I mentioned. But if it doesn't work well, or you choose not to use it, you can use the quoted steps #3 and #4 and return to the original Plymouth theme. Yes, all the quoted code is done in the terminal. You can copy and paste these lines, but as I said at the end, if you choose a different theme, be sure to substitute it's name for 'Earth-sunrise' in lines #1 and 2.

If you get it going, let us know.

---

### Post by RobGoss on 2015-05-25
I sure will thanks so much.

---

### Post by Ben_Shaver on 2015-05-26
While the rising sun animation is pretty amazing... Is it possible to use something like a video as a splash screen? (If so, how?)

---

### Post by Dennis N on 2015-05-26
> **Ben_Shaver said:**
> While the rising sun animation is pretty amazing... Is it possible to use something like a video as a splash screen? (If so, how?)

I've seen nothing that indicates that is possible at this time. If it were, it would be widely publicized. Thanks for the feedback that Earth-sunrise was a success.

---

### Post by Ben_Shaver on 2015-05-26
Well darn that sorta sucks, thanks for the help/answer. :) Bit of a random question, but do you know what folder the sunrise theme is in? I want to mess with it a bit, see how things work, etc.

---

### Post by Dennis N on 2015-05-26
All the theme files are in /lib/plymouth/themes/Earth-sunrise/
One customization that's easy: For my Xubuntu installation, I changed the **distro_name.png** to an xubuntu logo image that I located.
Have fun customizing.

---

