---
title: "Accessing files in via File Manager"
date: 2015-06-25
forum: General Help
---

### Post by amoun on 2015-06-25
Trusty 14.04


When I use the default programme called by the [Files] icon in the Unity Launcher bar I have problems opening certain files.

My /var/www/ is now in my home directory under websites/ The user and group being www-data

I have no problem with permissions and can create, copy and edit files. However whereas I can open image files [*.jpg, *.png etc] with www-data www-data user and group, with a single click, in the file manager window, I can not open [.css, .php, *.html etc] with the same owner and group (www-data) It seems the default file manager won't let me open txt type files under such user and group.

If I create a new txt type file it will have me as user and group and will open

In the case of the files types that wont open: if they are www-data user and group right clicking does not show a default opening application nor does gedit show under [open with]

However gedit does show as the default application under properties >open with.
All actions under right click > properties > open with have no effect on what happens in the file manager window

Probably been trying to hard to resolve this and missing something simple.

I just want to lick on  file and it opens in my preferred app, but file manager window doesn't respond if it's a txt type file without me being the user.

Any help would be appreciated

Thanks

EDIT So it could be a file extension root cause, a file header or mime type. I don't yet know how the file manager assess file types and then decides whether to open it or not and why that relates to the owner.

Tried editing the /user/share/applications.deafults.list  and ~/.local/share/applications/mimeapps.list  by adding text/css but no luck

---

### Post by coldraven on 2015-06-25
I'm not a server expert but maybe you need to add yourself to the group www-data
```
useradd -G {[COLOR=#996633]group-name[/COLOR]} [COLOR=#663333]username[/COLOR]
```
Edit: You might need to prefix that command with sudo

---

### Post by amoun on 2015-06-25
Thanks for your consideration but I have permissions. As I mentioned I can open image files but not text files.

It appears to be that nautilus won't let me open text files in the group www-data even if I am the user.

Under properties > open with : [gedit] is the recommended program

Yet I can only open txt files (css, htm, php) etc by right clicking > open with > other application and click on the pre-selected [gedit]

---

### Post by amoun on 2015-06-25
SOLVED found [http://askubuntu.com/questions/150160/double-click-does-not-open-the-default-program](http://askubuntu.com/questions/150160/double-click-does-not-open-the-default-program)

The problem seemed to be that text files were seen as executable and nautilus/file manager didn't respond

Under file window as described in mentioned post : menu > Edit > Preferences > Behaviour > Executable Text Files >  select View executable text files when they are opened.

Had to be something simple

---

