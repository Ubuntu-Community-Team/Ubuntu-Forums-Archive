---
title: "How is my After Format Basic Executable termial file + some questions about terminal"
date: 2008-06-26
forum: General Help
---

### Post by dinbrca on 2008-06-26
this is my basic after format termial file:
```

echo -n actions started at: && date
#Update Repositories
echo Updating Repositories
sudo apt-get update && sudo apt-get upgarde
clear

#Install VLC Media Player
echo -n Installing VLC Media Player- are you sure you want to install? [yes/no]
read install1
case $install1 in yes)
	sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc
esac
clear

#Install Amarok Music Player
echo -n Installing Amarok Music Player- are you sure you want to install? [yes/no]
read install2
case $install2 in yes)
	sudo apt-get install amarok
esac
clear

#Install MonoDevelop- C/C++/C#/Boo/Java/Nemerle/ILasm/ASP.NET Development Environment
echo -n Installing MonoDevelop- C/C++/C#/Boo/Java/Nemerle/ILasm/ASP.NET Development Environment- are you sure you want to install? [yes/no]
read install3
case $install3 in yes)
	sudo apt-get install monodevelop
esac
clear

#Install Some Good Games
##Install Tremulous
echo -n Installing Tremulous- Game- are you sure you want to install? [yes/no]
read install4
case $install4 in yes)
	sudo aptitude install tremulous tremulous-data
esac
clear
##Install XMoto
echo -n Installing XMoto- Game- are you sure you want to install? [yes/no]
read install5
case $install5 in yes)
	sudo apt-get install xmoto xmoto-data
esac
clear


#Shows What Was Installed
echo The Following Softwares And Games Had Been Installed:

echo Repositories Had Been Updated
case $install1 in yes)
	echo VLC Media Player Installed
esac
case $install2 in yes)
	echo Amarok Music Player Installed
esac
case $install3 in yes)
	echo MonoDevelop- C/C++/C#/Boo/Java/Nemerle/ILasm/ASP.NET Development Environment Installed
esac
case $install4 in yes)
	echo Tremulous- Game Installed
esac
case $install5 in yes)
	echo XMoto- Game Installed
esac
echo

#Linux BASH Commands Can Get From: http://www.ss64.com/bash/
echo Linux BASH Commands Can Get From: http://www.ss64.com/bash/
echo Enter exit To Quit Terminal
echo
echo
echo
echo -n actions stopped at: && date

```

How is it? (i am new to linux)

---

