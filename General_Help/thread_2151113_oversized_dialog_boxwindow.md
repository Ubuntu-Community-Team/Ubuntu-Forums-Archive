---
title: "oversized dialog box/window"
date: 2013-06-03
forum: General Help
---

### Post by sidewalkcynic on 2013-06-03
The application is KDE Baskets. It is a note taking application, and when i make a new note the dialog box islarger than the screen and I have to use the (Alt) key to grab and move the box to use it, and this is very time consuming, because i have to make a lot of notes that use the dialog. I have tried to adjust the numbers that i have found in the rc file, but I have not found the solution - does anybody have any ideas?
```
[Cross Reference Look]
bold=false
color=invalid
hoverColor=invalid
iconSize=16
italic=false
preview=None
underlining=OnMouseHover

[File Look]
bold=false
color=invalid
hoverColor=invalid
iconSize=32
italic=false
preview=TwiceIconSize
underlining=Never

[Insert Note Default Values]
defIconSize=32
defImageX=300
defImageY=200

[KFileDialog Settings]
Height 768=659
Recent Files[$e]=SLavatar.png,/media/comms/SLAdmin/SLiCons/SLavatar.png
Width 1360=1056

[Launcher Look]
bold=true
color=invalid
hoverColor=invalid
iconSize=48
italic=false
preview=None
underlining=Never

[Local Link Look]
bold=false
color=invalid
hoverColor=invalid
iconSize=22
italic=true
preview=TwiceIconSize
underlining=OnMouseHover

[Main window]
autoBullet=true
basketTreeWidth=-1
bigNotes=false
blinkedFilter=false
confirmNoteDeletion=true
dataFolder[$e]=
enableReLockTimeout=true
exportTextTags=true
filterOnTop=false
groupOnInsertionLine=false
hideOnMouseOut=false
lastBackup=-4713,1,1
middleAction=0
playAnimations=true
position=0,36
reLockTimeoutMinutes=0
showIconInSystray=false
showNotesToolTip=true
showOnMouseIn=false
size=1360,708
spellCheckTextNotes=true
startDocked=true
timeToHideOnMouseOut=0
timeToShowOnMouseIn=1
treeOnLeft=true
usePassivePopup=true
useSystray=true
welcomeBasketsAdded=true

[MainWindow]
Height 768=769
State=AAAA/wAAAAD9AAAAAAAABVAAAAJlAAAABAAAAAQAAAAIAAAACPwAAAABAAAAAgAAAAIAAAAWAG0AYQBpAG4AVABvAG8AbABCAGEAcgEAAAAA/////wAAAAAAAAAAAAAAJgByAGkAYwBoAFQAZQB4AHQARQBkAGkAdABUAG8AbwBsAEIAYQByAQAABNH/////AAAAAAAAAAA=
ToolBarsMovable=Disabled
Width 1360=1361

[MainWindow Toolbar mainToolBar]
IconText=IconOnly
Index=0
alreadySetToolbarSettings=true

[MainWindow Toolbar richTextEditToolBar]
Index=1
Position=Top

[Network Link Look]
bold=false
color=invalid
hoverColor=invalid
iconSize=16
italic=false
preview=None
underlining=OnMouseOutside

[Note Addition]
newNotesPlace=1
viewHtmlFileContent=0
viewImageFileContent=1
viewSoundFileContent=1
viewTextFileContent=0

[Notification Messages]
emptyBasketInfo=true
systemtrayquitBasKet Note Pads=false

[Programs]
animationProg=gimp
animationUseProg=true
htmlProg=quanta
htmlUseProg=false
imageProg=kolourpaint
imageUseProg=true
soundProg=
soundUseProg=false

[Sound Look]
bold=false
color=invalid
hoverColor=invalid
iconSize=32
italic=false
preview=None
underlining=Never

```

---

### Post by Habitual on 2013-06-03
> **sidewalkcynic said:**
> ```

[KFileDialog Settings]
Height 768=659
Width 1360=1056

[Main window]
size=1360,708

[MainWindow]
Height 768=769
Width 1360=1361


```

These values appear funny to me, at least not consistent in each of the stanzas

Just an observation.

---

### Post by sidewalkcynic on 2013-06-03
And, I have played with them, and it does not seem to help. Maybe I need to be a little bit more methodical about it, but that will have to wait until tommorrow - i'm too tired now. Thanks.

---

### Post by sidewalkcynic on 2013-06-04
It seems that the numbers in those contexts only effect the main window, and not the dialog box.

---

### Post by Habitual on 2013-06-04
Perhaps the dialog box(es) are re-sizable and need to be re-sized by hand once?
Did you try that?

Tomorrow is good too!

---

