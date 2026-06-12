---
title: "PCMan as Root"
date: 2013-11-18
forum: General Help
---

### Post by Robbyx on 2013-11-18
I have pcman latest version working in Ubunutu.

To run it as root they advise that I create a file in file-manager/actions ([http://wiki.lxde.org/en/PCManFM#Run_as_root](http://wiki.lxde.org/en/PCManFM#Run_as_root))

I have created a file  /home/robins/.local/share/file-manager/actions/root_pcman

In it I have placed:

> Desktop Entry]
Name = Open as Root
Tooltip = Open the folder as root
Icon = terminal
Profiles = on_folder;

[X-Action-Profile on_folder]
Name = Open as Root
MimeTypes = inode/directory;
SelectionCount = 1
Exec = gksudo pcmanfm %s


I do not know what to do next to open PCMan as root as the instrucions seem to stop at that point. 

Could you please  have a look at the reference above and suggest how I actually load PCMan as root.



Robin

---

### Post by Robbyx on 2013-11-18
Could someone please comment on my question because I do not understand how to proceed.

---

### Post by QIII on 2013-11-18
Please do not bump your threads any more often than 24 hours.  As you know, this is a world-wide community of volunteers who take time from our busy lives as we can.

Please give the community time to respond.

---

### Post by Robbyx on 2013-11-19
I have got a bit further by following the advice at 

[http://www.howopensource.com/2012/10/create-application-launcher-add-icon-to-unity-ubuntu-12-10/](http://www.howopensource.com/2012/10/create-application-launcher-add-icon-to-unity-ubuntu-12-10/)

and so I put the launcher  file into  

  /home/robins/.local/share/applications

and called the file pcman_root.desktop

with its contents:
[Desktop Entry]
Name = pcman_root
Tooltip = Open the folder as root
Icon = terminal
Profiles = on_folder;

[X-Action-Profile on_folder]
Name = Open as Root
MimeTypes = inode/directory;
SelectionCount = 1
Exec = gksudo pcmanfm %s


Searched for it in Unity and dragged it to the unity launcher and it did not work!!

Any ideas what I need to change?

---

### Post by black veils on 2013-11-20
ok you have got yourself into a little muddle. it seems all you wanted was to be able to open the file manager as root. you can either run the command **gksudo pcmanfm** or follow that guide as you did, from what i understand the guide is to provide an option in the tools menu or right-click menu in the file manager, to open as root.

there is another way you can do this, and thats to [COLOR="#FF0000"]copy[/COLOR] the pcmanfm menu file from **/usr/share/applications** to **/.local/share/applications**. change the file name to "pcmanfm root" or something. then open the file in a text editor and edit the line starting **Exec=** to look like this: **Exec=gksudo pcmanfm**. actually changing the line starting **Name=** would probably be good too, check for other name lines which might apply to you, like for me there is default and en_GB line.

now you should have 2 menu entries for the file manager, one being for root only.

---

### Post by Bucky Ball on 2013-11-20
Why do you want to open it as root??? You want to be REAL careful doing that as you can cause SERIOUS breakage.

If you want to access a folder that won't open any other way, open a terminal and 'gksudo pcmanfm'. That's it. Do what you need to do and then close the windows pronto. You can also access it via a terminal by using sudo. 

Opening any file browser as root is not a great idea unless there is no other way.

---

### Post by vasa1 on 2013-11-20
> **Bucky Ball said:**
> Why do you want to open it as root??? You want to be REAL careful doing that as you can cause SERIOUS breakage. ...
+1. 
All the same, PCManFM has the facility to open the current folder as root under **Tools**.

---

### Post by Bucky Ball on 2013-11-20
> **vasa1 said:**
> +1. 
All the same, PCManFM has the facility to open the current folder as root under **Tools**.

You learn something everyday! So it does. Thanks for that tip. ;)

---

### Post by Robbyx on 2013-11-22
Actually the latest version on the pcman website does not have the root option any more.  I am using that one not the one in our repository.

---

### Post by Robbyx on 2013-11-22
> **black veils said:**
> ok you have got yourself into a little muddle. it seems all you wanted was to be able to open the file manager as root. you can either run the command **gksudo pcmanfm** or follow that guide as you did, from what i understand the guide is to provide an option in the tools menu or right-click menu in the file manager, to open as root.

there is another way you can do this, and thats to [COLOR="#FF0000"]copy[/COLOR] the pcmanfm menu file from **/usr/share/applications** to **/.local/share/applications**. change the file name to "pcmanfm root" or something. then open the file in a text editor and edit the line starting **Exec=** to look like this: **Exec=gksudo pcmanfm**. actually changing the line starting **Name=** would probably be good too, check for other name lines which might apply to you, like for me there is default and en_GB line.

now you should have 2 menu entries for the file manager, one being for root only.


I have followed your second route leaving the previous version in the files. If I double click the version in .local/share/applications it opens and requests the admin password. However I am not seeing the file in the file manager. What more should I have done to get it there?

---

### Post by vasa1 on 2013-11-22
> **Robbyx said:**
> Actually the latest version on the pcman website does not have the root option any more.  I am using that one not the one in our repository.
There were plans to drop that option because it was potentially "dangerous". Looks like they're going ahead with that then.

---

### Post by Bucky Ball on 2013-11-22
> **vasa1 said:**
> There were plans to drop that option because it was potentially "dangerous". 

Which is why you shouldn't make any adjustments to make pcmanfm open as root on a permanent basis. Should be one time only. You would want a VERY good reason to have it open as root always. 'gksudo pcmanfm' is the best bet.

---

### Post by vasa1 on 2013-11-23
> **Robbyx said:**
> I have followed your second route leaving the previous version in the files. If I double click the version in .local/share/applications it opens and requests the admin password. However I am not seeing the file in the file manager. What more should I have done to get it there?
What exactly are you trying to do?
Why do you need the admin password to edit files in ~/.local/share/applications?

---

### Post by Bucky Ball on 2013-11-23
> **vasa1 said:**
> What exactly are you trying to do?


+1. My previous thoughts exactly.

---

### Post by stinkeye on 2013-11-23
My understanding of Robbyx's post is he simply wants a right click menu to open a directory
as root...the same as what can be done in nautilus and the earlier pcmanfm version.
Out of curiosity I installed pcmanfm from the [**_[COLOR="#B22222"]lubuntu daily repo[/COLOR]_**]("https://launchpad.net/~lubuntu-dev/+archive/lubuntu-daily").

I found that it picked up my nautilus-actions entry so just made one for pcmanfm.
Even when I set pcmanfm as the default file manager and the nautilus-actions item
was using  "**xdg-open**" it would still use nautilus, so made a duplicate but specified "pcmanfm".


[COLOR="#B22222"]**EDIT**:[/COLOR] **@Robbyx**
The method in your first post should work.
Save this as **root_pcman.desktop** to  **/home/robins/.local/share/file-manager/actions**
```
[COLOR="#FF0000"][[/COLOR]Desktop Entry]
 Name = Open as Root
 Tooltip = Open the folder as root
 Icon = dialog-password
 Profiles = on_folder;

 [X-Action-Profile on_folder]
 Name = Open as Root
 MimeTypes = inode/directory;
 SelectionCount = 1
 Exec = gksudo pcmanfm %[COLOR="#FF0000"]f[/COLOR]
```
Close any instances of pcmanfm and then open pcmanfm to check.
[ATTACH=CONFIG]248020[/ATTACH]

Another way when using unity is to add a quicklist item to launcher.
This will just open as root to your home folder.
```
cp /usr/share/applications/pcmanfm.desktop ~/.local/share/applications
```

add a quicklist item....
```
gedit ~/.local/share/applications/pcmanfm.desktop
```
and add this to the bottom....
```
Actions=root;

[Desktop Action root]
Name=Open as Root
OnlyShowIn=Unity;
Exec=gksudo pcmanfm
```
Save and close .

Drag and drop pcmanfm from the dash to the launcher and you will have a right click  "Open as Root" item.
[ATTACH=CONFIG]248019[/ATTACH]

---

### Post by Robbyx on 2013-11-23
I would like to think I had it working but I am not sure if I really have two versions now. As a starter could you suggest a way that I can tell what form of pcman has opened. I need to know if I am looking at the root version or the standard one. What would be ideal is if there was some header in pcman that said "Root is now being used"

---

### Post by Bucky Ball on 2013-11-23
The left hand column selections should be changed and root will be in there. The list will be icons. There is probably another way, but if you open a terminal, 'gksudo pcmanfm', you can be guaranteed you are in as root so take it as a given ...

---

### Post by Robbyx on 2013-11-23
All you wonderful people have given me so many solutions that I am now muddled and do not have pcman working the way I want. I want one version for ordinary use and another to be used at the same time for sudo. When I search in Unity for pcman 

**In applications** I have 
Pcman root (Does not work as nothing opens)
File manager pcmanfm (a folder)
PcmanFM
Desktop preferences

**In files and folders**
Pcman root. desktop
Aplications (a folder)

---

### Post by stinkeye on 2013-11-23
If you install the **compiz-plugins** package you will have a title bar info plugin
which can show root.
I use custom icons as well that I only install to ~/.icons so root has different icons.
Also shows an icon in the navigation bar.

---

### Post by stinkeye on 2013-11-23
> **Robbyx said:**
> All you wonderful people have given me so many solutions that I am now muddled and do not have pcman working the way I want. I want one version for ordinary use and another to be used at the same time for sudo. When I search in Unity for pcman 

**In applications** I have 
Pcman root (Does not work as nothing opens)
File manager pcmanfm (a folder)
PcmanFM
Desktop preferences

**In files and folders**
Pcman root. desktop
Aplications (a folder)

File manager pcmanfm (a folder)...opens pcmanfm here.
If you have created a  file **~/.local/share/applications/pcmanfm.desktop** that will override  **/usr/share/applications/pcmanfm.desktop**
Delete **~/.local/share/applications/pcmanfm.desktop** to use the default **/usr/share/applications/pcmanfm.desktop** again.

---

### Post by vasa1 on 2013-11-23
> **Robbyx said:**
> I would like to think I had it working but I am not sure if I really have two versions now. As a starter could you suggest a way that I can tell what form of pcman has opened. I need to know if I am looking at the root version or the standard one. What would be ideal is if there was some header in pcman that said "Root is now being used"

I (inadvertently) have a way to distinguish GUIs when opened as root or as user :)

The gtk theme and icon theme and window theme I use are not system-wide and so when I open something such as synaptic or gedit or leafpad with gksudo, the window uses fallbacks which are visually very different from  my themes.

I previously used to take the trouble of making logical links so that both GUIs (gksudo and normal) would look the same but now I don't.

---

