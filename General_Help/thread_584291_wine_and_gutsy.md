---
title: "wine and gutsy"
date: 2007-10-20
forum: General Help
---

### Post by chrishere01 on 2007-10-20
so yeah im trying to get wine installed with gutsey

can someone help me or walk me thru it

---

### Post by therealknewman on 2007-10-20
Applications > Add/Remove then search for Wine and check it. Worked fine for me.

---

### Post by chrishere01 on 2007-10-20
hmmm
yea its saying some error message
i did 
the sudo apt-get install wine
and its installed and what not
but its not running the exe's

---

### Post by ihcnet on 2007-10-20
What executables are you trying to run?

What does it say in the terminal after running the executable? Try wine <name>.exe <name> being the name of your program.

---

### Post by chrishere01 on 2007-10-20
hmm it says it isnt designed to run that file or something
and im trying to run .exe's and .msi
for steam

might be becaause i have 64 bit?

---

### Post by ihcnet on 2007-10-21
You might want to check out [http://appdb.winehq.org/appview.php?iVersionId=1554](http://appdb.winehq.org/appview.php?iVersionId=1554). Seems like some people have gotten it to install with 64 bit Ubuntu.

---

### Post by VinylPusher on 2007-10-21
To install Steam: -

1. Download the Steam installer to ~/.wine/
2. Download Tahoma font (search for 'tahoma.ttf' in Google) and copy it to ~/.wine/drive_c/windows/fonts/
3. Open a terminal and cd to .wine
4. Issue the following command: "wine start SteamInstall.msi"

Steam will now install and update itself.

Tested on 7.10 amd64.

---

### Post by chrishere01 on 2007-10-21
> **VinylPusher said:**
> To install Steam: -

1. Download the Steam installer to ~/.wine/
2. Download Tahoma font (search for 'tahoma.ttf' in Google) and copy it to ~/.wine/drive_c/windows/fonts/
3. Open a terminal and cd to .wine
4. Issue the following command: "wine start SteamInstall.msi"

Steam will now install and update itself.

Tested on 7.10 amd64.

it didnt work
my steaminstall.msi is in my .wine file

when i commanded it i received this 
home@home-desktop:~$ wine start SteamInstall.msi
fixme:exec:SHELL_execute flags ignored: 0x00000500
Application could not be started, or no application associated with the specified file.
ShellExecuteEx failed: File not found

---

### Post by chrishere01 on 2007-10-21
*sigh*

---

### Post by ocian on 2007-10-25
you have to cd to the directory where SteamInstall.msi is and then wine start SteamInstall.msi

---

