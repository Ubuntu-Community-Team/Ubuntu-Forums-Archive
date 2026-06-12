---
title: "need help, installed wine but it doesnt work"
date: 2006-10-15
forum: General Help
---

### Post by markg729 on 2006-10-15
just installed wine, but when i open an exe using the terminal with "wine <name>.exe" it shows an error message that says

```
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
fixme:win:SetWindowTextA setting text "Untitled - Notepad2" of other process window (nil) should not use SendMessage
```

if its just the driver how would i go about getting it?
thanks in advance

---

### Post by orb9220 on 2006-10-15
What graphics card driver are you using?

And you are trying to run the installer for the program and not the program itself.

You have to install the program into wine's file structure first then add it to wine using the winecfg command.

For installing notepad2 you need to find the installer program and copy to desktop and run in a term:

sudo wine /home/orb/Desktop/notepad2.exe   as an example for my desktop.

You are not trying to run it from windows are you?

---

### Post by markg729 on 2006-10-17
1. standard one that came with Ubuntu, graphics card is an integrated intel one about 4 years old
2. trying to run the actual program
3. shows the same error without last line when trying to run winecfg
4. havent got there
5. definitaly not windows

it shows the same error whenever i do anything with wine or wine tools

was trying out some more things and was trying to install DCOM98 from wine tools but it game me a failed: 199 error

---

