---
title: "Warcraft 3 loader"
date: 2007-09-06
forum: General Help
---

### Post by goffy59 on 2007-09-06
I suppose this is the wrong forum, but I wasn't sure where this would go. But before anyone suspects me as someone who downloaded Frozen Throne, I didn't. On windows I used daemon tools because my original Frozen Throne cd is scratched to the point where Blizzards securom protection doesnt detect the cd as being in the drive. Anyhow, I have images and I can install the game by burning these images. But it will not pass the securom test. So this lead me to a NO  CD loader, which I'm sure it works, but on linux it doesnt. To explain how this no cd crack works. When you connect to bnet, it checks if the game file is a certain size, so the crack must first load the game, and then rename it to to another name(the original), so by the time Securom asks for the cd it loads the NO CD crack and then goes back to the original so when you connect to bnet, it connects without a problem. I used wine to install warcraft 3( and the game runs fine except for this little problem; i tried it with a no cd crack but I cant play online because its an invalid version). And more evidence that I own it, I have my own cd keys which work fine. Anyhow, I want to see how it works. The .cmd file looks like this:
> FOR /F "skip=2 usebackq tokens=3 delims=	" %%i IN (`reg query "HKCU\Software\Blizzard Entertainment\Warcraft III" /v InstallPathX`) DO set InstallPathX=%%i

cd "%InstallPathX%"

ren "Frozen Throne.exe" Frozen_Throne.exe

ren war3.exe war3.121

ren war3_exe war3.exe

start /w Frozen_Throne.exe

ren war3.exe war3_exe

ren war3.121 war3.exe

ren Frozen_Throne.exe "Frozen Throne.exe"

I know NO CD cracks work in wine, but the way this loader works doesn't because it must read the registry and rename/change files around. I was looking for a bit of direction on how I could convert this .CMD to work on Linux, or find Linux commands that work the same so I can play online. My CD is damaged and the only thing I have our my images. In case anyone was wondering, this is for patch 1.21a. I heard you CANNOT burn securom 5 games because it has a special section of the CD that has a certain pattern. And I guess from what I've read, burning software cant copy this pattern. SO I used daemon-tools to emulate securom protection because my images do not have these special "sectors". Anyhow, please dont mistake me for a fool who downloaded it on bit torrent. I own this game and I have cd keys I use which are legitimate. I recently got into Ubuntu(and actually I REALLY LOVE it), and if I could get warcraft 3 working on here, I wouldn't need to boot back to windows. Diablo 2 works fine as well. I'm willing to do some research if someone would just point me in the right direction. I'm pretty good at following instructions people post on here (in fact I've solved nearly every problem I've had with Ubuntu because of all the nice people on here; thank you). Another shocking thing, is Ventrilo worked on Ubuntu(using wine), and every day I find even more reason to stay on Ubuntu. I don't play too much games, mainly Warcraft 3 TFT, DIablo 2, Battlefield 2 and currently bioshock(I go on windows for this, damn securom). I'm getting fed up with Microsoft now that Vista is out. Trying to force me to upgrade my computer for no reason what so ever. My CPU runs hotter on windows/vista (I'm dead serious), but thanks to Linux my CPU is used efficiently. I was looking at my Abit: 3rd eye display which shows information about my computer while its running.

---

### Post by cypherz on 2007-11-24
Hi,

I had same problem. I made this script for me. I hope it help.

```

cd ~/TransGaming_Drive/Program\ Files/Warcraft\ III
sudo ln -sf war3.exe.crk War3.exe
sudo cedega -gddb warcraft3frozenthrone.gddb Frozen\ Throne.exe -opengl
sudo sleep 3
sudo ln -sf war3.exe.org War3.exe

```

Like you can see, you must have in Warcraft III folder 'war3.exe.org' (original file) and 'war3.exe.crk' (patched file).

---

