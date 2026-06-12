---
title: "Simply GNOME"
date: 2014-03-21
forum: General Help
---

### Post by sosaudio1 on 2014-03-21
Here is the background.....I simply want a box that is just toooooo simple. I am making an HTPC based on XBMC. I only want a GUI desktop with the basics. I don't need anything but that. I followed this guide here: [http://askubuntu.com/questions/320903/usb-drive-with-stripped-down-ubuntu]("http://askubuntu.com/questions/320903/usb-drive-with-stripped-down-ubuntu") to a T but when I did apt-get install GNOME, well, you guessed it. I have the FULL install of GNOME. I just want to pick and choose what I install. Even if I select XBMC and it pulls every drop of deps to run it, I am cool with that. I just want a stripped down environment that is more of an appliance than a DE. 

Did research: XBMCbuntu? Nope, the 64 bit version that stood out is for 13 the latest version. Already tried and some of my plugins would not work with it.
                   Why Not XFCE? I think XBMC is not playing well with Thunar because I kept getting install errors. At one point using another stripped down version of Ubuntu, it said that my xbmc folder had permission problems....this was the home files.....looking at the home folder, it said that the owner was root.....yuck....user should have been owner of folder not root inside of home. So I think there were probably perm errors running thru that. I like Nautilus, I have proven it to work better time and time again....just more robust I guess.
                    Why not OpenELEC? Love it, can't run it. I have IDE drives playing off of a card installed in the box. OE can't find them.

Sooooooo we are here


I simply want something that plays well with synaptic, just installs enough to give me a GUI and lets me use Synaptic or even APT-GET to install synaptic to just get the most light, basic basic basic system I can get away with.

Any ideas on which way to go? I don't mind reformatting and reinstalling if need be but my basics are GNOME, Nautilus, Ubuntu, Synaptic with deb pkg install capability, no compiz in fact, no compositing, nvidia drivers 


On your mark, get set, GO!

Thanks everyone
Rich

---

### Post by ibjsb4 on 2014-03-24
I have no experience with XBMC, but a way to get nautilus.

Try this combo:

```
sudo apt-get install --no-install-recommends gnome-session-fallback nautilus

```
With a DM or startx.

Fall back to tty to add more

This is for 12.04

---

