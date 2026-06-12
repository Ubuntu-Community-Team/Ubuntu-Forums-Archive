---
title: "NEED HELP can't go pass the login screen"
date: 2015-04-08
forum: General Help
---

### Post by sebastiaan5 on 2015-04-08
When I boot up ubuntu I get to the login screen but when i entered my valid password my screen turns black for 0.5sec and I return again to the loginscreen and this keeps looping.

What have I done:

i entered the command: sudo su and then  startx

My screen went black after this for 10min so I tought I just restart my pc but sadly ubuntu won't work for me anymore.


greetz

---

### Post by sebastiaan5 on 2015-04-08
I needed to do this to fix:

sudo mv .Xauthority .XauthorityBak
sudo reboot


But i don't understand what happend, why did my screen looped? and what did this sudo mv command do?

---

### Post by Impavidus on 2015-04-08
Most likely your .Xauthority file had become owned by root. This may happen when you run graphical applications with sudo. To prevent this from happening, you have to run grapical application with root privileges using something like gksu, kdesu or pkexec, depending on your exact version and flavour of Ubuntu. I think sudo -h also works. See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for more details.

Because your .Xauthority was owned by root, your graphical session couldn't write to that file and subsequently failed to start, returning you to the login screen. The sudo mv command renamed your root-owned .Xauthority file to .XauthorityBak, so that on login new .Xauthority could be created and login succeeded. You can safely remove the old .Xauthority file (now named .XauthorityBak).

In fact, you don't need root permission to rename or remove a root-owned .Xauthority file, as long as you have write permission on the directory.

---

### Post by sebastiaan5 on 2015-04-08
thank you very much for your response :) I really want to learn Ubuntu and you taught me something :)

greetings,

Sebastiaan

---

