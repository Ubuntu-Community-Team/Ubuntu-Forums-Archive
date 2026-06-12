---
title: "Installing unofficial trello desktop client"
date: 2016-03-09
forum: General Help
---

### Post by markodd on 2016-03-09
Hello,

I'm trying to install the following unofficial trello desktop client: [https://github.com/danielchatfield/trello-desktop](https://github.com/danielchatfield/trello-desktop)

After downloading the "Trello-linux-0.0.1.zip" file, I get a file named "Trello". Doing

```
./Trello

```
Gives me the following error:

```
./Trello: error while loading shared libraries: libnode.so: cannot open shared object file: No such file or directory

```
How do I install this?

---

### Post by mastablasta on 2016-03-09
wow version 0.0.1 :)

instructions say:

> Linux[**Download**]("https://github.com/danielchatfield/trello-desktop/releases/latest") and unzip to some location.
To add a shortcut to the app, create a file in ~/.local/share/applications called trello.desktop with the following contents:
[Desktop Entry]
Name=Trello
Exec=/full/path/to/folder/Trello
Terminal=false
Type=Application
Icon=/full/path/to/folder/Trello/resources/app/media/Icon.png
 

I would say try with shortcut. Also maybe you will need to install a missing library libnode.so.

hint:
> No such file or directory

---

