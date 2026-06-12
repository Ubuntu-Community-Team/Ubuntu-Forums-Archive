---
title: "Invisible mouse on startup."
date: 2016-05-27
forum: General Help
---

### Post by brad48 on 2016-05-27
Hello all. Everytime I start up Ubuntu, I have an invisible mouse. I know it's there because I have a pop-up notifying me to upgrade to Ubuntu 15.10, and I can't hover over the buttons. 

I have a script that resets the mouse
```
sudo service lightdm restart
```
So all I'll need to do is Ctr+Alt+T and then run the script to restart lightdm and then my mouse re-appears after logging in. Unfortunately, lately when running this command sudo is not recognising my password. I can log in, I can switch (using ctr+alt+f1,2 etc.)  and log in that way, but running sudo from a terminal does not work and says my password isn't correct. 

Anyone know how to fix the issue of my invisible mouse? Sudo works just fine after managing to restart lightdm. (I do this by logging in using ctrl+alt+f1 or whatever then running the script from that console, as sudo works there).

---

