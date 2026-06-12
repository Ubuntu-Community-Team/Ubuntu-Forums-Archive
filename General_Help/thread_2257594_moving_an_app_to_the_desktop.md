---
title: "moving an app to the desktop"
date: 2014-12-20
forum: General Help
---

### Post by renbri on 2014-12-20
I'm very new (ex windows) and I'm trying to move the sudoku game that i've installed to the desktop. At the moment I access it via the dash every time. When I tried to drag and drop from there to the desktop I get an error message. There doesn't seem to be a move option on the launcher icon. Do I have to use commands, or am I restricted to the dash method? Thanks.

---

### Post by flaymond on 2014-12-21
Can you tell us what flavor of Ubuntu do you use? Is it Ubuntu? Xubuntu? Lubuntu? Kubuntu?

---

### Post by mc4man on 2014-12-21
Try - 
Browse to computer >  /usr/share/applications
look for a sudoku icon in there, if you find it > right click > copy to > select Desktop in Places & then click on the Select button on bottom of the window.

---

### Post by renbri on 2014-12-21
Interprog: I have installed Ubuntu 14.04 LTS.
mc4man: I don't really understand your advice. Does it mean using the command line? I tried entering the command ls /usr/share/applications and got a list of things like unity-display-panel.desktop, unity info-panel.desktop, etc with no sign of the sudoku app.

---

### Post by deadflowr on 2014-12-21
No command line needed. The advice is done in the "Files" program. 
Simply put you need to copy the file with the Sudoku icon from the folder /usr/share/applications to the Desktop folder, which should be listed in the Places section of the leftside bar in the Files program.
Do not try to move or drag and drop. Just right click and copy.

The file name is actually gnome-sudoku.desktop, fwiw.
(Though in the Files program it will show as Sudoku with the normal icon for it.)

If any of this makes any sense.

---

### Post by renbri on 2014-12-21
I'm beginning to feel really dense. I assume that by "Files" program, you mean that which is launched by the Files icon on the launcher. But that just shows me my "Home" directory containing folders like Desktop, Documents, etc; nothing that looks like usr/share/applications and no sign of the sudoku that I see when I go to Dash.

---

### Post by deadflowr on 2014-12-21
> **renbri said:**
> I'm beginning to feel really dense. I assume that by "Files" program, you mean that which is launched by the Files icon on the launcher. But that just shows me my "Home" directory containing folders like Desktop, Documents, etc; nothing that looks like usr/share/applications and no sign of the soduko that I see when I go to Dash.

Yes, that is what is meantby Files.
Sorry, we probably should have noted that to navigate to the /usr folder, and its subfolders, you click on the entry marked Computer in the left side panel.

(In Ubuntu 12.04 it is called File System instead of Computer, but I believe drag and drop works for it so in that case all this would be moot)

Edit: I think it should be clarified that this method is only one of the ways to do it.
If for some reason you feel more comfortable doing it using a command line then that is okay too.
In that case the command would be
```
cp /usr/share/applications/gnome-suduko.desktop ~/Desktop
```

---

### Post by monkeybrain20122 on 2014-12-21
Pin it to the launcher (the on the left) instead of scattering your stuffs all over the desktop like in Windows, it is what it is designed for.

---

### Post by renbri on 2014-12-21
How fascinating language can be, especially when you don't speak quite the same brogue as the other fella. I thank you for your patience and suspect that you are perhaps talking about the 12.04 version rather than the 14.04. What I see is a desktop called Unity with a "menu bar" along the top and a "Launcher" down the left hand side. There is nothing on either of them called "Computer", or even "File System" other than the Launcher icon called "Files".
Perhaps, when I gain a little more expertise, I'll be able to find the mysterious directory or folder and put it on something in the GUI. 
I certainly don't want to go command line for preference at this stage. I'm sure I'll have fun in the terminal later on but right now I want to become familiar with GUI and its capabilities.
Meanwhile, I note that I can lock the Sudoku icon to the Launcher if I choose and that would give me a desktop access without going through the dash.
The thing is, I now have this Linux OS with its nice hierarchical file system and I wanted to start off logically and put my primary folders and apps in the Desktop directory.
Also, both you and mc4man talk about a usr/share/applications folder as if it's something accessible via the GUI whereas to me it looks very much like a pathname that one would use on a command line.
Anyway, I thank you again for your generous efforts.
I might click on the sudoku icon on the launcher and try a hard one.
Is this masochism creeping up on me?

