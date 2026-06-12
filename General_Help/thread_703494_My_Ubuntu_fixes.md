---
title: "My Ubuntu fixes"
date: 2008-02-21
forum: General Help
---

### Post by Eestlane on 2008-02-21
I hope this topic stays onforum
Here I try to list all the enhancements new install of Ubuntu 7.10 needs/needed in my system. Or lets say it, this is my road from total newbie to something else.

*EDIT: Use these only if you have problems. You are more likely in need of my second post in this thread.*

I have LiteOn monitor, that has support for 1280x1024 resolution, however is not natural in it. Best resolution for that monitor is 1024x768 instead.
So Ubuntu doesn't always care if I change the monitor resolution, as some parts will stay inaffected.
To fix most places, I needed to remove the wrong 1280x1024 from etc/X11.org
So I had new line i.e
```
Modes		"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
```

To fix boot up resolution, I got an answer from [Naman Zone blog post]("http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html"):
```
sudo gedit /etc/usplash.conf
```

Next, a very irritating malfunction of my mouse. My sidebuttons behaved like normal buttons, or god knows what.
So in X11.org I had to do the changes:
```
	#Change from mouse to evdev
	Driver		"evdev"
	#Change from mice to event3
	Option		"Device"	"/dev/input/event3"
	#Remove Emulate3Buttons maybe if added them before?
```

And also write in Terminal
```
xmodmap -e "pointer = 1 2 3 4 5 6 7 8 9 10"
```

Now I have only problem that i.e if I want @ mark I can use Alt Gr+2, but in the same time Ctrl+Alt+2 does not work.
I also added some clear fonts. And ofcourse themes etc, but fonts are really quite necessary, as I really don't like the "smooth" fonts.

Hope I didn't write it in the wrong place. Now I have a good place to look up if I want to fix my Ubuntu again after reinstall for example.

*I also have a problem of crashing Doom 3 Linux Demo for example at no exact period. It might be because (I think) my RAM is errorenous, I had done memtest86 test at Windows time, and still have the fault addresses, now I have to find out how can I add them to the boot ignore list in right format.*

So, what I think is that Ubuntu has come a long way of what it was, but really needs more work, which it probably gets. And I'm extremely happy that ATI(AMD) actually cares about Linux community and their drivers get better with every release, just like Ubuntu.

Good luck to all of you!

---

### Post by wPwLUi3N on 2008-03-28
That's pretty slick !!!

Its good share your fixes with other so they donot have to go through the suffering we faced ourselves.

---

### Post by Eestlane on 2009-05-05
More to add:

#Disable PC Speaker (the annoying beep). I actually recommend physically removing the contacts from the mainboard, 
# you can put these back anyway if you want to.

```
echo "blacklist pcspkr" | sudo tee -a /etc/modprobe.d/blacklist
sudo rmmod pcspkr
sudo modprobe -r pcspkr
```

#Change Copy and Paste shortcuts in terminal
Terminal: Edit->Keyboard Shortcuts... 
Copy Ctrl+C
Paste Ctrl+V

#Add mp3 etc support
```
sudo apt-get install ubuntu-restricted-extras
```
#Add Microsoft(non smooth) fonts
```
sudo apt-get install msttcorefonts
```
#Make fonts not smooth (Good for CRT monitor like I have)
```
wget http://www.osresources.com/files/centos-windows-fonts/fontconfig.tbz
sudo tar xvjpf fontconfig.tbz -C /etc/fonts/
```

/* Alternatives if last won't work:
[http://www.stchman.com/ms_fonts.html](http://www.stchman.com/ms_fonts.html)
[http://ubuntuforums.org/showthread.php?t=208396](http://ubuntuforums.org/showthread.php?t=208396)
*/


#Install my favourite browser (which sucks in Linux a bit, though)
```
sudo apt-get install opera
```

#Fix mouse sidebuttons in Opera for back/forward use
```
sudo gedit /usr/share/opera/ini/standard_mouse.ini
```

#For Opera 10 use
```
sudo gedit /usr/share/opera/ui/standard_mouse.ini
```

Change Button6 to Button8
Change Button7 to Button9

#Enable NetworkManager to support Internet Connection Sharing
```
sudo apt-get install dnsmasq-base
```

#Fix low volume by VIA DXS and other needed tracks in
```
sudo alsamixer
```


Now some stuff that are not essential, but might be useful when needed.

* If you've installed gparted and want to edit ntfs partitions, you need to install ntfsprogs (ntfs-config might be useful too if needed)
```
sudo apt-get install ntfsprogs
```

* If you've upgraded from GRUB Legacy to GRUB2 and for some reason can't edit grub.conf even with sudo, reassign the permissions:
```
sudo chmod 666 /boot/grub/grub.cfg
```

* Check free memory with
```
free -m
```

* In case you have some long and CPU (and/or memory) consuming process
running, that you would like to keep running but slower install cpulimit:
```
sudo apt-get install cpulimit
```

You can check processes with a GUI via gnome-system-monitor (and there View->All Processes). To limit a process use id or name. For example this code would limit process with id 5552 to use no more than 40% of CPU:
```
sudo cpulimit -p 5552 -l 40
```
Typing cpulimit is self-explanatory for more information how to use this command.

* Use **Ctrl+Z** in terminal to terminate the application started from the terminal. So you can return to the terminal without (closing and) opening a new tab. For example, if you want to let the 5552 process to continue in normal cpu, terminate the limiter with this shortcut.
EDIT: Mhmm, seems it doesn't really terminate it. Just removes from associating with the terminal.

---

### Post by cariboo on 2009-05-06
this thread doesn't really belong here, I'm going to move it to General Help.

---

