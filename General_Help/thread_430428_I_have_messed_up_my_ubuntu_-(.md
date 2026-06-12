---
title: "I have messed up my ubuntu :-("
date: 2007-05-02
forum: General Help
---

### Post by Martinbr on 2007-05-02
I use ubuntu 7.04 and i have tried to instal the nvidia drivers and beryl using this code :

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup.beryl-script 
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup.beryl-script 
echo "deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main 
deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main" | sudo tee -a /etc/apt/sources.list 
wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add - 
sudo apt-get update 
sudo apt-get -y install beryl beryl-manager emerald-themes 
sudo nvidia-xconfig --add-argb-glx-visuals 
sudo cp /usr/share/applications/beryl-manager.desktop /etc/xdg/autostart/beryl-manager.desktop 
cp  /usr/share/applications/beryl-manager.desktop ~/Desktop/beryl-manager.desktop 
echo -e "Logout now and then press \e[0;31mCTRL+ALT+BACKSPACE\e[0m to restart xorg" 
echo "Installation completed !"


Now i only get a blank screen in ubuntu, and i cant do anything. Have i messed it up completly or can it be saved?

I am totally new to linux.

Hope someone can help.

Cheers
Martin

---

### Post by cisforcojo on 2007-05-02
Can definitely be saved. You'll need to pop in your Ubuntu CD and boot into 'rescue mode' it sounds like.
Do that and you'll only see text. Login as you would normally then type:

EDIT: Actually, I think you don't even need the CD. There should be a 'rescue mode' option in GRUB when you FIRST boot up your computer and select which OS you want.

```

sudo cp /etc/X11/xorg.conf.backup.beryl-script  /etc/X11/xorg.conf
sudo rm -rf /etc/xdg/autostart/beryl-manager.desktop
sudo rm -rf ~/Desktop/beryl-manager.desktop
 
```

Then Cntrl-Alt-Bksp to reboot, remove CD.

Try logging in. This should restore your computer to how it was before (but no Beryl)

---

### Post by Martinbr on 2007-05-02
Ahhhhhh.... Thx alot :-) 

Think ill stay away from beryl :-)

---

### Post by cisforcojo on 2007-05-02
Haha actually I recommend Beryl.
First make sure your nVidia drivers are working though. I'd just look for a different HOWTO.

---

