---
title: "ls won't list - starting with &quot;Projects&quot; folder"
date: 2019-11-08
forum: General Help
---

### Post by anneranch on 2019-11-08
I am trying to access a folder to execute "make" in it. 

I can list the folders under "DOC_COPY_LABEL , including "Projects" just fine.

however  this fails 

z@z-desktop:/media/z/DOC_COPY_LABEL$ cd Projects



I have no problem using application "Files" - it list desired folder contents just fine.

What is going on? 
Do I have some nonpritable character(s) in "Projects" folder ?
( I did checked spelling etc. ) 
Can I run "make" in desired folder using other then terminal ?

I can copy properties ( path) of desired folder into terminal ( ls path...) and it still fails. 


Only "Projects" folder is failing this way. 

 
```
z@z-desktop:~$ cd /media/z

z@z-desktop:/media/z$ ls
0822C8912019FFC8  DOC_COPY_LABEL  MISC_COPY        Programs
Alternate downlo  DOCMD0          MISC_COPY_LABEL  REsume
BACK              Eclipse         OpenCameraB      WorkspaceRaspber
BACK_COPY_LABEL   EOS_DIGITAL     Photo Album
DEV_COPY_LABEL    Ex Drive Co     Photo Album1

z@z-desktop:/media/z$ cd DOC_COPY_LABEL

z@z-desktop:/media/z/DOC_COPY_LABEL$ ls
Bell_Tower.odt            NanoVNA                   SPITFT.odt
Bluetooth                 NanoVNA_Q                 TODO_710_BACKUP.odt
Bluetooth.odt             New (DEV_COPY) Documents  TODO_710.odt
BT_VNA.odt                OneTouch                  TODO_911_1.odt
Documents                 OpenGL.odt                TODO_911.odt
eclipse-workspace         Projects                  TODO.odt
eclipse-workspace_BACKUP  Projects_COPY             Transistor
IOCTL.odt                 Python                    Transistor.odt
JS8Call                   RegenenRX                 Video
lost+found                RX.odt
LTSpice                   SPITFT_COPY.odt

z@z-desktop:/media/z/DOC_COPY_LABEL$ cd Projects
bash: cd: Projects: No such file or directory

z@z-desktop:/media/z/DOC_COPY_LABEL$ cd Projects
bash: cd: Projects: No such file or directory
```

---

### Post by uRock on 2019-11-08
You have two folders starting with the name Projects. 

Try this,
```
cd Projects/
```

---

### Post by Bashing-om on 2019-11-08
anneranch; Hello -

It appears to me that the target "Projects" is not in the view of the '(P)resent )W)orking (D)irectory'.

What shows:
```
 
sudo find / -iname Projects -type d

```

where we establish the path to that target.

[INDENT][INDENT]there is that "path" that seems right, but ....
[/INDENT][/INDENT]

---

### Post by uRock on 2019-11-08
It's there, bash just needs more input due to the matching folder names. I have multiple Desktop folders in the drive below, but only one that is just Desktop, which causes this;
```
uRock@OxfordComma:~$ cd /media/uRock/Old\ Home/Dekstop
bash: cd: /media/uRock/Old Home/Dekstop: No such file or directory
uRock@OxfordComma:~$ cd /media/uRock/Old\ Home/Desktop/
uRock@OxfordComma:/media/uRock/Old Home/Desktop$ 

```

---

### Post by anneranch on 2019-11-08
SOLVED
used ls -b to identify non printing character "\" 
and just guessed and added space after

---

