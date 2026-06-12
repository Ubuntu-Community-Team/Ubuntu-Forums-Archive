---
title: "Downloaded software won't action exe file"
date: 2014-09-07
forum: General Help
---

### Post by bobipod on 2014-09-07
I have set up a voice number via a voip provider.  I have downloaded the TAR file and it offers to open with Archive manager or archive mounter.  I have managed to extarct the file  which is the exe file to my download page.  If i right click it offers the choice to run but it won't do anything.  In properties the file is 15.0mb in size and syas it's file type is executable (application/x-executable)

What do i do to have this software run and set up the installation that i need?

I'm using 14.04 Ubuntu.

Thanks

---

### Post by yancek on 2014-09-07
A tar file when extracted will generally contain several files and usually contains a README or Install file telling the user what to do.  A first step to getting help is to post the name of the tar file and probably the site where you got it.  Also what the application is intended to do.

---

### Post by egeezer on 2014-09-07
The .exe files are Windows-specific, and are not executable by Linux systems unless you are using WINE.  You need to download a different file, one with the file extension .deb

---

### Post by bobipod on 2014-09-07
The file downloaded came from Voipfone.co.uk and i selected the option for Linux systems. I realise it may be the software at fault and not my OS. The application is supposed to install the software to use the voip phone on my pc to make the free calls.

---

### Post by nerdtron on 2014-09-07
What is the name of this TAR file? And what are the contents of the extracted folder?
Try the following command so that we can see the contents of the folder in question.
```
cd /path/to/Downloads/extracted/folder
ls -lah
```
Then post the output here.

---

### Post by egeezer on 2014-09-08
If you're still having trouble, try this Ubuntu reference:

  	 	 	 	   [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by mooreted on 2014-09-08
When I try to run it from a command line I get this:

./zoiper 
./zoiper: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory

Looks like you need some GTK libraries to make it work. Before you get into dependency hell, you might see if you can contact support and get instruction.

---