---

### Post by renbri on 2014-12-21
P.S. Also, the number of icons I can sensibly lock to the launcher is limited so I have to learn how to move them to the desktop at some stage. (There is no facility to drag and drop from launcher to desktop.)

---

### Post by renbri on 2014-12-21
Yes, I've discovered that, but surely you can only do that with a limited number of apps before the icons get very tiny? 
I take your point that I'm thinking like a windows man (no surprise) but I'd like the option, or just the understanding of what the other blokes are telling me.

---

### Post by monkeybrain20122 on 2014-12-21
How many do you want to pin to the launcher? It can fit quite a lot actually because of its "accordion" design. I have 24, which is unusual for most people.

---

### Post by deadflowr on 2014-12-21
> **renbri said:**
> How fascinating language can be, especially when you don't speak quite the same brogue as the other fella. I thank you for your patience and suspect that you are perhaps talking about the 12.04 version rather than the 14.04. What I see is a desktop called Unity with a "menu bar" along the top and a "Launcher" down the left hand side. There is nothing on either of them called "Computer", or even "File System" other than the Launcher icon called "Files".
Perhaps, when I gain a little more expertise, I'll be able to find the mysterious directory or folder and put it on something in the GUI. 
I certainly don't want to go command line for preference at this stage. I'm sure I'll have fun in the terminal later on but right now I want to become familiar with GUI and its capabilities.
Meanwhile, I note that I can lock the Sudoku icon to the Launcher if I choose and that would give me a desktop access without going through the dash.
The thing is, I now have this Linux OS with its nice hierarchical file system and I wanted to start off logically and put my primary folders and apps in the Desktop directory.
Also, both you and mc4man talk about a usr/share/applications folder as if it's something accessible via the GUI whereas to me it looks very much like a pathname that one would use on a command line.
Anyway, I thank you again for your generous efforts.
I might click on the sudoku icon on the launcher and try a hard one.
Is this masochism creeping up on me?

"Computer" is inside the program Files. When you open Files look at the left side pane for that program. You will see an entry for Computer.
It should be listed under the Devices section, I would think.
Nothing I referred to had anything to do with unity's launcher.

It's rare, but entirely possible that the sidebar for Files is not enabled. F9 should enable it if that is the case.

---

### Post by renbri on 2014-12-21
'Onyer deadflowr, I finally got it. And the copy-paste system worked.

It appears that the Unity desktop is not so different to Windows 7, with the Launcher being roughly equivalent to the "task bar" and the Dash somewhat similar to the "Start" button.
And your guidance has shown me how to open it up even more.
A thousand thanks for your persistence, mate. 
And Merry Xmas to boot.

---

### Post by renbri on 2014-12-21
But, monkeyface, there is all that real estate on the desktop proper. What do you do with that?
I guess it's all a matter of personal choice but my approach with Windows was to put my primary folders (e.g. educational categories from Anthropology to Zoology) and apps that I didn't use all that often or were not of major importance(like YouTube downloader or an encyclopedia) on the main desktop (not "scattered" but in neat rows alphabetically ordered!) and the frequently used or key items (like browser and office start buttons) on the "task bar"-which seems very much like the "launcher" to me.
Chaque un s[COLOR=#545454][FONT=arial]**on goût**[/FONT][/COLOR][COLOR=#545454][FONT=arial]  I suppose
Thanks for your input.[/FONT][/COLOR]

---

