---
title: "ubuntu without using terminal?"
date: 2014-07-04
forum: General Help
---

### Post by jc_le_mentec on 2014-07-04
Is it possible to use Ubuntu without ever using the terminal or command lines?
I want to install java for development purpose. I read that a good place to put it would be in usr/local.
but I can't get write access to it (while trying to extract the compressed downloaded file.i read that I need superuser privilege. Al I found was command line instructions. Can I ever get write access to any folder in my computer without ever using a terminal?
if there is some interest, I would be happy to elaborate on why I don't want to use command lines.
This is my first post here, new to linux and ubuntu, currently on mac os and windows 7 and writing this post from my ipad.

---

### Post by smirnich on 2014-07-04
If OpenJDK is sufficient, you can install it from the Ubuntu software center. If you need Oracle Java, I don't know how to do hat without using the terminal. But why not use the terminal?

---

### Post by mastablasta on 2014-07-04
yes you just need to run terminal as root. there used to be two terminal shortcuts one normal and one that had (root) written next to it.

anyway i am not sure what you are trying to do. as mentioend open JDK is in software center, oracle java has a PPA. you can open software cneter and then software sources and copy the PPA to sources. then update Soft. center, then oracle java will appear in software center.  click on it and click install.

---

### Post by coffeecat on 2014-07-04
I've moved this to General Help from Ubuntu, Linux and OS Chat because this sounds as though it's going to turn into a support thread.

> **jc_le_mentec said:**
> if there is some interest, I would be happy to elaborate on why I don't want to use command lines.

I  think you do need to elaborate because in my view that contradicts this:

> **jc_le_mentec said:**
> I want to install java for development purpose.

Any serious developer uses the command line at some point, even Windows users. 

To answer this:

> **jc_le_mentec said:**
>  Al I found was command line instructions. Can I ever get write access to any folder in my computer without ever using a terminal?

Yes, you can, by opening a root owned file browser, but that's not something any experienced user is likely to recommend. It's a potentially dangerous blunt instrument. As is a terminal with elevated privileges, of course, but you are better off getting comfortable with the command line, in my opinion. 

As you are new to Ubuntu I'll direct you to this community documentation page. Although indirectly related to your question, it is something that you would find useful to understand:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by 3rdalbum on 2014-07-04
> **jc_le_mentec said:**
> Is it possible to use Ubuntu without ever using the terminal or command lines?

Yeah, actually it's very possible. Not many people do it, but it definitely can be done. I do use the terminal, but I could choose to avoid it entirely if I wanted to. My father uses Ubuntu without touching the terminal; he is nearly 70 and doesn't know how to use the terminal.

> I want to install java for development purpose.

For computer programming, you'll need the terminal. 

> I read that a good place to put it would be in usr/local but I can't get write access to it (while trying to extract the compressed downloaded file.i read that I need superuser privilege. Al I found was command line instructions. Can I ever get write access to any folder in my computer without ever using a terminal?

To be fair, the command-line instructions for opening something as root are not exactly onerous. You could open the terminal and run this command:

```
gksudo nautilus
```

then everything you do within this file browser window will be done as root. So, you could navigate the file browser to where the compressed file is, double-click the file and then you'll be able to extract it to /usr/local or make any changes in the filesystem that you want to make. Within this window or any other windows that open as a result of using this window.

A while back somebody asked for a way of opening the root file browser window without opening the terminal. I have it at home - it's just a file you double-click to open the window.

Needing root/superuser permission to make system-wide changes is part of Linux's security system. It's part of what makes it safer and more secure than any of the other operating systems you use.

> if there is some interest, I would be happy to elaborate on why I don't want to use command lines.

Sorry, no... sounds like we've probably heard it before. Some of us have probably thought much the same as you in the past, until we realised the command-line has some advantages and actually isn't that difficult to learn.

---

### Post by buzzingrobot on 2014-07-04
No, use of the terminal is not needed for typical use of Ubuntu.

However, development, with Java or any other language, is not typical use.  Developers need an understanding of the Linux filesystem, permissions structure, bash, etc., even if they try to live in an IDE.

---

### Post by HermanAB on 2014-07-04
Why help and how to guides are usually using terminal commands is best answered with a counter question:
Have you ever tried to explain to someone how to do something on a GUI?

Furthermore, explanations can be copied and pasted into the terminal.  You cannot copy and paste commands into a GUI.

---

### Post by grahammechanical on 2014-07-04
It is completely possible to use Ubuntu without ever using the terminal provided (and this is important, so I will repeat it), provided we install applications through the Software Centre and accept the limited default set of modifications and do not start using the terminal to change the OS. In that case we will need to use the terminal to fix things. But there is always the non-terminal way of correcting any mess we make. It is called re-installing Ubuntu.

Linux gives us a great freedom to modify the OS but it also gives us the great freedom to break the OS. We can still be free without claiming every freedom possible but that means accepting limitations. And there is nothing wrong with that.

Regards.

---

### Post by jc_le_mentec on 2014-07-04
Thanks all for the feedback.
I tried [COLOR=#000000][FONT=Ubuntu Mono]gksudo nautilus
[/FONT][/COLOR]as I didn't have gksudo installed I got an error message indicating the command line to install it. So I copied and pasted this command and got gksudo apparently installed.
I tried again [COLOR=#000000][FONT=Ubuntu Mono]gksudo nautilus
[/FONT][/COLOR]and this time got the following error:
(nautilus:2432): GLib-GObject-WARNING **: invalid cast from 'GtkMessageDialog' to 'NautilusWindow'
**
ERROR:nautilus-window.c:2116:nautilus_window_get_slots: assertion failed: (NAUTILUS_IS_WINDOW (window))
So far it has been a little bit frustrating, but I am learning.

As for using the terminal, I find more easy, less error prone to drag files from one window to another. I don't ever need to remember the exact name of the files, just look and move. I will be less likely to copy the wrong file or do any other operation by mistake. I understand the terminal is used for more than just copying file. I am not trying to convince anyone, I just would like to get things done as simply as possible without having to learn a new syntax, and I prefer to click click click instead of type type type.

---

### Post by 3rdalbum on 2014-07-05
It doesn't matter if you get error messages in the terminal, as long as the root file browser window opens. Does it?

I agree with you about it being easier to drag files from one window to another. This activates the brain's spacial processing area, whereas if you copy files in the terminal you don't get that benefit and it feels more difficult to comprehend whereabouts everything is.

Did you know that the terminal can accept drag and drop? If you were using the terminal and you needed to type a filename or file path, you don't need to type - you can just drag and drop the file onto the terminal and it gets typed for you. Also, if you start typing a filename or foldername in the terminal and then hit Tab, it fills in the rest of the filename/foldername for you. Tab-completion works for several different things in the terminal too.

---

