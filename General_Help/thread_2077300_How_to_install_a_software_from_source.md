---
title: "How to install a software from source?"
date: 2012-10-28
forum: General Help
---

### Post by arunkumargoge on 2012-10-28
I very new to Ubuntu i work with linux before but i really dont know much about this .. I wanna help regarding installation of software.. I download the vlc player tar.xz file from [http://www.videolan.org/vlc/download-sources.html](http://www.videolan.org/vlc/download-sources.html) and i extracted the archive when i type [COLOR="YellowGreen"]make[/COLOR] it says cannot target on make file and i tried ./configure too but No use .. Is it possible to get source file like windows setup.exe file while dwl from synaptics or ubuntu s/w portal ?

---

### Post by howefield on 2012-10-28
Do you know that you can install VLC via the Ubuntu Software Centre ?

---

### Post by arunkumargoge on 2012-10-28
I do know that .. But i have to try this way, my internet speed is very less i cannot download everytime from ubuntu center .. For 22Mb it take 15 minutes ..and i really need backup for the software so that in future i can install without net connection ..

---

### Post by howefield on 2012-10-28
> **arunkumargoge said:**
> i cannot download everytime from ubuntu center .. For 22Mb it take 15 minutes ..and i really need backup for the software so that in future i can install without net connection ..

The packages downloaded from Ubuntu Software centre go into /var/cache/apt/archives so are easily copied elsewhere for future use.

Not answering the original question, but just so you know.

Try [http://wiki.videolan.org/UnixCompile#Ubuntu](http://wiki.videolan.org/UnixCompile#Ubuntu) for installing from source.

---

### Post by arunkumargoge on 2012-10-28
Thank you for this .. I followed you, most of them are *.deb files .. For each s/w like Vlc i'm getting lot of deb files .. How to  install deb files and which one i have to install at first there are many ?

---

### Post by ajgreeny on 2012-10-28
Put all the .deb files into a temporary folder in your /home, navigate to the folder in terminal and then install the debs with ```
cd path/to/folder && sudo dpkg -i *.deb
```The system will work out the order to install the individual packages.

I am still not sure why it is quicker to download the source than simply to get the debs installed from the repos;  you have to download everything at some point.

---

### Post by flint5 on 2012-10-28
Open a Terminal and go to folder where you have copied all this files,
for example if is copied in folder named 'debs' in your home folder, use command:

cd /home/debs

hit enter:

than use this command:

sudo dpkg -i *.deb

hit enter

than you have to enter your password, 

hit again enter, and thats all.

---

### Post by ajgreeny on 2012-10-28
> **flint5 said:**
> Open a Terminal and go to folder where you have copied all this files,
for example if is copied in folder named 'debs' in your home folder, use command:

[COLOR=Red]cd /home/debs[/COLOR]

hit enter:

than use this command:

sudo dpkg -i *.deb

hit enter

than you have to enter your password, 

hit again enter, and thats all.
The line in red above will not work! It should be ```
cd debs
```as you will already be in your home. If you want to figure out ways of using terminal navigation, for the full pathway you could also use ```
cd /home/*username*/debs
```Notice the difference?

---

### Post by flint5 on 2012-10-28
Sorry ajgreeny, you're right, my mistake i omit the username.

---

