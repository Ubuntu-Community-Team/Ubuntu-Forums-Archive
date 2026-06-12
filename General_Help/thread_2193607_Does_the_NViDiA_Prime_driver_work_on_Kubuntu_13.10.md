---
title: "Does the NViDiA Prime driver work on Kubuntu 13.10?"
date: 2013-12-13
forum: General Help
---

### Post by gfran on 2013-12-13
Has anybody had any experince in attempting to install the Nvidia Prime Optimus driver in Kubuntu 13.10? If so, do you have any installation instructions? Kind Regards

---

### Post by efflandt on 2013-12-13
"Attempting" to install **nvidia-prime** in 64-bit regular Ubuntu 13.10 resulted in a dialog during boot about a graphics issue with a dialog asking if I wanted to reconfigure X or use low graphics mode. However, that dialog was totally unresponsive, so I had to switch to a vt and log in to purge nvidia-prime. I have not had a chance to look for current information yet on nvidia-prime, and even primusrun does not work for graphics (only primusrun glxinfo). Not sure if I need a specific nvidia driver version for primusrun or nvidia-prime or some configuration (Intel HD 4600/Nvidia GTX 765M).

I have been using nvidia-experimental-310 (actually 319.60 last time I checked) and so far optirun seems to work well enough for what I need, once I figured out optirun launch parameters for steam games (I just use Intel for steam itself).

---

### Post by gfran on 2013-12-22
I am answering my own question to say that The nvidia prime driver DOES work in Kubuntu 13.10. I have it installed and it works perfectly. I followed the following instructions [http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)

---

