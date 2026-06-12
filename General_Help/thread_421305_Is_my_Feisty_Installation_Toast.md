---
title: "Is my Feisty Installation Toast?"
date: 2007-04-24
forum: General Help
---

### Post by Iokua on 2007-04-24
I installed Feisty the other day without any problems. Current configuration is dual boot with Windows XP on a desktop with no odd hardware requirements. Now I'm unable to boot into Ubuntu and I'm not really sure what's happened. Here's the story as best as I can figure:

[LIST]
[*]After initially installing Feisty, I decided to wait to install updates because the servers were overloaded. Otherwise, it worked fine. 

[*]I attempted to update last night. There were 120 available updates. 

[*]About half way through, it crashed, claiming an error that I did not make note of because I assumed the servers were still overloaded.

[*]To fix any broken packages, I attempted to run Synaptic, but it would not accept my password (although it worked perfectly two days ago.) It consistently said: "Incorrect Password" but I am absolutely positive that I have the correct password.

[*]So I then checked the forums for advice, logged into the terminal, ran apt-get -f install, apt-get check, and everything seemed fine.

[*]Next, I reverted to my Windows habits and decided to reboot in the hopes that something would change. Upon rebooting, I was able to log in but Gnome hung, giving me the error: "Unable to branch new process from terminal" or something like that. There was no desktop. Just a brown background with a blank, inaccessible, white terminal window. So I tried to access the terminal via Ctrl+Alt+F1, which then gave me the following error message ad infinitum: "bash: /dev/null: Permission denied." This message repeated until I rebooted.
[/LIST]

Any ideas on what's happened here?

---

### Post by phidia on 2007-04-24
Have you tried using your install cd "Recover a broken system" ?
Choose the partition that your ubuntu install is on and see if that will allow you to get into your install. Let us know what happens, and good luck.

---

### Post by Iokua on 2007-04-25
Just in case anyone cares, I was unable to salvage the installation. I have no idea what happened. I had to do a fresh install.

---

