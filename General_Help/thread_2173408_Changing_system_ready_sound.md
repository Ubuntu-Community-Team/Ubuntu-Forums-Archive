---
title: "Changing system ready sound"
date: 2013-09-09
forum: General Help
---

### Post by feremtpc on 2013-09-09
**[IMG]http://ubuntuforums.org/images/icons/icon9.png[/IMG] Help!!   System ready sound**

 		 				 					 					 				 				 		 			 				[INDENT]  					So I am Trying to personalize my laptop.... I am using ubuntu   13.04, I tried to change the system ready drums "conga" sound. this is   what I did.
1. convert my own .mp3 file to a .ogg file and name it system-ready.ogg.
2. I opened /usr/share/sounds/ubuntu/stereo as root and replaced the   file that was there with mine, but the sound is not playing for system   ready.
I looked into trash to restore the other file but I cannot find it   anymore, because I read later that this was just linked to   dialog-question.ogg, so I guess the system ready sound commando is just   not being told to the computer.
How do I configure so I can have my computer play the system-ready.ogg file I put in the folder,
I have play system ready enabled in dcong-editor com.canonical.unity-greeter.

thanks. 				
[/INDENT]

---

### Post by R8FQCHC on 2013-10-07
I would also like some help on this issue for 13.04...

I tried an alternative method (which also didn't work):
[LIST]
[*]Create a custom sound theme "CustomSounds" in /usr/share/sounds, including a system-ready.ogg file
[*]Select the theme for my user by dconf-editor (org/desktop/gnome/sound/theme-name = CustomSounds)
[*]Select the theme for the lightdm user by dconf-editor  (using the code below to run dconf-editor as lightdm - the same method I  have used successfully to set the unity greeter background and some  other settings)
[/LIST]

I have the customised sounds, but unity greeter still plays the default  system ready drums! Perhaps my .ogg violates some constraint somewhere? I  can't see why though - it's plenty short and etc... Is the system-ready  sound played by some other user perhaps?

Any help appreciated!

Running dconf-editor as lightdm:
```
me@box:~# sudo -i # Escalate to root
root@box:~# xhost +SI:localuser:lightdm # Allow lightdm to use the X Server
root@box:~# su lightdm -s /bin/bash # Masquerade as lightdm user
lightdm@box:~# dconf-editor
```
...Don't forget to clean up afterwards:
```
lightdm@box:~# exit
root@box:~# xhost -SI:localuser:lightdm # Revoke lightdm privileges
root@box:~# exit # Drop back to my user
```

---

