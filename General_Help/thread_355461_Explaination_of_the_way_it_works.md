---
title: "Explaination of the way it works"
date: 2007-02-07
forum: General Help
---

### Post by scottsanpedro on 2007-02-07
Hi,

I just loaded a programme (wpagui) for wireless configuration, just to check it out.

Then couldn;t figure how to get it running, so searched the forums and found an answer that said 
Type gui_wpa at the command prompt.

[]("http://ubuntuforums.org/showthread.php?t=244667&highlight=wpagui")

Did that and all works fine.

I then thought, I should have been able to figure that out by finding the (what I called .exe) file so this will help me in the future.

in terminal ran Locate wpa_gui

Nothing found.

So how does this run then, when I enter wpa_gui in the command prompt?

from a confused newie

Thanks

Scott

---

### Post by FluffyElmo on 2007-02-07
The *locate* command searches a database of file locations so if you just added the program it probably hasn't been indexed yet. It usually updates daily or you can update it immediately by typing *sudo updatedb* from the command line, that takes time though. 

You can also search for files directly using the *find* command, or use the GUI version of *find* by going to *Places->Search for Files...* on the top menu. I think this command behaves more like what you originally expected from *locate*.

---

### Post by llamakc on 2007-02-07
Another thing one can do is use the dpkg tools to locate all of the files installed with a package.

```

dpkg -L packagename

```

---

### Post by mcduck on 2007-02-07
One more is 'which' command that searches executable files and displays then the path. For example 'which beryl' will output '/usr/bin/beryl'

Anyway, the executable files for almost everything you install will be in /usr/bin..

---

### Post by scottsanpedro on 2007-02-07
excellant. this will help me no end.
thanks very much :)

---

