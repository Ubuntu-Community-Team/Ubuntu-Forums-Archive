---
title: "Where is the debian menu"
date: 2006-11-26
forum: General Help
---

### Post by telovoyagarcar on 2006-11-26
I read that the debian menu will show more of the applications installed.. 
i have installed "menu"... but the debian icon is not there next to the gnome menu panels like i want to... 
if i click Add to panel.. i dont have the option for the debian menu..
how do i put it there?

---

### Post by RAOF on 2006-11-26
The debian menu comes under the "applications" menu, but is disabled by default.  Right-clicking on "Applications" should get you an option to edit the menu.  Just tick the box next to "Debian" :).

---

### Post by telovoyagarcar on 2006-11-26
Ok thanks... i see it but i must to tick the checkbox and is not letting me do it... i guess because im not root... this starts to be a pain in the ***... everything i want to do needs to be root....

so the only way to do it is logging off then log on with root to make the change?

Thanks

---

### Post by RAOF on 2006-11-26
You shouldn't need to be root to do that - it's only affecting your user profile.  Aargh, I wish I knew a CLI way to do this - it's difficult to give help with a GUI :(.

I know it's difficult, but in what way is it "not letting you tick the checkbox"?  Is the Debian menu greyed out, or something?  Urgh.

You should be able to do it.  Maybe try fiddling around a bit in the menu-editor?

---

### Post by telovoyagarcar on 2006-11-26
look at the pic...
i can uncheck the ones already checked but i can not check any new one...
And i can not log on with root from the welcome screen...
it is crazy...
so how do i execute that menu option panel as root?...

anyone?

---

### Post by RAOF on 2006-11-26
Aaargh.  That's exactly what it looks like for me, except when I click on the checkbox it works!

I'll reiterate, though.  You **do not** want to try to mess with that as root.  Best case scenario: you change the menu for the root user only.  Worst case scenario: various files in your home directory get owned by root, you can no longer graphically log-on, and you need to run a **sudo chown *username* -R /home/*username*/*** to fix it.

As for the not being able to login as root: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by autocrosser on 2006-11-26
As I recall--there was more to making the debian menu work than just install menu--I'll look thru my info & post it---

---

### Post by autocrosser on 2006-11-26
Take a look at this post:  [http://www.ubuntuforums.org/showthread.php?t=288588](http://www.ubuntuforums.org/showthread.php?t=288588)

should be helpful;)

---

### Post by telovoyagarcar on 2006-11-26
ok..
i took a look in the list of processes and that panel is called "alacarte"

so i sudoed it in the CLI and works.. but still no able to check the boxes.. and when i do.. i get this error in the terminal window...

/var/lib/python-support/python2.4/gtk-2.0/bonobo/__init__.py: inconsistent use of tabs and spaces in indentation
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/Alacarte/DialogHandler.py", line 441, in on_menu_contents_changed
    self.saveMenu(self.menu_original_values, True)
  File "/usr/lib/python2.4/site-packages/Alacarte/DialogHandler.py", line 463, in saveMenu
    if path == values[0]:
IndexError: tuple index out of range
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/Alacarte/DialogHandler.py", line 441, in on_menu_contents_changed
    self.saveMenu(self.menu_original_values, True)
  File "/usr/lib/python2.4/site-packages/Alacarte/DialogHandler.py", line 463, in saveMenu
    if path == values[0]:
IndexError: tuple index out of range

---

### Post by RAOF on 2006-11-27
"alacarte" is the menu editor, yes.  You really shouldn't have used root - you should probably **sudo chown *username* -R /home/*username*/*** to make sure you still own the files in your home directory.

And, strangely, I also see this behaviour now.  What version of alacarte do you have (you can get this with **aptitude show alacarte**), and what Ubuntu version are you running?  I've got alacarte version: 0.10.1-0ubuntu1.  It might be time to file a bug on [launchpad.net](launchpad.net)

---

### Post by telovoyagarcar on 2006-11-27
Version: 0.10.1-0ubuntu1
Ubuntu Edgy..

ill check the links now..

thanks

---

