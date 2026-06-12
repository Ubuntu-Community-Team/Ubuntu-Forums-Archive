---
title: "Need help fatal error!!!"
date: 2008-05-25
forum: General Help
---

### Post by RussianRoulette on 2008-05-25
I just tried to install an snes emulator from the terminal and got an error half way through, saying “deb' is not known on line 56 in source list /etc/apt/sources.list' Then I went to add remove programs and got an error saying 'Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.'
can anyone help me?

---

### Post by joshsmith on 2008-05-25
hey,
then you need to check line 56 in source list /etc/apt/sources.list
open it by running
sudo gedit /etc/apt/sources.list in the terminal

you should spot that all lines look pretty similar (except lines starting with #) except for the 56th line, which because of some terminal command you have run is incorrect. go and delete the line, or change it to what is supposed to be if you have run some specific command and are expecting it to look like something. then run the update manager again


ps, you can get a snes emulator easily by installing the package zsnes or snes9x....  in synaptic

---

### Post by RussianRoulette on 2008-05-29
That worked thanks.




-RussianR-

---

