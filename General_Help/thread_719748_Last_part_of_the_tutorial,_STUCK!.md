---
title: "Last part of the tutorial, STUCK!"
date: 2008-03-09
forum: General Help
---

### Post by Aaron_Griffiths_92 on 2008-03-09
Ive been installing a lookalike theme for vista and im now onto the screenlets, i have no idea how to install them, the first part of the installation notes told me to go to "make install" but i dont know where that is, it also gave me three terminal commands in none of which came to any avail. so im sat here looking at a folder full of screenlets that i have no idea how to install to my desktop... please reply swiftly... thanks!  

URL= [http://www.compiz.org/Desktop_Screenlets](http://www.compiz.org/Desktop_Screenlets)

---

### Post by oldos2er on 2008-03-09
"make install" is a command you enter in the terminal after compiling source code.

 After looking at the URL you posted, I think the easiest thing to do would be to add the repository to your software sources, then install through Synaptic or apt-get.

---

### Post by Aaron_Griffiths_92 on 2008-03-09
that was chinese to me

---

### Post by TeoBigusGeekus on 2008-03-09
You must first download the tar.bz2 file, which is a compressed archive (like a zip or rar file). Then you must double click it and the archive manager will decompress it anywhere you like, say on your desktop.
You then open a terminal (Applications->Accessories->Terminal) and navigate to the decompressed folder. 
cd /home/yourusername/decompressedfolder
(replace yourusername with you know what and decompressed folder with the name of the decompressed folder).
Once you are in the folder, you must type 
sudo make install
You will be asked for your password, type it and press enter.
The application will be installed and you are pretty much done...
Just type the other commands the tutorial tells you to in order to launch the screenlets.

---

### Post by Aaron_Griffiths_92 on 2008-03-09
tried the first part "nothing of this filename"

---

### Post by TeoBigusGeekus on 2008-03-09
> **Aaron_Griffiths_92 said:**
> tried the first part "nothing of this filename"
Could you be a bit more specific?

---

### Post by Aaron_Griffiths_92 on 2008-03-09
sent you a pm instead

---

### Post by oldos2er on 2008-03-09
> **Aaron_Griffiths_92 said:**
> that was chinese to me

 Ok, go to System, Administration, Software Sources. Click Third-Party software, then click +Add. Paste in "deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) gutsy screenlets" assuming you're running Gutsy. Close Software Sources.

 Open a terminal (Applications, Accessories, Terminal). Paste in this command:

wget [http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg](http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg) -O- | sudo apt-key add - && sudo apt-get update

 After that one's done, run this one:

sudo apt-get install screenlets

---

### Post by Aaron_Griffiths_92 on 2008-03-09
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

---

### Post by Aaron_Griffiths_92 on 2008-03-09
just incase his helps, I use the 64 bit version of ubuntu gutsy gibbon 7.10

---

### Post by Aaron_Griffiths_92 on 2008-03-09
bump

---

### Post by oldos2er on 2008-03-09
Check Software Sources to make sure all repositories are enabled.

---

### Post by Aaron_Griffiths_92 on 2008-03-10
how do i do this?

---

### Post by oldos2er on 2008-03-10
System, Administration, Software Sources; make sure all the boxes are checked underneath "Downloadable from the Internet"

---

