---
title: "Help with Nautilus-Actions Configuration Tool"
date: 2016-03-30
forum: General Help
---

### Post by Kentrino on 2016-03-30
Hello everyone!

I am a total newbie when it comes to Ubuntu/linux in general, and I have a quick question! :)

I am using a program called Qnapi, to automatically download subtitles for my movies, and it works very good.. When installed in Windows, it allows to right click on the movie file, and then there will be an option to "Download Subtitles", and this app opens, and searches for the subtitle in question. Unfortunately this option does not appear in Ubuntu after installing the application. I have to manually open the application, then browse for that movie file (since I am totally new to the file architecture in Ubuntu, this is quite a cumbersome task for me). 

I've done some "research" and found out that "Nautilus-Actions Configuration tool" allows me to program a specific command, and that it will appear when I right click a file.
Now, since I have literally no clue as to which commands/actions are needed to create such a shortcut, I am kindly asking if anyone would be able to help me?

I have qnapi installed, and I want to be able to right-click the movie file, then have an option such as "Find subtitle", and for this command to tell qnapi that qnapi should search for a subtitle for this file.
Is this possible? :)

Cheers

Kent

---

### Post by dragonfly41 on 2016-03-30
I can suggest one approach I'm currently using for another desktop automation workflow .. but it is not the only approach you can try.

Check under Ubuntu > Accessories if you have Actionaz installed.   Or just run in terminal .. actionaz .. to see if it launches.
Otherwise install.

Then in Actionaz GUI you can target a program such as Qnapi and execute actions.
You can also run bash scripts or other scripts from an Actionaz wrapper script.

After testing any Actionaz script you can run script in background mode which does not show the Actionaz GUI.

Actionaz runs in both Linux and Windows. 

I don't know if Nautilus-Actions Configuration Tool has same features.

The general search pattern for such tools would be "automation tools".

Selenium is another automation tool.  And AutoHotKey in Windows is similar to Actionaz.


[Later edit]

It may be that you prefer to add actions to Nautilus File Manager if you are using this to manage movie files. Look also at Thunar..

[http://www.howtogeek.com/116807/how-to-easily-add-custom-right-click-options-to-ubuntus-file-manager/](http://www.howtogeek.com/116807/how-to-easily-add-custom-right-click-options-to-ubuntus-file-manager/)

Perhaps I should add that you can use both Nautilus-Actions to run from Nautilus context manager any Actionaz scripts you develop to extend the automation.

*i.e. using the tools in tandem.*

Actionaz scripts (with extension ascr) are made executable and can be run as any other command line script.

So you would create a Nautilus command "Find Subtitle" which runs an Actionaz script to automate Qnapi app.

One feature of Actionaz is that you can target images such as buttons on Qnapi window.

---

### Post by mc4man on 2016-03-30
The qnapi.desktop file is deficient. It needs a %aletter added to the end of the Exec= line to show in the context menu. Easy to do, copy & paste below into a terminal, then press enter to run.
```
cp /usr/share/applications/qnapi.desktop ~/.local/share/applications/
```
Then to edit the file - 
```
gedit ~/.local/share/applications/qnapi.desktop
```

On the Exec=qnapi line add a %U to end with a **space after qnapi**, see screen
Then save file.

The first time you r.click on a video file you'll need to go into the context menu a bit deeper, after that it'll be right there.
(by deeper =  Open with > Other application > View All Applications

---

### Post by Kentrino on 2016-03-30
Thank you very much for your thorough answer! :)

I played a bit around with Nautilus-Action configure, with big help from the link you posted.

I simply put the command to qnapi -q (proud that I found this from some google-foo) and then a %f as parameter, and it works!

Thanks

EDIT: Well, thanks mc4man, I was wondering why qnapi didnt show as an option when choosing which app to open the file in.. Thanks so much! :)

---

