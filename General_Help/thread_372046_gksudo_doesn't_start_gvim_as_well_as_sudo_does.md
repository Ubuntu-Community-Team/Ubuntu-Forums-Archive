---
title: "gksudo doesn't start gvim as well as sudo does"
date: 2007-02-27
forum: General Help
---

### Post by Phrawm48 on 2007-02-27
IF I use *gksudo gvim*, THEN gvim opens without reading my vim or gvim configuration files.  For example, font name and size (set in .gvimrc), line numbering, and syntax highlighting (set in .vimrc) are NOT loaded.  I must set them manually from within gvim.

Conversely, IF I use *sudo gvim*, THEN all the aforementioned preferences are correctly loaded.

Should I be using gksudo to start gvim?  If yes, how can I made gksudo include my otherwise working *gvim* preferences?

Cheers & thanks,
Ric
SFO

---

### Post by zvacet on 2007-02-28
Why don´t you use gvim icone?

---

### Post by Phrawm48 on 2007-02-28
*Why don´t you use gvim icone?*

Well, ok, but first -- what is *icone*?

> 
ric@ric-desktop:~$ apropos icone
Gnome2::IconEntry (3pm) - (unknown subject)


If I try *gvim icone*, it merely produces a new empty file for editing.  Conversely, *icone gvim* results in "command not found".

So, I'm not sure how icone might (or might not) help me...(?)

Cheers & thanks,
Ric
SFO

---

### Post by xenmax on 2007-02-28
> I use *gksudo gvim*, THEN gvim opens without reading my vim or gvim configuration filesVim config files in your ~/ dir are only picked up if you are running as yourself. When you are superuser, it picks up config files from system wide areas - such as /etc/vim/gvimrc
Since i dont use gksudo gvim often i haven;t  bothered, but if you find it necessary, move your config settings to that file as well.
Note that settings in this file affects *all users*.
EDIT: These settings however can be over-ridden by those in ~/.gvimrc when you are running as yourself.

---

### Post by Phrawm48 on 2007-02-28
> Vim config files in your ~/ dir are only picked up if you are running as yourself.

But IF I use *sudo gvim*, THEN my preferences are loaded properly.  The point being that *sudo* loads my user-level preferences but *gksudo* doesn't...

Cheers & thanks,
Ric
SFO

---

### Post by jvc26 on 2007-02-28
Sudo runs with root privileges but uses the user's configuration file, whereas gksudo uses root's Firefox configuration file. For more info see: [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)
Il

---

### Post by zvacet on 2007-02-28
In format menus create launcher wherever you want Vim to be.
name:GVim Text Editor
coment:editing text files
command:gvim -f %U
Icone will find in usr/share/pixmaps
Good luck

---

### Post by aysiu on 2007-02-28
> **Illuvator said:**
> Sudo runs with root privileges but uses the user's configuration file, whereas gksudo uses root's Firefox configuration file. For more info see: [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)
Il
Yes. In fact, the behavior described (*gksudo* uses root's config files; *sudo* uses user's config files) is precisely why *gksudo* should be used, so as not to accidentally change ownership of user files to root.

If you want to use your user config, why are you running the app with *sudo*?

---

### Post by Phrawm48 on 2007-02-28
> If you want to use your user config, why are you running the app with sudo?

The short answer is to edit, or more accurately to be able to save changes to, such files as *xorg.conf*, *fstab*, et al.

It had  heretofore seemed to me (although I may not have been paying sufficient attention.   Sigh...) that *sudo gvim* was doing what I wanted.  But then I read a comment that one should instead use *gksudo* for GUI applications.

I followed this up with a quick peek at *man gksudo* which tells me that "gksudo is a frontend to sudo".  Aha, I thought.  I'll try using *gksudo gvim*.

Alas, *gksudo*, it seems, is not merely a graphics frontend to *sudo*: it uses different initialization profiles.

Thanks everyone for all your efforts to help but his seems to be yet another of those Linux things where the more information I acquire the less I understand...

Cheers & thanks 'gain,
Ric
SFO

---

### Post by aysiu on 2007-02-28
> **Phrawm48 said:**
> 
Alas, *gksudo*, it seems, is not merely a graphics frontend to *sudo*: it uses different initialization profiles. Yes, this is true--and, as I said before, precisely the reason you should use *gksudo* instead of *sudo*.

Using applications as root but with a user's profile risks screwing up ownership of user configuration files.

If you want, you can copy your profile to root's profile so that it's consistent. I don't know where *gvim*'s config lives, but let's assume it's /home/phrawm/.gvim. Just do ```
sudo mv /root/.gvim /root/.gvim.old
sudo cp -R ~/.gvim /root/.gvim
``` Then you'll have the same profile for root and user.

---

### Post by Phrawm48 on 2007-02-28
OK, thanks -- I copied my home directory's *.vimrc* and *.gvimrc* files to */root* and now *gksudo gvim* opens gvim with the desired initializations.

NOW, one more question.  What is the implication, then, of using *sudo vim* (note, _not_ gvim) to edit files such as *fstab* or *xorg.conf*?

Perhaps the question is better asked as, what's the high-level logic for editing system configuration files using **any** given text editor?  Always use *gksudo EditorName*, always use *sudo EditorName*, or...?

Then, too, I suppose the question pertains to editing files that are owned by some other user or group...(?)

Cheers & thanks 'gain,
Ric
SFO

---

### Post by aysiu on 2007-03-01
I don't know why it is the way it is, but I do know *sudo vim* should be okay because *vim* is a terminal (not a graphical) application.

---

