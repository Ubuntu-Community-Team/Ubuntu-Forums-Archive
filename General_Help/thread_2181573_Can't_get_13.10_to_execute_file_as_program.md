---
title: "Can't get 13.10 to execute file as program"
date: 2013-10-18
forum: General Help
---

### Post by El Zoido on 2013-10-18
Hello!

Today I upgraded to 13.10 (from 12.04 LTS) and now have a somewhat annoying issue.
I can't get Ubuntu to execute a file by double clicking.
This seems to happen with all the (text) files I tried so far, but to give a specific example:
I have an installation of Matlab on my pc, but for whatever reason, the installer always fails to provide a link, so I helped me by placing a link on the desktop, or by creating a small script pointing to the matlab file and marking "allow to execute file as program". 
Double click would bring up the option to execute the file and matlab would start. Worked good enough...

Now with 13.10, whenever I try to execute it, it just opens gedit, so the only way to start matlab is by using the terminal.
Not that this is a show-stopper, but it's an inconvenience.

Anyone got an idea why 13.10 refuses to execute the files?

---

### Post by varunendra on 2013-10-19
> **El Zoido said:**
> Now with 13.10, whenever I try to execute it, it just opens gedit

From Ubuntu 13.04 onwards, the default behaviour of the file manager is to open the file as text even when it is made executable. You can change this in the file manager's settings though -

Open any folder > go to **Files > Preferences > Behaviour tab > select "Ask each time"** option under "Executable Text Files" section.

---

### Post by okkadiroglu on 2013-10-19
Hi,

I have similar problem. When I click an icon on my desktop, Files 3.8.2 crashes and the icons that are on the Desktop screen disappears. When I start Files again the icons return on the screen. I can navigate directories on the Files Places and Bookmarks but can not open/start any file or directory on the list on the Files screen. I did what is recommended by Varunendra but nothing changed.

---

### Post by varunendra on 2013-10-19
> **okkadiroglu said:**
> I have similar problem. When I click an icon on my desktop, Files 3.8.2 crashes and the icons that are on the Desktop screen disappears. When I start Files again the icons return on the screen. I can navigate directories on the Files Places and Bookmarks but can not open/start any file or directory on the list on the Files screen. I did what is recommended by Varunendra but nothing changed.

That ^^ is not really a 'similar' problem, not even remotely close.

Your problem seems to be a Nautilus or some other bug totally crashing the file manager, while the topic in this thread is about a deliberate, intentional behaviour of opening text files in text editor even if marked as executable.

You should start a new thread, providing a detailed description of the problem, with sufficient background info (when it started happening, after an upgrade or a fresh install, etc.), and ask for help on it.

---

### Post by El Zoido on 2013-10-19
> **varunendra said:**
> From Ubuntu 13.04 onwards, the default behaviour of the file manager is to open the file as text even when it is made executable. You can change this in the file manager's settings though -

Open any folder > go to **Files > Preferences > Behaviour tab > select "Ask each time"** option under "Executable Text Files" section.

Thanks for the answer! Will check when I'm back at work on monday.

It does kind of raise the question though, why someone thought it would be a good idea to open executables as text files by default.
After all executing them after marking them as executable is kind of the point behind it, isn't it?

---

### Post by grahammechanical on 2013-10-19
It is not often understood that most of the utilities in Ubuntu are Gnome utilities. So, when there are Changes to Gnome Nautilus that people do not like they blame Ubuntu when in fact it is Gnome organisation that is making the change. Ubuntu has moved away from the icon cluttered desktop design of Microsoft. We have not had the option to create desktop launchers for a while. I have heard that is it still possible to create a desktop launcher and I have a Windows program runing under Wine that puts an icon on the desktop and that will launch that program. So, things are possible. But things are changing all the time.

Regards

---

### Post by El Zoido on 2013-10-19
Oh, I'm aware of the fact that Ubuntu is using Gnome as the base for the Unity Shell.
Also, I'm not complaining, I'm merely wondering why that decision was made.

Anyway, I guess I know the solution to the problem now, so all is well. :)

---

### Post by varunendra on 2013-10-19
> **El Zoido said:**
> It does kind of raise the question though, why someone thought it would be a good idea to open executables as text files by default.
After all executing them after marking them as executable is kind of the point behind it, isn't it?

I agree. Probably it was to avoid confusion and/or 'accidental' execution by new users who don't understand that much about executables.

In my experience so far, most users who can differentiate between executables and non-executables prefer (kinda habit) to run it via termianl (./<file> or sh <file>). While consider a newbie who may get confused when he downloads a tar.gz archive, reads some online guide to patch a file in it, double-clicks to open it and is presented with a scary dialogue box instead of opening it because all of the files in it are executables (I'd put realtek drivers on top of the list of such packages). :P

With its new looks, obviously Gnome is focusing on the dubious term "user-friendliness" and is purposefully dumbing down the GUI for the same purpose. So looks like a part of that 'development' to me.

---

### Post by El Zoido on 2013-10-19
> **varunendra said:**
> 
With its new looks, obviously Gnome is focusing on the dubious term "user-friendliness" and is purposefully dumbing down the GUI for the same purpose. So looks like a part of that 'development' to me.

I doubt that it's an improvement of user-friendliness, though.
The dialogue box at least gave you the possibility to execute it (as it should when it is marked as executable), yet with that change you have to run it from terminal, or change the default behavior.
Now I can do either, but it's a) additional steps and b) removes a perfectly fine possibility from the GUI.

---

### Post by El Zoido on 2013-10-22
Ok, it's complicated a bit because I uninstalled the appmenu/global menu (I don't like that feature on large monitors, I think it's increasing distances I have to move with the mouse too much), but that seems to completely remove the menu bar for Nautilus/Files. That means, I can't access the preferences that way.

However, instead of simply marking my file as executable, I have instead made a .desktop file out of it, which works better.

Edit: I now also managed to get the full menu into Nautilus/Files without appmenu, so I could change the default settings to something more sensible.

---

