---
title: "Some keyboard shortcuts has no effect when keyboard layout is not english."
date: 2015-02-07
forum: General Help
---

### Post by goghvv on 2015-02-07
Hi.
Why is it that when the keyboard layout is set to non-english (Hebrew), then some keyboard shortcut does not work?
For example, when I hit Ctrl+C or Ctrl+V it has no effect whatsoever. So whenever I want to copy-paste some hebrew text, I need to shift the keyboard layout to english, then hit Ctrl+C and Ctrl+V to copy-paste the text, then shift it back to hebrew keyboar layout to keep writing. That's really annoying.
In fact, looking at this [list of keyboard shortcuts]("https://help.ubuntu.com/community/KeyboardShortcuts") everything in that list works fine when the keyboard layout is hebrew _except_ the **Common Application shortcuts** described in this link.
Is it a known bug? Is it even a bug? maybe missing installation files?

I'm running Ubuntu 14.04.1 LTS.

---

### Post by Elad_Hen on 2015-03-01
I've just installed Lubuntu and I have the same problem (also with Hebrew). Keyboard shortcuts such as Ctrl-C and Ctrl-V don't work. Have you found a solution?

---

### Post by Elad_Hen on 2015-03-01
Ok, a good friend, and far more knowledgeable than myself in the world of linux, gave me the solution.


He says he thinks the way Lubuntu switches between languages is the source of the problem. 


He told me to run this command: 
[B]
setxkbmap -option grp:alt_shift_toggle "us,il"[/B]


Now everything works wonderfully. 


How can I help lubuntu fix this problem?

---

### Post by Elad_Hen on 2015-03-01
Of course, you should uninstall the Hebrew input method before doing this.

---

### Post by Elad_Hen on 2015-03-01
It  seems the solution I gave you isn't a permanent one. I've found  (with  the help of that friend) the method to make the change permanent  in  this discussion:  [http://askubuntu.com/questions/102344/switching-keyboard-layouts-in-lubuntu-11-10](http://askubuntu.com/questions/102344/switching-keyboard-layouts-in-lubuntu-11-10)  It's  a bit complicated but I'm copying it in hope that it will help others:   
1. Install the desired languages. 


$ gnome-language-selector 


2.  Create a shell script to execute setxkbmap after a delay and save  it  in a convenient place. Running it in the background may speed up the   login process. Increase sleep time if needed. Replace "us, il" with   your desired language codes. 


$ echo '(sleep 2; setxkbmap -option grp:alt_shift_toggle -layout "us,il") &' > ~/setxkbmap.sh 


3. Make the script executable and verify that it works by toggling the key combination Alt-Shift to switch language. 


$ chmod +x ~/setxkbmap.sh 
$ ~/setxkbmap.sh 


4. Create a .desktop file which executes the shell script just created. Replace "username" with your username. 


$ echo '[Desktop Entry] 
Type=Application 
Name=Keyboard Language Switcher 
Exec=/home/username/setxkbmap.sh 
Icon=/usr/share/lxkeymap/media/icon.png ' > ~/Desktop/setxkbmap.desktop
 
5. Logout and login again, then test by clicking on the new icon on your desktop, then toggling Alt-Shift.


6. Move the .desktop file to ~/.config/autostart 


$ mv ~/Desktop/setxkbmap.desktop ~/.config/autostart 


7. Logout and login again, then test by toggling Alt-Shift.

---

