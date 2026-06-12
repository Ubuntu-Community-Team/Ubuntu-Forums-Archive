---
title: "Wine wont work :/"
date: 2007-08-08
forum: General Help
---

### Post by bolex on 2007-08-08
When i typed "wine tmoriginaldemo.exe" (or any .exe files) in the terminal, it replied:

Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
wine: could not load L"c:\\windows\\system32\\tmoriginaldemo.exe": Module not found

What should i configure, so i can run exe games in Ubuntu? :/

---

### Post by dfreer on 2007-08-08
Firstly, have you run the command *winecfg* by itself yet? This generally creates needed files at ~/.wine/

Also, you need to specify the path to the .exe you are trying to run. For example, if that .exe is located on your desktop, you should try this command:
```
wine ~/Desktop/tmoriginaldemo.exe
```
Or if it is located in your home folder, this command:
```
wine ~/tmoriginaldemo.exe
```
If you change directory to the program, you should run it like so:
```
wine ./tmoriginaldemo.exe
```

---

### Post by bolex on 2007-08-08
I have just configured it, wich i mean pressing the autodetect.

The trackmania demo is located at my desktop, and if i use the command 
```
wine ~/Desktop/tmoriginaldemo.exe
```

it just write back:

```
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.

```

---

### Post by dfreer on 2007-08-08
hmmm. I'm not too sure from here, it may be the demo simply doesn't work. I'm downloading a copy from downloads.com or whatever, to see if I get the same results.

The copy I got produced this error:
```
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
```
But it proceeded to install fine. Although it doesn't appear to actually run. Not sure why you are getting these errors:
```
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
```

---

### Post by Aesir09 on 2007-08-08
dude instead of doing things in terminal just go to the item you want to "wine" and open it with "custom Command" and in there just type wine.

you might have been providing the wrong path

---

### Post by dfreer on 2007-08-08
If you know it works in wine, this is good advice. But if you are trying to troubleshoot why a program doesn't work, you'll need to use the commandline to see the error messages...

---

