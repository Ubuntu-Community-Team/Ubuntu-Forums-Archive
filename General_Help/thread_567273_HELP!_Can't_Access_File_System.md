---
title: "HELP! Can't Access File System"
date: 2007-10-04
forum: General Help
---

### Post by CheeseQueen452 on 2007-10-04
I don't know how this happened, but I can't access "file system" when I open the file browser. I click on it, & it just reloads the file browser which shows my home/user directory. What do I do? HELP!!!

---

### Post by CheeseQueen452 on 2007-10-04
Well, it appears I can't access ANY folder in my file browser. Even my personal folder with all my music & pictures is not accessible.

The only thing I did today was try to install the mplayer plugin, which first lead me to install several packages to resolve the dependencies, in order to install the mplayer plugin. I also had to remove some packages, but I doubt they caused this issue. I don't remember what they were, unfortunately, since I went through a very lengthy process just to install the plugin.

I know it won't be easy to help me without much info, but if anyone can clue me in as to what could cause this & how to fix it, I'd be very greatful!!

---

### Post by CheeseQueen452 on 2007-10-04
Can anyone help?

---

### Post by CheeseQueen452 on 2007-10-04
Anyone?

---

### Post by CheeseQueen452 on 2007-10-04
*bump*

---

### Post by bodhi.zazen on 2007-10-04
Open a terminal

enter ```
nautilus /
```

Is that what you wanted ? If not, what is wrong ? error message in the terminal ?

---

### Post by CheeseQueen452 on 2007-10-04
Well, that opened the "file system" directory, but when I clicked on a folder, the same thing happened as I described in my original post. I can't open any folders. I don't see any error messages.

> **bodhi.zazen said:**
> Open a terminal

enter ```
nautilus /
```

Is that what you wanted ? If not, what is wrong ? error message in the terminal ?

---

### Post by bodhi.zazen on 2007-10-04
My guess is that you are looking at a permissions issue.

Close nautilus and re-open it with :

```
gksu nautilus /
```

Careful, you are running as root ...

---

### Post by CheeseQueen452 on 2007-10-04
This is what the terminal said when I tried to open a folder:

(nautilus:5841): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Initializing gnome-mount extension

** ERROR **: file nautilus-navigation-window.c: line 834 (activate_nth_short_list_item): assertion failed: (index < g_list_length (window->details->short_list_viewers))
aborting...


Now what?

> **bodhi.zazen said:**
> My guess is that you are looking at a permissions issue.

Close nautilus and re-open it with :

```
gksu nautilus /
```

Careful, you are running as root ...

---

### Post by bodhi.zazen on 2007-10-04
The "Warning" is a know bug and can be ignored.

The Error, however, is more problematic ...

What version of ubuntu are you running ?

Try filing a bug report, although that does not help you much ...

---

### Post by CheeseQueen452 on 2007-10-04
I'm running Ubuntu 7.0.4. I looked up Nautilus in synaptic, & a few of the dependencies are packages that I recall installing before I was able to install the mplayer plugin. When I installed some of those packages, I got a warning that an older version was available which is more fully supported. I ignored the warning. Perhaps that's what caused the problem I'm now having?

When Ubuntu 7.10 is released in 2 weeks, will that upgrade resolve the issue?

> **bodhi.zazen said:**
> The "Warning" is a know bug and can be ignored.

The Error, however, is more problematic ...

What version of ubuntu are you running ?

Try filing a bug report, although that does not help you much ...

---

### Post by bodhi.zazen on 2007-10-04
You would think so ...

I assume you mean 7.10 ;)

---

### Post by CheeseQueen452 on 2007-10-05
That's what I said..... So, bottom line..... how do I fix this?

> **bodhi.zazen said:**
> You would think so ...

I assume you mean 7.10 ;)

---

### Post by CheeseQueen452 on 2007-10-06
Can anyone help?

---

### Post by CheeseQueen452 on 2007-10-07
Any help would be appreciated!

---

### Post by CheeseQueen452 on 2007-10-09
*Bump*

---

