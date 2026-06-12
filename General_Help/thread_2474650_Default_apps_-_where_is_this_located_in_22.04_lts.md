---
title: "Default apps - where is this located in 22.04 lts"
date: 2022-05-04
forum: General Help
---

### Post by jmichaels29 on 2022-05-04
To make a program the default app - where is this located in 22.04 lts's settings

---

### Post by TheFu on 2022-05-07
> **jmichaels29 said:**
> To make a program the default app - where is this located in 22.04 lts's settings

Huh?  Perhaps you could be a little clearer?  What are you trying to accomplish? Act like we are 5 yrs old and only know the minimum computer skills.

Please.

---

### Post by jmichaels29 on 2022-05-07
Sorry,

I want to look at the list of default apps for things like which program is set to be the default web browser, what program is the default DVD player, etc...

---

### Post by TheFu on 2022-05-07
> **jmichaels29 said:**
> Sorry,

I want to look at the list of default apps for things like which program is set to be the default web browser, what program is the default DVD player, etc...

On my system, when I right click on the file type in the file manager, it shows the default application used to open that type of file.  From there, it can be changed once or forever.

This has ZERO impact from a CLI interface.

---

### Post by jmichaels29 on 2022-05-07
ok, thanks

Somewhere in settings, I seen before, that one can select which program will open a particular app (not file type I think, I can't recall) - can't seem to get back to that screen in settings (somewhere).   But I'll use your suggestion.

Also, I can't seem to get VLC to open when a DVD is inserted into the desktop.  Perhaps that should be put in a new thread.   

Thanks

---

### Post by GhX6GZMB on 2022-05-07
I'm on Lubuntu which is not the same, but...
In your file manager, just right click on the file you want to open and select the application. This will then become the primary application for opening the file.

---

### Post by DuckHook on 2022-05-07
I assume you are using vanilla Ubuntu, therefore Gnome?

Settings &#8594; Default Applications

On mine, there are only six categories. It's not really of much use, but it covers the six most important.

For other file types, as per previous posters, you can define/redefine the default app through Nautilus every time you choose an app to open a specific type of file. This setting lasts until you repeat the process and choose a different app.

---

### Post by TheFu on 2022-05-07
> **jmichaels29 said:**
> ok, thanks

Somewhere in settings, I seen before, that one can select which program will open a particular app (not file type I think, I can't recall) - can't seem to get back to that screen in settings (somewhere).   But I'll use your suggestion.

Also, I can't seem to get VLC to open when a DVD is inserted into the desktop.  Perhaps that should be put in a new thread.   

Thanks

For a very few applications, there are XDG.... settings.  These are controlled in the ~/.config/ somewhere, perhaps related to the mimetypes settings on the system. IDK. The **xdg-settings** program will show, set and get specific answers.  On my system, because I don't use any DE, 
```
$ xdg-settings --list
Known properties:
  default-url-scheme-handler    Default handler for URL scheme
  default-web-browser           Default web browser

$ xdg-settings get default-web-browser
firefox.desktop
```

There is also xdg-open which is what actually gets called with the different data files to be handled by looking up the default applications from somewhere.

```
$ xdg-open 'http://www.freedesktop.org/'
$ xdg-open /tmp/foobar.png

```

There's also xdg-mime which should show the answers for the types of files and which program gets used to open it.

When I ran 
$ xdg-open  ~/.ssh/config
**geany** was used to open the file. I suspect I set geany as an editor to be used somewhere in a GUI about 2 yrs ago. 
The value of my EDITOR environment variable was ignored, which sorta pisses me off. There shouldn't be multiple answers for the same question.  PAGER is another, similar environment variable. These 2 have been part of Unix systems for probably 50 yrs now.  The PAGER is the viewer that shows output 1 page at a time, **less** or **more** are the most common answers, with less having more features, but a nasty habit of clearing the screen at the end of a paging session. There's an option to disable that, thankfully.

I cannot fathom that 22.04 would be any different, especially if using the Gnome4 DE.

---

