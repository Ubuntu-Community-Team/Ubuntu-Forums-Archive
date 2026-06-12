---
title: "Is there a program to automatically open a bunch of URLs?"
date: 2017-07-23
forum: General Help
---

### Post by PopsTheSailor on 2017-07-23
Hi, I'm looking for a new car and thus have about 10 or so URLs that I look at every day. I have them all saved in my email and bookmarked too. I'm lazy and don't want to open my browser or email and individually click on each link. Is there any program where I can list them all and have a "easy button" to click and it will open all of them for me? I'd even be willing to write a SIMPLE script file if there's a way to do it there and someone can give me a hint of the statement I would use to cause them to open.

---

### Post by #&amp;thj^% on 2017-07-23
See if this suits your needs: [https://superuser.com/questions/385207/how-to-open-a-list-of-urls-in-firefox-or-seamonkey](https://superuser.com/questions/385207/how-to-open-a-list-of-urls-in-firefox-or-seamonkey)

---

### Post by sudodus on 2017-07-23
You can create a super-simple script with one line. Assuming you use firefox to browse, it can look like this (but use your own web addresses)

```

firefox ubuntu.com launchpad.net ubuntuforums.org &

```

Or you can create a corresponding alias and store the alias in **~/.bashrc** near the other aliases

```

alias car-ads='firefox ubuntu.com launchpad.net ubuntuforums.org'

```

Run the alias in a terminal window with

```

car-ads

```

---

### Post by deadflowr on 2017-07-23
You can set firefox to open multi tabs at startup by adding urls to the startup section of Preferences >> general Home Page.
You set each url and then put a pipe in between them, like
```
ubuntu.com|someplace.com|etc|etc|etc
```
Firefox also allows you to set multiple profiles so you can set one for this and keep the existing one in place.
What I would do is
Open a terminal and run
```
firefox -ProfileManager
```
Create a new profile and name it cars.
Then let it open that new profile.
Then edit the home page settings.
Then exit, and restarts to see if it worked.
If successful I would then re-run the profilemanager command and this time select the default profile, so that firefox will reload the normal profile.

Now, to set a way to open that cars profile.
Easy way is to simply create a desktop file for it
Open a text editor and put something like this in it:
```
[Desktop Entry]
Name=Cars
Exec=firefox -P cars
Type=Application
Icon=firefox #<you can use any image you want, really

```
and save the file as cars.desktop
in the local user location ~/.local/share/applications.

Depending on Desktop environment if may be listed in other (or something like that) if using an old menu like mate or xfce, or may the system may need a restart, or logout/login for it to properly show if using unity or gnome.
(Or it may show up immediately)


Hope that makes sense and isn't too far out there.

---

### Post by Bucky Ball on 2017-07-23
If you're using Firefox, why not just install the extension 'Tab Groups' from 'Tools> Extensions> search for Tab Groups> Install'.

You can them make a tab group called, say, 'Cars' and have just your car tabs in there.

Quick and easy solution. Hope that helps and good luck.

---

### Post by dragonfly41 on 2017-07-23
Yet another idea.

You should have installed under Applications > Accessories a little utility called Actiona.   This is used for automating desktop tasks.

Create a directory to hold your Actiona scripts .. e.g. /home/yourid/actiona.

Launch Actiona.

Now there are several widgets to use but you will be interested in OpenURL widget under System category.

Drag OpenURL to your middle pane and insert the URL in field.

You can drag as many widgets as you choose.

You can refine the script by adding Message Box etc.

When the window is open you can select/deselect widgets (urls).

Now save the script with extension ascr.

When opened it will run through the widgets and launch multiple URL's.

---

### Post by SeijiSensei on 2017-07-24
I'd just put all the URLs into a Firefox folder.  Then you can right-click the folder and choose "Open All in Tabs."  Simple, easy, and nothing extra to install.

---

