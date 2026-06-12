---
title: "Shell Script Will Not Open With Terminal 14.04.3"
date: 2015-11-08
forum: General Help
---

### Post by coljohnhannibalsmith on 2015-11-08
Hello,

I have a shell script that automates changing both of my MAC addresses. Prior to the last update, it would ask if I wanted it to "run in terminal or display." Normally, I would click on "run in terminal" and it would do that. Now it just opens with GEdit; and when I try to get it to open with terminal, that option is not available.

How can I get this script working again?

Thanks, Hannibal

---

### Post by Lars Noodén on 2015-11-08
I'm not sure of the easy way.  The hard way is to make a .desktop file for it: [https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles)
I notice I have a few of them now, but hopefully someone has an easier way.

---

### Post by brian-mccumber on 2015-11-08
Open a terminal and navigate to the directory that the script is in then execute it by using ./scriptNameHere.sh. You may have to use chmod +x scriptNameHere.sh to get permission for it to run.
[ATTACH=CONFIG]265416[/ATTACH]

I use a program called open in terminal that allows me to right click the file browser window and open that directory in the terminal directly.
[http://askubuntu.com/questions/207442/how-to-add-open-terminal-here-to-nautilus-context-menu](http://askubuntu.com/questions/207442/how-to-add-open-terminal-here-to-nautilus-context-menu)

---

### Post by ajgreeny on 2015-11-08
Is the script executable if you choose properties from a right click in nautilus, and in the nautilus preferences do you have "Ask" as the chosen behaviour when you click on shell scripts?

---

### Post by brian-mccumber on 2015-11-08
It has been my experience that shell scripts do not run when trying to use Run Software from right clicking the script and choosing open with Run Software, unless the script uses a gui. I have always had to use the terminal to get them to run. Unless it's a shell script that runs other programs, then a .desktop calling that script works, or making a .desktop for your script will also run it.

---

### Post by brian-mccumber on 2015-11-08
I have even went so far as to put a copy of my script in the root/usr/bin folder and creating a .desktop for it so I can run it from my launcher. If you copy it to there you still have to set it's permissions using chmod. Here is a code sample of a .desktop file that I made for a script I wrote that I installed into user/bin. The only successful way I have gotten .desktop files to open in gedit so I can edit them is to drag and drop them into the text editor from the file browser.

```

[Desktop Entry]
Version=2.3
Name=modStat
Comment=Check modem data resources
Exec=/usr/bin/modStat
Icon=/home/brian/.icons/HughesNet_logo.png
Terminal=true
Type=Application
Categories=Utility;Application;
Name[en_US]=Hughesnet Status

```

Also after putting my script into usr/bin, I can open a terminal and type in the script name and it will run while I am in any directory with the terminal.

---

### Post by ajgreeny on 2015-11-08
Rather than putting it in the root system files such as /usr/bin you can make a folder in your home called /bin, which is included in the default $PATH if it exists, and run it from there with just its name, as if it were in /usr/bin.

---

### Post by coljohnhannibalsmith on 2015-11-11
> **ajgreeny said:**
> Is the script executable if you choose properties from a right click in nautilus, and in the nautilus preferences do you have "Ask" as the chosen behaviour when you click on shell scripts?

For some reason "Ask each time" was not set. I set it; and now it runs properly.

Gentlemen, the .desktop suggestion was also very useful. this never even occurred to me. Now, I have two ways to do it.

Thanks, Hannibal

---

### Post by coljohnhannibalsmith on 2015-11-11
BTW, this script runs fine on my DELL 5520 i7; but on my DELL 1545 Pent5, the ethernet MAC Changes; but the WiFi MAC will not. I have networking completely disabled when I run this script.

---

