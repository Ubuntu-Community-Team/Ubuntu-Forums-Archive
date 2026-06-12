---
title: "HPLIP Install Files in Wrong Place?"
date: 2016-06-19
forum: General Help
---

### Post by Quarkrad on 2016-06-19
Running Mate 16.04.   Installed hplip many times with various ubuntu versions and different printers. Downloaded hplip 3.16.5 to Downloads folder, opened terminal and cd Downloads.   Once in Downloads run sh hplip-3.16.5.run and followed instructions (as usual).  hplip has installed all its files into my Downloads folder - surely, this isn't right?

---

### Post by ajgreeny on 2016-06-19
> **Quarkrad said:**
> Running Mate 16.04.   Installed hplip many times with various ubuntu versions and different printers. Downloaded hplip 3.16.5 to Downloads folder, opened terminal and cd Downloads.   Once in Downloads run sh hplip-3.16.5.run and followed instructions (as usual).  hplip has installed all its files into my Downloads folder - surely, this isn't right?
Are you sure?

When you used the run command the system first unpacks everything to a folder in your Downloads folder called hplip-3.16.5 and installs the real program into /usr/share.

I think you can even remove the hplip-3.16.5 from Downloads and things will still work, though I've never tried that before.  I am trying it out now and will report back tomorrow after a reboot to thoroughly test it.

Run ```
locate hplip
``` in terminal and you'll see a huge list of the 3500 approx files in your home and then all the others in /usr/share

---

### Post by ajgreeny on 2016-06-20
I have just tested my theory about removing that Downloads/hplip-3.16.5 folder, and I was correct; removing it does not stop hplip, nor the HP Device Manager from working.

---

### Post by Quarkrad on 2016-06-22
You are right - I ran the command and all the files are in usr/share.  I deleted all the files and reinstalled hplip - looking at detail, rather than watching the terminal commands casually, I can see the problem - but do not know how to fix it.   hplip3.png shows my Downloads folder full of the install files BUT hplip.odt shows I have permission issues.  I'm guessing because of this permission issue the install just installs in the directory where it sits - i.e. Downloads.  Can you help re my permissions problem?

---

### Post by ajgreeny on 2016-06-22
As regards the permissions problem I do not really understand what you mean.
Which files did you delete; the hplip-3.16.5 folder in you Downloads folder, or all those in /usr/share?

---

### Post by X-RED_Tech on 2016-06-22
The only few times I needed HPLIP it was already installed or I installed it from the official repositories. Never tried downloading it from HP.

That said, in this case shouldn't the script be run with sudo? It would otherwise require elevated privileges in order to put files in system folder, would it? Did the installer (script) asked for the sudo password at any point? If not I don't see how it could have been installed correctly.

---

### Post by Quarkrad on 2016-06-23
In my text file hplip.odt (#4) - at the beginning of the install process there are a number of entries including **chown: cannot read directory './hp dump/hplip-3.16.5': Permission denied**.  I once again deleted everything (files from Downloads, /etc/ and /usr) and reinstalled using the following: **cd /Downloads** followed by  **sudo chmod +x hplip-3.16.5.run** followed by  **./hplip-3.16.5.run**.  Now it all works and I do not have all the install files in my Downloads folder.  Having said all this - I have not had to do this before.  (Source [https://sites.google.com/site/tipsandtricksforubuntu/printer-info/hplip-driver](https://sites.google.com/site/tipsandtricksforubuntu/printer-info/hplip-driver)).

---

### Post by ajgreeny on 2016-06-23
> **X-RED_Tech said:**
> The only few times I needed HPLIP it was already installed or I installed it from the official repositories. Never tried downloading it from HP.

That said, in this case shouldn't the script be run with sudo? It would otherwise require elevated privileges in order to put files in system folder, would it? Did the installer (script) asked for the sudo password at any point? If not I don't see how it could have been installed correctly.
Usually that is the best answer but if you have a newer printer that is not supported by the repository version of hplip you have to download  it as Quarkrad did and run the hplip-3.16.5.run in terminal.  You do not run it as root using sudo however, as the script asks you to raise your permissions with your user-password at the appropriate time.  It is very easy to install that way; it just takes a bit longer than using the repos version.

---

