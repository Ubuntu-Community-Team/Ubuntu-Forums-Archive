---
title: "How to restore Desktop folder"
date: 2016-03-02
forum: General Help
---

### Post by schnuckenack2 on 2016-03-02
Hello

I copied my old /home directory into the new installation. In the old installation, the /Desktop folder was called /Arbeitsfläche (Germanized). Now I wanted to achieve that the contents of /Arbeitsfläche would be shown on the desktop. I thought, if I deleted /Desktop and renamed /Arbeitsfläche accordingly, it would work out. It didn't work out and instead it now shows all contents of /home/Schnuckenack on the desktop. 

How do I tell the system that /home/Desktop is the desktop?

Thanks

---

### Post by egeezer on 2016-03-02
Create a new /Desktop directory and put the contents of the old /Arbeitsfläche  into it.

---

### Post by yancek on 2016-03-02
You're posting conflicting information.  You initially state "I wanted to achieve that the contents of /Arbeitsfläche would be shown on the desktop" and later state " It didn't work out and instead it now shows all contents of /home/Schnuckenack on the desktop" which is exactly what you initially say you wanted.  What exactly do you want?  If you have all the contents of your Desktop displayed on your Desktop and want them in a Desktop directory, just re-create the Desktop directory as suggested.  Your post isn't really clear.

---

### Post by mcgess on 2016-03-02
Normally your Desktop directory would be /home/Schnuckenack/Desktop rather than /home/Desktop

If you really want the directory to be /home/Desktop (not sure why you would but maybe for sharing a desktop setup between different users) you could create a symbolic link.

---

### Post by schnuckenack2 on 2016-03-03
> **yancek said:**
> You're posting conflicting information.  You initially state "I wanted to achieve that the contents of /Arbeitsfläche would be shown on the desktop" and later state " It didn't work out and instead it now shows all contents of /home/Schnuckenack on the desktop" which is exactly what you initially say you wanted.  What exactly do you want?  If you have all the contents of your Desktop displayed on your Desktop and want them in a Desktop directory, just re-create the Desktop directory as suggested.  Your post isn't really clear.

Hello yancek,

What I said was the following:

**What I want**
 The contents of /home/Schnuckenack/Desktop shown on the desktop. 

**What it does instead**
It shows the contents of /home/Schnuckenack on the desktop

**Although I...**
created /home/Schnuckenack/Desktop and put the files to be shown on the desktop in it

I guess the system doesn't recognize /home/Schnuckenack/Desktop, well, as the *desktop*. But how do I tell the system that it *is* the desktop-folder? 

I lack the knowledge &#8222;of what sort&#8221; those /Desktop and /Images and /Documents, /Videos, /Music and /Downloads folders are anyway. Are they symbolic links or anything like that? 

Thanks

---

### Post by mcgess on 2016-03-03
I use Lubuntu so I'm not sure this will help on other versions but try looking in .config/user-dirs.dirs

---

### Post by schnuckenack2 on 2016-03-04
> **mcgess said:**
> I use Lubuntu so I'm not sure this will help on other versions but try looking in .config/user-dirs.dirs

Thanks, that solved my problem!

The variable just contained my home directory. I appended 'Desktop' and now everything is fine.

```
# in .config/user-dirs.dirs

XDG_DESKTOP_DIR="$HOME/"
```

How do I mark this thread as [SOLVED] ?

---

### Post by mcgess on 2016-03-04
Glad your problem is solved.

The instructions for marking the thread as solved are here

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

