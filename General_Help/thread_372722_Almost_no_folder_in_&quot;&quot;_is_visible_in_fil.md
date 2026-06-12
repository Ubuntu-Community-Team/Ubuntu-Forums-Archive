---
title: "Almost no folder in &quot;/&quot; is visible in file browser (except for home and media)"
date: 2007-02-28
forum: General Help
---

### Post by Lord Darth Vader on 2007-02-28
I recently noticed that the only folders visible in "/" in file browser are "home" and "media".

I used to see all the folders in file browser. Whenever I type the exact address of any folder in the address bar, I can see the contents. Therefor I assume that there is nothing wrong with the permissions.

Any idea what has changed?

---

### Post by an.echte.trilingue on 2007-02-28
That was done to try to make the UI simpler.  Typically speaking, if you need to go into the other folders, you know what you are looking for, whereas the UNIX file structure is confusing as hell for people who don't care to get to know it.  It is only like that at a GUI level.  If you ls  / it is all still there.

Maybe a good idea, maybe not, personally I like it that way.

Take care
-mat

---

### Post by Lord Darth Vader on 2007-02-28
I see your point. The problem is that it was not like this and I used to SEE all the folders in file browser. As far as I can remember I haven't change any setting in this area.
Personally speaking, I prefer to see all my folders!

---

### Post by eantoranz on 2007-02-28
There is an option to allow all files to be displayed. On konqueror, you have to enable "show hidden files". That should make it.

---

### Post by Lord Darth Vader on 2007-02-28
I am using gnome. I should say that I installed KDE in my ubuntu a couple of days ago but I didn't like it that much so I un-installed it completely. I guess it happened after this un-installation and again I can guess that KDE has changed something in my file browser. 

However, you are right in pointing out that enabling "show hidden file" solve the problem. 
The question is whay this has happened and how can I make it like before in my dear gnome?! Should I change permission and properties of every single folder?

---

### Post by Ramses de Norre on 2007-02-28
Is this in nautilus? I see all my directories when I go to / ...
And not to be offensive but how stupid is it to hide them without an option to unhide them???
Like people who do know the file structure like to type in paths manually every time... why have you got a file manager then, that's the same as cli.
And I can imagine not everyone likes cli.

---

### Post by Lord Darth Vader on 2007-02-28
Problem solved!

I just found a file in "/" by the name of ".hidden" .
It simply contains the names of folder that should be hidden when "show hidden files" is disabled. I simply edited that file and erased that list.  That simple!

I didn't even know such a file exists!

---

### Post by Ramses de Norre on 2007-02-28
Woow that's awesome! I've been already looking for such a feature to hide files without changing their name.
This works in every folder, thanks a lot for telling about this!

---

### Post by Lord Darth Vader on 2007-02-28
Pleasure!

---

### Post by x1a4 on 2007-02-28
> **Lord Darth Vader said:**
> Problem solved!

I just found a file in "/" by the name of ".hidden" .
*<snip>*


*/.hidden* is a symlink pointing to */etc/kubuntu-default-settings/hidden-root*

---

### Post by Lord Darth Vader on 2007-02-28
> **x1a4 said:**
> */.hidden* is a symlink pointing to */etc/kubuntu-default-settings/hidden-root*

So I am right in thinking that this happened since I installed KDE in Ubuntu. But now that I have uninstalled it completely, why this file is still in use? Is it something common between gnome and KDE?

---

### Post by x1a4 on 2007-02-28
> **Lord Darth Vader said:**
> So I am right in thinking that this happened since I installed KDE in Ubuntu.

Yes, it happened when you installed KDE.  If you only want dot files to be hidden, you can safely remove those KDE files. Or better still, rename them, this way when you change your mind you can just rename them back.

>  But now that I have uninstalled it completely, why this file is still in use? Is it something common between gnome and KDE?

Not exactly, but as you saw some GNOME apps (and Xfce for that matter as I had the same problem after getting rid of KDE) do make use of it.  It's part of a push towards standardization.  If you have multiple DEs installed and don't want to see certain system directories you can set it in one, and have it like this in all (or most at least) without having to make the same change multiple times.

---

