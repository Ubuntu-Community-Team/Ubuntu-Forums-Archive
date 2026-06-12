---
title: "HOWTO: Xubuntu Hardy + Compiz + nvidia + dual-head"
date: 2008-05-08
forum: General Help
---

### Post by 01000111 on 2008-05-08
After my recent experience on trying to get this to work, I thought I'd supply a how-to for thems that wants it.  The following assumes that you already have a working dual-head setup, and want Compiz running with a cube on each monitor...

1. install nvidia-settings

2. sudo nvidia-settings
2a. change X server display config to Twinview
2b. set screen resolutions as necessary

3. reboot

4. sudo mousepad /etc/X11/xorg.conf
4a. make sure xinerama is set to false

5. use synaptic to install compiz and emerald

6. ccsm (aka Advanced Desktop Effects Settings)
6a. set General options, Desktop Size, Horizontal Virtual Size to the number of sides for the cube
6b. set Window Decorations, Command to "emerald"
6c. set Desktop Cube, Multi Output Mode to Multiple Cubes and enable Desktop Cube
6d. enable Rotate Cube

7. enjoy

The above gives you a cube on each monitor and when you perform a cube rotate, both cubes rotate at the same time.  If you leave Xinerama enabled, and don't use Twinview, you can get two cubes that you can rotate individually (a neat effect), but you can't move windows from one cube to the other.  If anyone knows how to have a cube on each monitor, so you can move windows from one cube to the other, and rotate them individually with separate keyboard combinations, LMK.

01000111

---

