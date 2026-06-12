---
title: "Having a problem with ePSXe"
date: 2012-11-24
forum: General Help
---

### Post by IIMaxII on 2012-11-24
I just switched from Windows 8 today so bare with my nooby questions.

I installed epsxe 1.6(linux version) extracted to home folder, and when I go to open epsxe nothing happens at all...I've looked up guides, tried to irc rooms, nothing...someone please help me! :( This is on linux mint, but it's basically the same thing as ubuntu right?

---

### Post by The Cog on 2012-11-24
What kind of file is it? What are you trying to open it with? How are you trying to open it?

---

### Post by IIMaxII on 2012-11-24
It's an executable file, I'm not trying to open it with anything, I'm just double clicking the file. I assume this is the proper thing to do as it is a native linux program port.

---

### Post by IIMaxII on 2012-11-24
Someone must know how to get it up and running, guides on google are outdated.

---

### Post by The Cog on 2012-11-26
If it is really an executable file, then double-clicking it should run it. But it may not be marked executable, and it may be running (possibly crashing) in the background without creating a window.

The normal thing to do if an executable is not running properly would be to run it from the command line, and see if it prints any error messages.
Open a command prompt in the directory where the executable is, and run the program from there. So if the executable filename epsxe, enter the command:
```
./epsxe
```

But let's check what you actually have. Again, with a command prompt in the same directory as the file, run these two commands and post the results here:
```
ls -l epsxe
file epsxe
```

It is possible that the only problem is that the file is not marked as executable. You can make it executable by editing the properties in your file manager.

---

