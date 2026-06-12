---
title: "orange screen before and after splash during boot"
date: 2008-07-08
forum: General Help
---

### Post by mike-uk on 2008-07-08
Hi everyone,
I'm new to ubuntu having previously come from pclinuxos.
My problem is cosmetic. I have an automated login and when gdm starts up I first get an orange screen then a splash (with sound) then another blanc orange screen prior to the desktop.
Is it possible to fill all this time with something more in keeping with my wallpaper (a more consistent theme).
Does gdm have an equivalent to ksplash?
I've tried using kdm but ksplash doesn't work!
It's embarrassing when a friend sees it boot (hardly impressive).
Any solutions?
mike-uk

---

### Post by ajgreeny on 2008-07-08
Not sure about the orange screen before splash, if you mean the usplash with the increasingly long orange bar, but the screen after that before the gnome desktop shows can be changed by following this info.

sudo gedit /etc/gdm/PreSession/Default

look for
Code:

# Default value  
      if [ "x$BACKCOLOR" = "x" ]; then  
              BACKCOLOR="#dab082"  
      fi

and change the "#dab082" to "97A7CD" or whatever colour code you want.
Code:

# Default value  
      if [ "x$BACKCOLOR" = "x" ]; then  
              BACKCOLOR="#6093D5"  
      fi

You will need to know the colour code No. which you can get from various sources, including the Change Desktop Background window, and using the colour picker in that.  You can't, unfortunately, use a jpg or other picture.

---

### Post by sayakb on 2008-07-08
Simplest way is to goto System->Administration->Login Window
Click on **Local** tab and change the **Background Color.**

PS: But what ajgreeny advised is equally efficient.

EDIT: Install Ubuntu Tweak from getdeb.net 
Now open Applications->System Tools->Ubuntu Tweak. Expand **Startup** and click on **Session Control** and set a wallpaper sized splash screen from there.

---

### Post by evolving_monkey on 2008-07-08
Thank you ajgreeny. Changing this through Appearance does not seem to work. I altered the file in the way you recommended and it worked perfectly.

Thank you very much.

---

### Post by NLCarrII on 2008-07-08
[http://ubuntuforums.org/showthread.php?t=753261](http://ubuntuforums.org/showthread.php?t=753261)

That should help.

---

### Post by mike-uk on 2008-07-09
Many thanks everyone.
Thanks to  NLCarrII for pointing me in the right direction - problem solved!:)
Thanks to kirsis for providing a solution.
It would be nice to have some kind of animation (even if it's only something moving in a circle) in a future ubuntu.
Now the only thing missing (with regards to pclos) is a remaster that boots into my nvidia drivers.
This is not an attempt to start another thread (I have googled on this and there doesn't appear to be a solution), just an observation that I must keep pclos on the usb stick.:(
mike-uk

---

