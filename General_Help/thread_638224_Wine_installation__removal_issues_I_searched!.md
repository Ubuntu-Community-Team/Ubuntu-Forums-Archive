---
title: "Wine installation / removal issues I searched!"
date: 2007-12-11
forum: General Help
---

### Post by Mular on 2007-12-11
Hello.. having a problem here..

Basically I installed wine via the Synaptic Manager, decided on removing it because I was having some issues in it (no sound in desktop and odd performance) So I uninstalled it through the manager and I noticed under application that it was still showing as installed.
Anyways again I tried to then reinstall wine, seemed to work ok but the menu icon never "refreshed" it no longer showed cfg wine.. 

So I uninstalled it again through the manager. Then did a search on how to remove it fully, read about sudo aptitude purge wine.. Tried that still didn't completely get rid of it. Then one post said to delete the .wine dir. So I did rm -r .wine and then it was all gone.. Still had the stupid application menus though!

So another post said to get rid of them you go into /home/.config/menus and in there is a config you can edit, did that - still the program was there.. Then I looked over the config and saw you could go to /etc/xdg/menus and then under merged applications I found that stupid wine-wine entry.. Deleted that and now its all completely gone..

Problem is I really want wine to install right, how do I get it to install with the applications menu intact? Really want to access wine cfg! Also once its install I can do in the command line wine help - and then it creates some directories, and then says error something about C://windows/help not found, then the same for wine version..

So somethings not right.. am I missing something here? Maybe I still didn't complete remove it from my system? 
Thanks for the help guys!

Mular

---

### Post by Mular on 2007-12-11
Ok So I fixed my own issue just incase anyone is trying to figure out the same thing..

When you reinstall Wine I guess its a known bug that you no longer get the menus properly.. So I just made my own..

Right click on Applications, go down to edit menu. From there go to wine, and click new item, then what was important to me was the winecfg command.. Put that in and atleast you can get that window up.

Also as soon as you install something new it will install wine > programs >newly installed program on your Application Menu ;0

---

