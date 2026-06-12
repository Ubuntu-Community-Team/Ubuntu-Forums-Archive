---
title: "Need help installing opera please"
date: 2005-09-27
forum: General Help
---

### Post by Eejay on 2005-09-27
Hi everybody I was wondering if someone could show me how to install Opera web browser, I noticed that Operas website had a Deb install But I did not see one for Ubuntu.

The reason why I ask is because I just now finished installing Ubuntu (took 2 hours) everything is looking good I don't want to mess up the tar ball and install it on to the wrong area I have a feeling that Opera will conflict with Ubuntu or need additional plug ins. Some say Opera is computable with Ubuntu others disagree, I don't know so I figured I'd come here and ask the pros. 

Any help suggestions on how to go about Installing Opera web browser will be much appreciated.

[http://www.opera.com/](http://www.opera.com/)

---

### Post by odin on 2005-09-27
the only thing I can tell you is that I installed it in ubuntu with no problems and there's actually a version for the 3 releases(breezy,hoary,warty)of ubuntu.

---

### Post by Zotova on 2005-09-27
Goto the following link

[http://www.opera.com/download/index.dml?platform=linux&x=175&y=17](http://www.opera.com/download/index.dml?platform=linux&x=175&y=17)

In the drop down box select ubuntu and then select 5.04 from the three tick boxes below. For ease save it in your home directory.

Once downloaded install it by opening the terminal and typing:

sudo dpkg -i xxx.deb

Of course changing xxx to the name of your file - in my case the file was called opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb so you would use the following:

sudo dpkg -i opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb

Once it has installed you should find opera in your internet folder.

---

### Post by Eejay on 2005-09-27
Thanks for the reply I saved the download onto the desktop then typed, into the terminal  sudo dpkg -i xxx.deb opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb

Then received this error message

 username@box:~$ sudo dpkg -i xxx.deb opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb
dpkg: error processing xxx.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 xxx.deb
 opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb
username@box:~$

Any idea on what could have gone wrong I don't want to muck up this pc again so I'm being real cautious about longing is as root or sudo thanks for the replies I appreciate them.

---

### Post by hellothere55 on 2005-09-27
In the terminal goto were you downloaded it and type "sudo dpkg -i o" and then press tab.  It should then auto complete with the opera pack as long as theres only one o file.  Press enter afterwards and that should install it.  Make sure to restart the gnome-panel, "killall gnome-panel".  Look for it in the Internet folder of the Applications menu.

---

### Post by Eejay on 2005-09-27
Update: I knew it everyone has been complaining about Ubuntu having dependency issues with Opera I tried just about everything to install this web browser here is the latest error message.

username@box:~$ sudo dpkg -i xxx.deb opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb
dpkg: error processing xxx.deb (--install):
 cannot access archive: No such file or directory
Selecting previously deselected package opera.
(Reading database ... 58048 files and directories currently installed.)
Unpacking opera (from opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb) ...
dpkg: **dependency problems prevent configuration of opera:**
 opera depends on libqt3c102-mt; however:
  Package libqt3c102-mt is not installed.
dpkg: error processing opera (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xxx.deb
 opera
username@box:~$

---

### Post by Eejay on 2005-09-27
Thanks for the replies

How do I reach that point from the terminal 

...... I opened the terminal typed home/username opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb and then typed "sudo dpkg -i o and nothing happened. How am I supposed to change into the directory where the downloaded is located using the terminal ? I tried everything 

Home/username opera_8.50-20050916.5-shared-qt_en_sarge_!386.ded ... Nothing happened I don't know how to use the terminal to cd into the directory where the download is located. sorry for being such a Noob I just installed Ubuntu a couple days ago.

I been at this for 3 hours I am about ready to take a 45 automatic and blow up this damn computer lol

---

### Post by Eejay on 2005-09-27
[QUOTE=hellothere55]In the terminal goto were you downloaded it.[/QUOTE]

Thanks for the replies

How do I reach that point from the terminal 

...... I opened the terminal typed home/username opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb and then typed "sudo dpkg -i o and nothing happened. How am I supposed to change into the directory where the downloaded is located using the terminal ? I tried everything 

Home/username opera_8.50-20050916.5-shared-qt_en_sarge_!386.ded ... Nothing happened I don't know how to use the terminal to cd into the directory where the download is located. sorry for being such a Noob I just installed Ubuntu a couple days ago.

I been at this for 3 hours I am about ready to take a 45 automatic and blow up this damn computer lol

---

### Post by aysiu on 2005-09-27
Which .deb did you download from the Opera website? Make sure you get the Debian-static one, not the Ubuntu one (I know that sounds wrong, but it's the way it is).

---

### Post by tehwa on 2005-09-27
It seems you saved the opera install package to your Home directory. If you open a fresh terminal window, you should start in your home directory, and be able to run the dpkg command to install from there.

By the look of your previous output, that command will be ```
sudo dpkg -i opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb
```

If you recieve the same dependancy error you mentioned above, it can be corrected with the following command:```
sudo apt-get install libqt3c102-mt
```

When hellothere55 mentioned typing "-o" he was referring to a feature of gnome-terminal, where if you type the first letter of a filename, then press 'Tab' it will autocomplete the filename. This saves typing time. You can test it in your home directory by typing "cd D", then before hitting return, pressing Tab. You will see the command autocompleted as "cd Desktop".

---

### Post by mumushi on 2005-09-28
username@box:~$ sudo dpkg -i xxx.deb opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb
dpkg: error processing xxx.deb (--install):
cannot access archive: No such file or directory
Selecting previously deselected package opera.
(Reading database ... 58048 files and directories currently installed.)
Unpacking opera (from opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb) ...
dpkg: dependency problems prevent configuration of opera:
opera depends on libqt3c102-mt; however:
Package libqt3c102-mt is not installed.
dpkg: error processing opera (--install):
dependency problems - leaving unconfigured
Errors were encountered while processing:
xxx.deb
opera
username@box:~$




i also have the same problem . can anyone please help me how to install libqt3c102-mt and other dependencies that opera needs? 

Any help would be greatly appreciated. Thanks in advance.

---

### Post by Vulpus on 2005-09-28
When Zetova said:

[I][COLOR="Blue"]Of course changing xxx to the name of your file - in my case the file was called opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb so you would use the following:[/[/COLOR]I]

He obviously didnt make it clear you should change xxx to the name of the file! :rolleyes: 

One of my favourite sayings is "never overestimate the inteligence of the customer"!

Though to be fair, i have done the same thing myself before now.

---

### Post by Vulpus on 2005-09-28
[QUOTE=Eejay]Update: I knew it everyone has been complaining about Ubuntu having dependency issues with Opera I tried just about everything to install this web browser here is the latest error message.

username@box:~$ sudo dpkg -i xxx.deb opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb
dpkg: error processing xxx.deb (--install):
 cannot access archive: No such file or directory
Selecting previously deselected package opera.
(Reading database ... 58048 files and directories currently installed.)
Unpacking opera (from opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb) ...
dpkg: **dependency problems prevent configuration of opera:**
 opera depends on libqt3c102-mt; however:
  Package libqt3c102-mt is not installed.
dpkg: error processing opera (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xxx.deb
 opera
username@box:~$[/QUOTE]

The reason you are getting the 'no such file or directory' is that there is no such file or directory called xxx.deb!

xxx.deb is just an example.  You need to actually type in the name of the file.  i.e.

sudo dpkg -i opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb

NOT 

sudo dpkg -i [COLOR="Red"]xxx.deb [/COLOR]opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb

---

### Post by Eejay on 2005-09-28
Oh believe me I tried everything something is definitely wrong the download is located inside of the home directory 

I typed this command into the terminal sudo dpkg -i opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb

Then received this error message, pasted below.

username@box:~$ sudo dpkg -i opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb
(Reading database ... 58150 files and directories currently installed.)
Preparing to replace opera 8.50-20050916.5 (using opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb) ...
Unpacking replacement opera ...
dpkg: dependency problems prevent configuration of opera:
 opera depends on libqt3c102-mt; however:
  Package libqt3c102-mt is not installed.
dpkg: error processing opera (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 opera
username@box:~$

After that I typed ,  this command into the terminal.  sudo apt-get install libqt3c102-mt

The error message is posted below.

username@box:~$ sudo apt-get install libqt3c102-mt
Reading package lists... Done
Building dependency tree... Done
Package libqt3c102-mt is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libqt3c102-mt has no installation candidate
username@box:~$

I don't get it somethings gotta give.

---

### Post by Zotova on 2005-09-28
Sorry for any confusion I caused when saying xxx.deb - I did mean what the above poster said. Anyhow, here is a fix to your problem.

I have hosted the missing file which you require on my server. So follow these instructions and we should get opera working.

1. Open terminal
2. wget [http://www.shanghai.me.uk/linux/libqt3c102-mt.deb](http://www.shanghai.me.uk/linux/libqt3c102-mt.deb)
3. sudo dpkg -i libqt3c102-mt.deb
4. If there are any dependancy issues then please install the missing packages via synaptics. Once done then perform task no.3 once again. Once installed then move to no. 5
5. wget [http://www.shanghai.me.uk/linux/opera.deb](http://www.shanghai.me.uk/linux/opera.deb)
6. sudo dpkg -i opera.deb

Opera should now be installed on your system.

I hope that works for you.

---

### Post by Eejay on 2005-09-28
Zotava thanks it worked Opera did not show up inside of the application menu, after the browser was installed. I though to myself oh no, not again I damn near punched the computer screen, I been at this for days so I opened the Run terminal, then typed Opera into the run bar, the browser pooped up, and welcomed me to opera web browser everything is working fine.

Thanks for all the replies I appreciate them very much.:smile:

---

### Post by Zotova on 2005-09-29
Opera not showing in the menus is normal, the same happened to me. If you wish to add it to the menus you can use smeg and everything then works perfectly.

---

