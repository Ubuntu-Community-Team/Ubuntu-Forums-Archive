---
title: "Need Help With Audio/video"
date: 2006-10-13
forum: General Help
---

### Post by EntenduEtOublie on 2006-10-13
So uhh I just installed Unbuntu Linux today and I've been playing with it all day and cant get my videocard or my soundcard to work properly... I have a Nvidia GeForce something or other and a Soundblaster X-Fi and neither are working properly so if somebody out there could help me out, I'm completely linux retarded thanks

---

### Post by pay on 2006-10-13
What are the problems with thw videocard? Are you getting a graphical login or is it text based? I can't really help with the soundcard.

---

### Post by Rhubarb on 2006-10-13
I think your x-fi sound card is heavily software defined, and I doubt very much that creative would make linux drivers for it (in my opinion creative have always been poor at making software).
I could be wrong here, but I doubt if you'd be able to get your sound card working.

To get your 3d video drivers working is easy:
Start up synaptic (it's in the menus somewhere, administration?).
Make sure the extra repositories are enabled (search the forums here if you need help doing this).
In synaptic do a search for "nvidia-glx".  Install it.
Then you'll need to edit a text file, in a terminal type in:
```
sudo gedit /etc/X11/xorg.conf
```
Then you'll need to find the nvidia part in the text file.
Find the line that ends with "nv", and change it to "nvidia".
Save and close, then reboot your pc.

I probably haven't explained it too well here, there are much clearer concise instructions to do this here in the forums.

Could you please explain a little more about exactly what problems you are having with your video?

---

### Post by EntenduEtOublie on 2006-10-13
well I used to running 1600x1200 and it wont go higher than 1024x768 and just the graphics on some websites arnt loading at all so I'm pretty sure that it doesnt have the right driver... and it's whatever Dell uses for their GeForce

---

### Post by EntenduEtOublie on 2006-10-13
and when I ran that last command it said cannot open display(null) and told me to run the gedit--help to find the right command

---

### Post by galileon on 2006-10-13
make sure you install the nvidia-glx package as Rhubarb explained above,

then open a terminal (Applications>Accesories>Terminal)
type this:

sudo dpkg-reconfigure xserver-xorg -fgnome

it will give u a graphical configuration tool....

---

### Post by galileon on 2006-10-13
[http://opensource.creative.com/soundcard.html](http://opensource.creative.com/soundcard.html)

no drivers anytime soon... :(

---

