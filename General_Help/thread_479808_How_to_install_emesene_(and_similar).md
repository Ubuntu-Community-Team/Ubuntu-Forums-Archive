---
title: "How to install emesene (and similar)?"
date: 2007-06-20
forum: General Help
---

### Post by bronze on 2007-06-20
Tried downloading emesene latest from sourceforge: [http://sourceforge.net/project/showfiles.php?group_id=168206]("http://sourceforge.net/project/showfiles.php?group_id=168206")

It's a .zip, with tons of .py's and a "application/x-shellscript".

The x-shellscript launches the app, but what I would really like is to know how to "install" it (in order to get it into the Applications menu, or atleast how to add a working entry into the Applications menu.

Thanks in advance.
Best regards,
bronze.

---

### Post by harty83 on 2007-06-20
Since there is no need to compile or anything, you can't really "install" it.  So this is what I would do.

Move the emesene folder to /opt

```
sudo mv ~/Desktop/emesene /opt
```

Make sure emesene is executable (mine wasn't upon downloading and unzipping)

```
sudo chmod +x /opt/emesene/emesene
```

Create a shortcut in the /usr/bin folder
```
sudo ln -s /opt/emesene/emesene /usr/bin/emesene
```

Then create a menu option by going to System -> Preferences -> Main Menu.  Click on Internet under menus then on New Item button on the right.  Fill in the name and "emesene" in the command.  Click on the "No Icon" and browse to /opt/emesene/themes/default and select an icon.  Click OK.

That should do it.

---

### Post by bronze on 2007-06-20
> **harty83 said:**
> Since there is no need to compile or anything, you can't really "install" it.  So this is what I would do.

Move the emesene folder to /opt

```
sudo mv ~/Desktop/emesene /opt
```

Make sure emesene is executable (mine wasn't upon downloading and unzipping)

```
sudo chmod +x /opt/emesene/emesene
```

Create a shortcut in the /usr/bin folder
```
sudo ln -s /opt/emesene/emesene /usr/bin/emesene
```

Then create a menu option by going to System -> Preferences -> Main Menu.  Click on Internet under menus then on New Item button on the right.  Fill in the name and "emesene" in the command.  Click on the "No Icon" and browse to /opt/emesene/themes/default and select an icon.  Click OK.

That should do it.

Very good reply. Thank you. But I have to admit, it still won't work. I did exactly as you wrote, but I think I know what the problem is. When I double click at the original file (now at opt/emesene/emesene), I get a prompt:
***TRANSLATED***
> "Do you want to run "emesene" or show the contents?"
"emesene" is a executable textfile"
"run in terminal" "show" "cancel" "run"

And if I right-click on the file --> Properties --> Open with tab: It's registered to be opened with "Text editing".

Is it supposed to be like this?
If I create a "link" (perhaps it's shortcut in english, but I think it's called link) and run it, I get the same prompt, but nothing happens if I press "run". If I follow your procedure, making a shortcut or "application starter", I don't even get a prompt. Nothing happens.

---

### Post by harty83 on 2007-06-20
Do you get the following if you run emesene from a terminal?  

```
alan@laptop:~$ emesene
python: can't open file 'Controller.py': [Errno 2] No such file or directory

```

If you do then open the emesene in a text editor and change 

```
python Controller.py
```

to 

```
python /opt/emesene/Controller.py
```

---

### Post by bronze on 2007-06-20
> **harty83 said:**
> Do you get the following if you run emesene from a terminal?  

```
alan@laptop:~$ emesene
python: can't open file 'Controller.py': [Errno 2] No such file or directory

```

If you do then open the emesene in a text editor and change 

```
python Controller.py
```

to 

```
python /opt/emesene/Controller.py
```

Yep, that was the problem. Thanks, mate.

---

### Post by pjalegria on 2007-08-14
I dont understand why Emesene is not in Feisty repository , is such a good IM client?????

---

### Post by Qu4k3R on 2007-10-04
> **pjalegria said:**
> I dont understand why Emesene is not in Feisty repository , is such a good IM client?????

It is very nice.. i have tried gaim, amsn, pidgin, and kde ones.. (kopete and others)

Emesene is very nice.. even for kde..

But why don't you "try" it?

EDIT: you got here a emesene site, [http://emesene.org](http://emesene.org) and [http://getdeb.net](http://getdeb.net) site. You just need to search until you find the download page of emesene.

---

### Post by mekas2024 on 2007-10-25
Hi guys, 

Im very interested on this messenger, specialy because i need a lot to be offline but able to chat with my company partners, so.... i did everything u say here, i have up n running emesene but the problem that i have its that never get online, i enter mi email and password an it display the window that its conecting but it never get online :S

DId someone know what could be ?

Thanks a lot i hope someone know!

Regards, 

Mekas

[[IMG]http://thumbnails.imajr.com/conecting_370319.png[/IMG]](http://imajr.com/conecting_370319)
[IMG]http://imajr.com/conecting_370319[/IMG]

---

### Post by carlosalvatore on 2008-03-27
to install emesene quickly and simple just add the repository to your sources list.

In a terminal window type:
```
sudo gedit /etc/apt/sources.list
```

Add at the bottom of the file this lines

```
# Emesene - Messenger 
deb http://apt.emesene.org/ ./
deb-src http://apt.emesene.org/ ./
```

then close and save sources.list

now again in the terminal type:

```
sudo apt-get update
sudo apt-get install emesene

```

And that's it.

Good luck! ;)

---

### Post by l_b on 2008-04-02
> 
```
sudo apt-get update
sudo apt-get install emesene

```

And that's it.

Good luck! ;)

This didn't work for me. I got a: Failed to fetch [http://apt.emesene.org/Sources.gz](http://apt.emesene.org/Sources.gz)  404 Not Found

---

### Post by l_b on 2008-04-02
Never mind. It worked fine. Just had to remove the deb-src from the list.

---

### Post by carlosalvatore on 2008-04-02
Only use this line in the sources.list

```
## Emesene
deb http://apt.emesene.org/ ./
```

and try again:

```
sudo apt-get update
sudo apt-get install emesene
```

Good luck, again..

---

