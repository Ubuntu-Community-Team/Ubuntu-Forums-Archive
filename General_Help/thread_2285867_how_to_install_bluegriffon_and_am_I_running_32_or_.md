---
title: "how to install bluegriffon? and am I running 32 or 64 bit"
date: 2015-07-08
forum: General Help
---

### Post by Southron on 2015-07-08
I am running xubuntu ubuntu 14.04.2 

I have installed software from the software center before but am now trying to download bluegriffon. from here [http://bluegriffon.org/pages/Download](http://bluegriffon.org/pages/Download)

Ive read several posts about installing downloaded programs and this comes closest to my problem [http://ubuntuforums.org/showthread.php?t=778886&highlight=how+to+install+downloaded+programs](http://ubuntuforums.org/showthread.php?t=778886&highlight=how+to+install+downloaded+programs)

I dont know what to do after I download the program 

The post above says to use the applications menu but I cant find one or even know if xubuntu has one. 

can someone please tell me how to run it once I download it?

---

### Post by overdrank on 2015-07-08
Hi and maybe this link can[**_ help _**]("http://askubuntu.com/questions/25961/how-do-i-install-a-tar-gz-or-tar-bz2-file")

---

### Post by monkeybrain20122 on 2015-07-08
bluegriffon is pre-compiled and you don't need to install. Just extract the tarball , go to folder bluegraffin and click on the file "bluegraffin" or "bluegraffin-bin"  (or from the terminal, cd into the bluegraffin folder and run "./bluegraffin"  without quotes) 

Since it is not installed in the file system for it to show up in the xubuntu menu you have to create a .desktop file and put it in ~/.local/share/applications. I or many other people can help you with that if you wish.

But the last update is 2013, is the project still alive?

---

### Post by Southron on 2015-07-08
Thanks for both your help. When I tried to extract the file it downloaded I got a message from archive manager that said it couldnt that said open it and archive type was not supported. The file ended in .tar-1 so maybe its a copy of another file (hence the -1)?
I dont even know what it means. I took off the tar-1 and it extracted. following above directions now

---

### Post by monkeybrain20122 on 2015-07-08
Are you sure the download was completed? I just downloaded a .tar.bz from your link and I had no problem extracting and running it.

---

### Post by Southron on 2015-07-08
Thanks for both your help. I renamed the downloaded file and it extracted. I will need help with the .desktop file and putting it in the applications folder if anyone will help thanks

---

### Post by monkeybrain20122 on 2015-07-08
You can find the template of a .desktop  file by looking at files from /usr/share/applications and edit the Name, Exec and Icon lines and other things that may be applicable

For example
```

[Desktop Entry]
Type=Application
Name=BlueGriffon
Exec=/home/monkeybrain/bluegriffon/bluegriffon
Icon=/home/monkeybrain/bluegriffon/chrome/icons/default/default48.png
Terminal=false
Categories=Development;

```

You should modify /home/monkeybrain/bluegriffon to the path to where you extarcted the blugriffon folder to.  You then save this file as for example, bluegriffon.desktop and put it in .local/share/applications in your home  and then make it executable(right click Properties .. depending on your file manager or from the terminal "chmod +x .local/share/applications/bluegriffon.desktop" without quotes)

.local is a hidden folder. You can see it by clicking 'show hidden' in your file manager or press ctrl+H to see it or you can simply mv the desktop file there from the terminal.

You may have to logout and log back in for it to show up in your xfce menu.

Edited 1: corrected typo in bluegriffon
Edited 2: changed Exec line from bluegriffon-bin to bluegriffon, the binary could not find the shared libraries in the folder by itself.

---

