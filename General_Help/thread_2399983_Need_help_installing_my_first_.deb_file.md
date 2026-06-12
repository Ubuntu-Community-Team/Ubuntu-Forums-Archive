---
title: "Need help installing my first .deb file"
date: 2018-08-31
forum: General Help
---

### Post by scribner on 2018-08-31
I just downloaded my first .deb file to be installed manually. It's a program from Corel called AfterShot Pro 3, a RAW photo editor.

After I paid for the program on Corel's website, a download page came up. There are three different files to choose from for the Linux operating system: AfterShotPro3.deb, AfterShotPro3-system-Qt.deb, and AfterShotPro3.rpm. I chose the first one after some googling and reading that .deb is preferred over .rpm for Ubuntu (not sure what the second one is for; please share if you know).

Note that Corel provides no information on how to install the application on Linux, nor do their customer support know what to do.

So I did some more googling and found you should install deb files by entering: 

[FONT=courier new]~$ sudo dpkg -i /home/nick/Downloads/AfterShotPro3.deb[/FONT]

into Terminal. But that didn't seem to work so I entered something else I googled: 

[FONT=courier new] ~$ sudo apt-get install /home/nick/Downloads/AfterShotPro3.deb[/FONT]

But that didn't seem to work either. Now I am left with an icon for Corel AfterShot Pro 3 in my list of apps that doesn't work. How do I remove this partial install from my computer and correctly install the .deb file? Thanks so much for anyone who can help.

---

### Post by $yl9pAR%t on 2018-08-31
Is "nick" your username? If not replace "nick" with your username and run first command you mentioned.

Anyway I prefer gdebi to install .deb files. I guess you do not have gdebi installed by default so run this command in terminal:

```
sudo apt install gdebi
```

Next, using file manager navigate to directory where you have downloaded your .deb file, right click it and choose "install using gdebi" or something like that.

---

### Post by scribner on 2018-08-31
Thank you so much for your reply!

Yes, "nick" is my username.

I will take a look at everything you mentioned when I get home from a restaurant I'm about to visit. Could you please take another look at my last paragraph and tell me how to uninstall what's there now before I try to install it again?

---

### Post by deadflowr on 2018-08-31
Use apt instead of apt-get to install off-line debs, use the full path like you ran
```
sudo apt install /home/nick/Downloads/AfterShotPro3.deb
```

As per the dpkg command, something that can happen when using dpkg is that not all the package dependencies required might not be satisfied so then it errors or fails,
in that case you need to run
```
sudo apt-get install -f
``` 
which will or should fix the error issues.

The apt command posted above would have automatically fixed any depends issues.
As will installing the package through gdebi,

(You also might try installing it with The built in Software installer which should be the default option to use when clicking on the deb file, 
or at least it's the default option in Ubuntu main; i'm not sure about the various flavors out there)

---

### Post by NM5TF on 2018-09-01
@scribner....

you asked about the second choice file to download...the Qt.deb file

mostly for use of developers wanting to make changes....

"Qt is a cross-platform C++ application framework. Qt's primary feature is its rich set of widgets that provide standard GUI functionality."

for some in-depth reading, go here [http://http://doc.qt.io/qt-5/linux.html]("http://http://doc.qt.io/qt-5/linux.html")

tommy

---

