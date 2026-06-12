---
title: "Every time i log into ubuntu it logs me out again"
date: 2017-10-21
forum: General Help
---

### Post by johnstefnds on 2017-10-21
So when i try to log into ubuntu 17.04 gnome, the monitor blacks out for a few seconds and then i am logedout again... and when i try again to log in same happens.

All this started because i wanted to install vulkan and followed a guide where i had to install the latest nvidia drivers for linux manually... everything worked well but then i restastarted the computer and got into this loop...

I tried to remove nvidia drivers through the console but no resault.. i tried to add a new user and log in but again it automatically logs out (i can log in only in console with ctrl+alt+f2)

I tried all this askubuntu.com/questions/942810/ubuntu-logs-out-immediately-after-logging-in

But nothing....

There must be a way to fix this..

---

### Post by johnstefnds on 2017-10-21
Ok found the solution, as I said **in my particular case** the problem was "display related" (later on I realized it was driver related) since the problem started when I tried to update my Graphics driver which seemed to have been successful since I had video output and no issues after the installation but all the log-in problems described above  materialized after I restarted the computer.(also sorry for the typos I had to post this question from a cellphone [IMG]https://ubuntuforums.org/images/smilies/icon_razz.gif[/IMG] )

First I thought I would be ok simply by Ctrl +Alt + F2 and then log in the console and:


    ```
sudo apt-get remove nvidia-*
sudo apt-get autoremove
```

Thinking that nouveau or some default setting would take over which then would allow me to log in the gnome desktop but I was wrong (deleting the problematic driver was a good step though) 

Turns out that I needed to reinstall the nvidia drivers too, so I did that by:

    ```
sudo apt-get install nvidia-current
sudo apt-get update
sudo apt-get upgrade
```

Which doesn't update to the latest supported/tested version for ubuntu but I did not care to look into how to do that (probably instead of `-current` you type in the version number or you add the nvidia PPA but I wasn't sure about what the latest version available for ubuntu was nor what to type in for the nvidia PPA and did not want to research it since if this worked I could log in to my desktop and just graphically select the latest version from the Software & Updates manager which I did)

Then I pushed Ctrl + Alt + SysRq + R + E + I + S + U + B


(you have only to hold Ctrl + Alt + SysRq the others you can type in a serial manner one by one oh and SysRq is the print screen button in case your keyboard doesn't have both labels or a dedicated sysrq button last but not least not all of those commands (buttons) work if not previously enabled by you.. for more info about this go [here]("https://askubuntu.com/questions/11002/alt-sysrq-reisub-doesnt-reboot-my-laptop")
Also even if most of them dont work some of them should work like U,S and B which is better than nothing I guess and will safer restart your system - I was kinda afraid to just shutdown but it could also work without hanging anything I am a noob though so I did not want to leave it to chance :P - )

And everything works now :)

---

### Post by ajgreeny on 2017-10-21
Great news! Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

