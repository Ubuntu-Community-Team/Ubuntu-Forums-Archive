---
title: "Screen resolution"
date: 2006-10-17
forum: General Help
---

### Post by ivanp on 2006-10-17
Hi everyone,

my screen resolution is not as wide as i use to have in windows mode. how can i set for a **higer resolution and definition**? where do i find what's the video controller?

regards

Ivan

---

### Post by Kateikyoushi on 2006-10-17
If you are using ubuntu (the gnome desktop manager) you can change it in System >> Preferences >> Screen resolution.

The command "lspci" will list your video controller, type it to a terminal.

In case you can't find the right resolution you are looking for copy this to a terinal to reconfigure x.

Create a backup first
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

Then reconfigure the x server
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by ivanp on 2006-10-17
I wento thru a configuration process that ended by restarting the xserver, but when it was running again it still didn't show any higher resolution than 1024x768 

i have added the 1152x864 option to the xorg.conf but still can't get it to work in higher resolution

---

### Post by Kateikyoushi on 2006-10-17
What is your video controller ?

---

### Post by ivanp on 2006-10-18
is an onboard video chip

the motherboard is **Intel 82801db**

---

### Post by Kateikyoushi on 2006-10-18
You can list your devices with the following command.
```
lspci
```

If the display controller is an Intel 800 or 900 series (Intel 845G, 855G, 865G, 915G, 915GM, and 945G), there is a very easy solution to fix this.

Copy this to terminal.
```
sudo aptitude install 915resolution
```

After it is installed reboot or restart X.

---

### Post by ivanp on 2006-10-19
i run the command and it showed there was an error and the instructions to fix it

i changed the
mode=38

xresol=1280
yresol=1024

bit=32

in 915resolution/default or somethimg like that and restarted

then i had to put that resolution in the xorg.conf and when restarted ubuntu so the changes take effect, while loading i had a fail message in the pcmcia loader and never again i saw the screen. it just stays black

how do i go back to the previous state or fixit by command in a textmode tty?

---

### Post by bigken on 2006-10-19
boot into single use mode and run the sudo dpkg-reconfigure xserver-xorg
command use the space bar to select your desired resolution sizes ;)

---

### Post by ivanp on 2006-10-19
i have started in the recovery mode. i tried to run the dpkg-reconfigure xserver-org command and got

/usr/sbin/dpkg-reconfigure xserver-org is not installed

as answer.

i have started the xserver in the recovery mode and it does start, but in english, i had it in spanish, and with the new resolution working just great. i restarted the pc but in normal mode again i run out of screen and the pcmcia services failed message keeps showing at start up

any ideas?

---

