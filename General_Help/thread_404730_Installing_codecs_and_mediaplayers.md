---
title: "Installing codecs and mediaplayers?"
date: 2007-04-08
forum: General Help
---

### Post by Mixy on 2007-04-08
Hi

I just installed Ubuntu for the first time. Edgy eft, 6.10. Altho this is first time Ubuntu, i've tested other Linux distros before, so i am not a total noob.

Okey, first i am trying to get divx/xvid/x264 codecs to work, and i searched the forum. I wanna install VLC, but it is not i my repos. Neither is mplayer. I searched the forum, wich said it should be in the repo :P Okey, so i continue looking, and found somewhere it said that i should go into synaptic ->Settings-> Repositories and then click add. Or something like that. The thing i dont understand tho, is that when i go there (repo settings), there is nothing there that says add. I've added a repo before (ntfs-3g), but there i had a link, and worked my way around. To add that, i also followed a guide full of screenshots, but the repo window looked nothing like the one i am in.

If there is anyone that can help me, i'd be grateful :)

---

### Post by Maestro23 on 2007-04-08
These links will help.  You need to enable all your repositories(Manging repo link).  For your codecs(Restricted format link)


Useful Links:

Installing Software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)

Restricted Formats(mp3, playing DVD, etc..): [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Managing Repositories: [https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)

Community Docs: [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

CommandLine Beginners: [http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

Basic Commands: [https://help.ubuntu.com/community/BasicCommands](https://help.ubuntu.com/community/BasicCommands)

LinuxCommand.org(Commands & Linux File Structure): [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Graphic Card Drivers
ATI supported cards: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti)
Installing ATI Drivers: [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)
Installing Nvidia Drivers:[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)
Envy Script(ATI/Nvidia): [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Super Grub Disk: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by bulldog on 2007-04-08
Type ```
gksudo gedit /etc/apt/sources.list
``` in a terminal.
This will open your sources.list and you can change it.
 Now uncomment  [remove the #] in front of lines with Universe and Multiverse and safe the file.

Type in your terminal```
sudo aptitude update && sudo aptitude upgrade
``` to reload the repositories.
Now open synaptics and type mplayer and/or vlc in the search box.

It should be there :)

---

### Post by Mixy on 2007-04-09
Great :) Got both codecs and mediaplayers working now. Plus fglrx ;) All that remains now is xgl and beryl ;)

---

