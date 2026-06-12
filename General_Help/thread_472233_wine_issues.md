---
title: "wine issues"
date: 2007-06-12
forum: General Help
---

### Post by andymushu on 2007-06-12
I wanted to install version 0.9.37 of wine (the second newest one) because of compatibility issues with steam, but i ran into a lot of problems. i finally decided to just install the newest version and work from there. i installed it then ran the winecfg command. i tried to run steam through wine but it gave me this error: "Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/andy', starting in the Windows directory.
wine: could not load L"c:\\windows\\system32\\SteamInstall.exe": Module not found"

i know i have to be in the directory to run the .exe, but i can't even find this directory. any help?

---

### Post by Citizin on 2007-06-12
Im not big on WINE, I tried running MIRC in wine just to notice it runs horrible slow, the GUI lags, its just plain choppy, running a game in WINE would probably be pure hell.

Get Crossover, I recently installed it and it runs all of my windows apps without a problem, very smooth, and very fast.

---

### Post by andymushu on 2007-06-12
the game i want to play, counterstrike: source, is supposed to run particularly well in wine. one of the best games, so i hear. i am open to suggestions though. is crossover free? any links you could give me?

---

### Post by Shay Stephens on 2007-06-12
Try uninstalling wine via synaptic and then reinstalling wine via the deb (assuming you are using a deb).

---

### Post by andymushu on 2007-06-12
thanks for the reply, but it did nothing for me. either i need to figure out where my virtual c drive is located, or figure out why i can't run steam

---

### Post by cookies on 2007-06-12
> **andymushu said:**
> thanks for the reply, but it did nothing for me. either i need to figure out where my virtual c drive is located, or figure out why i can't run steam

If you delete /home/USERNAME/.wine, your Virtual C drive and all wine settings are deleted. 

USERNAME being your user name.

---

### Post by andymushu on 2007-06-12
so how would i go about recreating that virtual c drive?

---

### Post by cookies on 2007-06-12
Start winecfg, and it'll be remade.

---

### Post by andymushu on 2007-06-12
where is the virtual c drive located? i am under the impression that you need to be in the directory when you run an exe through wine. assuming this is true, the location of my files is kind of important.

can someone tell me how to fix the following errors? i ran winecfg but if didn't help.

andy@andy:~$ wine SteamInstall.exe
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/andy', starting in the Windows directory.
wine: could not load L"c:\\windows\\system32\\SteamInstall.exe": Module not found

---

### Post by andymushu on 2007-06-12
bump

---

### Post by cookies on 2007-06-12
> **andymushu said:**
> where is the virtual c drive located? i am under the impression that you need to be in the directory when you run an exe through wine. assuming this is true, the location of my files is kind of important.

can someone tell me how to fix the following errors? i ran winecfg but if didn't help.

andy@andy:~$ wine SteamInstall.exe
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/andy', starting in the Windows directory.
wine: could not load L"c:\\windows\\system32\\SteamInstall.exe": Module not found

Uhm

if steam is on your desktop

wine /home/andy/Desktop/SteamInstall.exe

simply typing wine SteamInstall.exe assumes that it is in C:\Windows\system32

Oh, and the virtual C is

/home/andy/.wine/drive_c/

.wine is hidden, so go to View > Show Hidden Files to see  it.

---

### Post by andymushu on 2007-06-13
thanks for the help. i got to the wine folder, but there is no virtual c. could someone tell me what i am doing wrong here? is there some command i need to run?

when i right click the steam install exe i get the option to open with wine, but it does nothing. wine is installed, but i need the virtual c drive.

---

### Post by Nythain on 2007-06-13
if your drive_c is missing, in terminal type
winecfg
that should recreate it
if it doesnt then its probably not missing
in terminal type
cd ~/.wine/drive_c
to get to program files type
cd ~/.wine/drive_c/Program\ Files

you can run an exe in wine from anywhere as long as you know the path to the exe.... example
wine ~/.wine/drive_c/Program\ Files/uTorrent/utorrent.exe
will work for me no matter where im at when i type it

---

### Post by andymushu on 2007-06-13
when i type winecfg it gives me this in the terminal

Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/andy', starting in the Windows directory.
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/', starting in the Windows directory.

then opens up the wine config dialog box. there is still no c drive though.

i got it working. thanks everyone for the help.

---

### Post by markusf21 on 2007-06-13
this is the easiest way for me
1. put .exe to be installed on desktop
2. open terminal
3. type wine and hit space bar
4. then just drag the exe into terninal and hit enter

---

### Post by Shay Stephens on 2007-06-13
The virtual c drive is in your wine directory /home/username/.wine/drive_c/

But you don't need to be in that directory.  When I run Photoshop 7, I use this:
wine "c:\program files\adobe\Photoshop 7.0\Photoshop.exe"

The quotes are needed if there are spaces in the path.  And you will notice that the windows path is used and not the linux path.

If you want to start fresh, uninstall wine, delete the wine folder in your home folder, reinstall wine, and run winecfg, then install the program you want to run.  If there is no program icon in the applications - wine menu, then reboot.  If still nothing, then create a launcher for it.

---

