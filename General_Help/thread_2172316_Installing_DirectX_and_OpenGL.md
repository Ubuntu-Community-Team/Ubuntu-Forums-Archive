---
title: "Installing DirectX and OpenGL?"
date: 2013-09-04
forum: General Help
---

### Post by twinki2 on 2013-09-04
Is it possible to install DirectX and OpenGL that would work in browsers?

For example I need DirectX to play a browser MMO (Runescape.. I know)

I'm doing this on either Xubuntu or Lubuntu whichever will work correctly.. I tried to install DirectX with WINE but I'm not quite sure it worked and Dxdiag ended up not working and I totally just gave up and just installed a fresh version.

---

### Post by GwL3eNC on 2013-09-04
Hello twinki2,

if you want to play the game directly in the browser, i dont think there is much to do
to get it work. Just because it's a browser game. I saw on the runscape side
a client to download if you want to play over the desktop. This is for windows and
the winehp internet side tells about runscape works in wine. possibly it's easier
to use playonlinux in combination with wine

sudo apt-get install playonlinux

After install it has an icon in the menu. During install a new game with
playonlinux you can install much additional libraries like dx9,
dxconfig etc.

---

### Post by twinki2 on 2013-09-04
> **GwL3eNC said:**
> Hello twinki2,

if you want to play the game directly in the browser, i dont think there is much to do
to get it work. Just because it's a browser game. I saw on the runscape side
a client to download if you want to play over the desktop. This is for windows and
the winehp internet side tells about runscape works in wine. possibly it's easier
to use playonlinux in combination with wine

sudo apt-get install playonlinux

After install it has an icon in the menu. During install a new game with
playonlinux you can install much additional libraries like dx9,
dxconfig etc.


So is there no  way to get OpenGL or DirectX to work via browser?

---

### Post by GwL3eNC on 2013-09-04
hi,

i think you have a wrong imagination or i dont understand your intend. You only need to
install 

sudo apt-get install openjdk-7-jre icedtea-7-plugin

after i install that and restart firefox i was able to click on the play
button, register and create a player profile. You cant do what you mean, i think.

---

### Post by twinki2 on 2013-09-04
> **GwL3eNC said:**
> hi,

i think you have a wrong imagination or i dont understand your intend. You only need to
install 

sudo apt-get install openjdk-7-jre icedtea-7-plugin

after i install that and restart firefox i was able to click on the play
button, register and create a player profile. You cant do what you mean, i think.


I can load and play Runescape fine via browser... what I mean is that I have to play it in DirectX Mode, is there any way I can do that in browser? If not can I do it on the desktop client?

If I try to enter the OpenGL Mode or DirectX mode it says it's unable to enter that display mode, I have to be able to use DirectX or OpenGL for what i'm planning on doing (I'd rather not explain, just know that I have to be in either OpenGL Mode or DirectX in a browser :P)


EDIT: I got OpenGL to work in browser, and DirectX works on the desktop client, but is there any way to get DirectX to work on the browser?

---

