---
title: "Java app bluej not respecting custom theme fonts/cursor"
date: 2014-01-21
forum: General Help
---

### Post by samwillc on 2014-01-21
Hi,

Does anyone know why the java app bluej does not respect the theme I have chosen. Running ubuntu 12.04 and ubuntu-tweak I chose 'uncomplicated' theme because of its pleasant but simple look. However, when running bluej, the default Monospace font is not 'Meslo LG S' which I chose for the default monospace font and also, I chose 'whiteglass' for the cursor. Now when hovering around in a firefox window, the cursor is the one I chose in ubuntu-tweak, as soon as I move in across the screen and onto a bluej window, the cursor changes back to default ('DMZ White').

I don't know why my theme choices are not respected but I suspect it's something not to do with bluej in particular, but more a java issue after reading about similar problems people have had in netbeans. Running:

```
sam@sam-pc:~$ java -version
java version "1.7.0_51"
Java(TM) SE Runtime Environment (build 1.7.0_51-b13)
Java HotSpot(TM) 64-Bit Server VM (build 24.51-b03, mixed mode)
```

I have had to edit the bluej.defs file and manually input 'Meslo LG S' as the editor font in a number of places which seems pretty daft seeing as 'Monospaced' should be enough to use the monospaced font I have chosen as the system default, if that makes sense. An extract:

```
bluej.editor.font=Meslo LG S
#bluej.editor.font=Inconsolatas
#bluej.editor.font=Monospaced
#bluej.editor.font=Courier
#bluej.editor.font=SansSerif-bold
#bluej.editor.font=Arial-bold
```

If I comment out the Meslo LG S line and uncomment the Monospaced one, the font displayed in bluej looks a lot like courier new, except a badly drawn skinny version. Why font hinting seems to be at maximum in java is another topic, fonts look useless in menus etc. That's another thing I need to look into.

Any extra info would be very helpful, thanks.

Sam.

**EDIT**

Can I add that the cursor works correctly throughout all apps when I manually set it here:

```
sudo update-alternatives --config x-cursor-theme
```

---

