---
title: "Videos and A Better GUI"
date: 2007-04-27
forum: General Help
---

### Post by GuitarRocker2562 on 2007-04-27
Well, I found out that the video part of videos won't play on my computer when running beryl or compiz (including the Desktop Effects in Preferences). When just using gnome, videos play fine. My question, how do I get a nice desktop environment and be able to play my videos (even vlc wont work right, and I am not using mplayer for ALL my videos)

---

### Post by fwojciec on 2007-04-27
Try using Xine for video playback.  On my laptop this is the only player that cooperates with Beryl (it's not perfect, but works).

---

### Post by Pox on 2007-04-27
Are you using straight Nvidia, AIGLX or XGL under the beryl?  I know AIGLX and XGL have some issues, but I'm on straight nvidia-glx-new and VLC, Mplayer, Totem, Xine all work fine for me.

---

### Post by GuitarRocker2562 on 2007-04-27
i don't have an nvida chip, i have a ?? (I read "Intel Graphics Media Accelerator 900"), it is an HP s7320n PC

---

### Post by fwojciec on 2007-04-27
I have a similar Intel card on my laptop so I think I know exactly what the problem you're describing is.  I haven't been able to resolve it completely.  On my laptop I can get the video to show in the window (using VLC or Movie Player) by moving the window slightly, sometimes I have to try a few times, but full screen playback never works with those players and Beryl on.  You can temporarily turn Beryl off to watch videos (switch to Metacity) - that's one solution.  

Another solution is to use Xine player (the package name is "gxine" I think - sorry I can't be more helpful with this, but I don't use it myself, since I don't watch movies on my laptop, but I did try it once and it worked.)  Xine seems to be pretty much unaffected by Beryl - there are some issues when you move or resize player window but overall it works quite well.

Neither solution is perfect, but you should be able to get it to work in either case.  If you ever want to buy another video card buy a nVidia card (you don't really need a very expensive model) - in my experience (I've tried Intel, ATI and nVidia) they work best in Linux.

---

