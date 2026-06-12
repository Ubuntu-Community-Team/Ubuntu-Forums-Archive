---
title: "how can I edit ALL of my system folders under Root?"
date: 2007-10-18
forum: General Help
---

### Post by suchawato on 2007-10-18
I had a really frustrating morning.
I tried to install some really nice fonts as Root, but the system would not let me paste into my fonts folder!!!
How do I disable this "safety" feature.
I'll take the risk, it's my computer.
Thanks in advance,
-Stu

---

### Post by aysiu on 2007-10-18
This will help you:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by kellemes on 2007-10-18
> **suchawato said:**
> 
I'll take the risk, it's my computer.


:popcorn:
Good point, your absolutely right.

The link provided by previous poster explains it all.

---

### Post by suchawato on 2007-10-19
This is actully not what I meant.
I know how to log in as root, or sudo commands.
However it seemed as if even in root, I was not able to edit some folders the way I would have liked.
Perhaps my system was just running slow, but does anyone have any idea what I am talking about?
thanks
-Stu

---

### Post by aysiu on 2007-10-19
Name what folder and what command you're trying to run on it. Or, better yet, just run the command and highlight everything in the terminal (command, error messages, whatever) and paste everything back here for people to look at it.

That's the easiest way to diagnose the problem.

---

### Post by LanDan on 2007-10-19
don't know what you did, but it is possible...
[http://linuxhelp.blogspot.com/2005/11/make-your-files-immutable-which-even.html](http://linuxhelp.blogspot.com/2005/11/make-your-files-immutable-which-even.html)

---

### Post by suchawato on 2007-10-20
i believe it was fonts:/// I was not able to paste files in this directory.
Under /user/share/fonts I was able to cut and paste files. I finally was able to install them by pasting them here under /user/share/fonts/truetype. It was odd to me that I couldnt' paste them into the original folder I mentioned, even though I could see all of the existing fonts. Is fonts:/// a true folder, or just a visual display of all the fonts in the system?
-Stu

---

### Post by sstusick on 2007-10-20
Try copying and pasting the fonts into the > /home/<username>/.fonts directory.

---

### Post by LanDan on 2007-10-20
aaaahhhh,

no thats not a real foleder indeed, like susstick just said its likely ashortcut to thew folder in your /home , just like trash:///

---

### Post by Page on 2007-10-20
If i have to work in a system folder, I use  "sudo nautilus"  or "sudo dolphin".

It lets you do what you have to do, since either of those commands gives you a file manager with root permissions.  (just remember to chown any of your own files back to you, if you copy them to a new folder as root, since IIRC they would inherit root ownership in that instance)

---

### Post by aysiu on 2007-10-20
> **Page said:**
> If i have to work in a system folder, I use  "sudo nautilus"  or "sudo dolphin". Or, better yet, ```
gksudo nautilus
``` and ```
kdesu dolphin
```

---

### Post by suchawato on 2007-10-22
Why is "gksudo nautilus" and "kdesu dolphin", better than "sudo nautilus" or "sudo dolphin"?

Thanks for the responses.

---

### Post by LanDan on 2007-10-22
> **suchawato said:**
> Why is "gksudo nautilus" and "kdesu dolphin", better than "sudo nautilus" or "sudo dolphin"?

Thanks for the responses.

why don't people just use nano?

---

### Post by Nunu on 2007-10-22
to Sudo or not to Sudo... that is the question.

whats the difference between sudo and nano??

---

### Post by LanDan on 2007-10-22
sudo is short for SuperUserDo and gives you the omnipotent root priviliges
nano is a text editor you can use on the command line

sudo nano /etc/X11/xorg.conf for example

---

### Post by aysiu on 2007-10-22
> **suchawato said:**
> Why is "gksudo nautilus" and "kdesu dolphin", better than "sudo nautilus" or "sudo dolphin"?

Thanks for the responses.
Read this:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by suchawato on 2007-10-23
Hmm.
Interesting.
I'll definitely be sure to be aware of that when running root commands.
Thanks for the post!

---

