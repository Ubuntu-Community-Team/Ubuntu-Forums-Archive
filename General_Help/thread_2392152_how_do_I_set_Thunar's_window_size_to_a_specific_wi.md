---
title: "how do I set Thunar's window size to a specific width and height?"
date: 2018-05-17
forum: General Help
---

### Post by ardouronerous on 2018-05-17
I've installed Thunar File Manager on Lubuntu 16.04.4 LTS and I want to resize Thunar with a width of 798 and a height of 547 exactly.

I've read somewhere that you can set Thunar's width and height in the thunarrc file located in [FONT=courier new]/home/user/.config/Thunar[/FONT] but I found no such file in the folder.

I've found a thunarrc file while Googling for solutions from here: [https://github.com/clauseggers/dotfiles/blob/master/.config/Thunar/thunarrc](https://github.com/clauseggers/dotfiles/blob/master/.config/Thunar/thunarrc)

```
[Configuration]
DefaultView=ThunarDetailsView
LastCompactViewZoomLevel=THUNAR_ZOOM_LEVEL_SMALLEST
LastDetailsViewColumnOrder=THUNAR_COLUMN_NAME,THUNAR_COLUMN_SIZE,THUNAR_COLUMN_TYPE,THUNAR_COLUMN_DATE_MODIFIED
LastDetailsViewColumnWidths=50,165,50,50,232,50,50,70,178
LastDetailsViewFixedColumns=FALSE
LastDetailsViewVisibleColumns=THUNAR_COLUMN_DATE_MODIFIED,THUNAR_COLUMN_NAME,THUNAR_COLUMN_SIZE,THUNAR_COLUMN_TYPE
LastDetailsViewZoomLevel=THUNAR_ZOOM_LEVEL_SMALLER
LastIconViewZoomLevel=THUNAR_ZOOM_LEVEL_NORMAL
LastLocationBar=ThunarLocationButtons
LastSeparatorPosition=170
LastShowHidden=FALSE
LastSidePane=ThunarTreePane
LastSortColumn=THUNAR_COLUMN_NAME
LastSortOrder=GTK_SORT_ASCENDING
LastStatusbarVisible=TRUE
LastView=ThunarDetailsView
LastWindowHeight=572
LastWindowWidth=841
LastWindowMaximized=FALSE
MiscVolumeManagement=TRUE
MiscCaseSensitive=FALSE
MiscDateStyle=THUNAR_DATE_STYLE_SHORT
MiscFoldersFirst=TRUE
MiscHorizontalWheelNavigates=FALSE
MiscRecursivePermissions=THUNAR_RECURSIVE_PERMISSIONS_ASK
MiscRememberGeometry=TRUE
MiscShowAboutTemplates=TRUE
MiscShowThumbnails=FALSE
MiscSingleClick=FALSE
MiscSingleClickTimeout=500
MiscTextBesideIcons=FALSE
ShortcutsIconEmblems=FALSE
ShortcutsIconSize=THUNAR_ICON_SIZE_SMALLEST
TreeIconEmblems=FALSE
TreeIconSize=THUNAR_ICON_SIZE_SMALLEST


```

I've set [FONT=courier new]LastWindowHeight[/FONT] to 547 and [FONT=courier new]LastWindowWidth[/FONT] to 798 and saved the file as thunarrc in [FONT=courier new]/home/user/.config/Thunar[/FONT], but nothing happened, Thunar retains the width and height from when I first installed it.

---

### Post by kazakore on 2018-05-17
I use Ubuntu Studio so full XFCE based and have changed the value of LastWindowWidth using the settings editor (package xfce4-settings-editor) and after changing the setting opening a new window opens to the width I've manually set.

Edit:
and according to the Arch Wiki the file you want to edit, if doing so by hand, is
~/.config/xfce4/xfconf/xfce-perchannel-xml/thunar.xml
Although it does say these changes wont be seen immediately (maybe try restarting??)

[https://wiki.archlinux.org/index.php/Xfce#Configuration](https://wiki.archlinux.org/index.php/Xfce#Configuration)

---

### Post by ardouronerous on 2018-05-17
Thanks that worked! :)

I went to [FONT=courier new]/home/user/.config/xfce4/xfconf/xfce-perchannel-xml/thunar.xml[/FONT] and edited these values:
```
  <property name="last-window-width" type="int" value="640"/>
  <property name="last-window-height" type="int" value="480"/>
```
into
```
  <property name="last-window-width" type="int" value="798"/>
  <property name="last-window-height" type="int" value="547"/>
```

After restarting, Thunar's window size was resized to my specifications, thanks.

---

### Post by dragonfly41 on 2018-05-17
I will add this note which I was typing as you were searching for a solution.

...

There is a useful tool actiona which has lots of applications for automating desktop.

Launch actiona (it should be in Accessories)

In the blank gui add just one action - window

Parameters: 

Window Title:  e.g. <username> - File Manager
Action: Resize
Resize width: 798
Resize height: 547

save and run

This will resize Thunar window

You can also add - move position.

Save the file as say thunar.ascr

You can run such scripts in command line by typical command
actexec thunar.ascr

---

