---
title: "Very odd and annoying graphics problem"
date: 2013-06-12
forum: General Help
---

### Post by katyMarshal on 2013-06-12
Dear Ubuntu experts,

I am having a strange graphics issue especially with menus. The problems is seen only when working with menus where black of dotting marks appear on menus. Images below are examples while working on Lyx. Notice the black background and marks; these are random and change to something else every time. The same problem is reproducible on Firefox, Gimp etc.. I am using Ubuntu 13.04 (clean install) and never seen this problem on Ubuntu 12.10. My graphics card is Mobile Intel® GM45. by using the the command: dpkg -l | grep xorg-video
I can see that xserver-xorg-video-intel  is installed on my machine so I am assuming no problem with my graphics card. To make sure no problem with xorg I did:

sudo apt-get remove --purge xserver-xorg
sudo apt-get install xserver-xorg
sudo dpkg-reconfigure xserver-xorg

and 

sudo apt-add-repository ppa:andrikos/ppa

then

sudo apt-get update
sudo apt-get upgrade

However, non of that solved the problem.


Please help...........


[ATTACH=CONFIG]243752[/ATTACH][ATTACH=CONFIG]243753[/ATTACH][ATTACH=CONFIG]243754[/ATTACH][ATTACH=CONFIG]243755[/ATTACH][ATTACH=CONFIG]243756[/ATTACH]

---

