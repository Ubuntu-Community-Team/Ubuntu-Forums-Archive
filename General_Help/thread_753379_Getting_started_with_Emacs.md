---
title: "Getting started with Emacs"
date: 2008-04-12
forum: General Help
---

### Post by 7raTEYdCql on 2008-04-12
Can someone help me getting started with Emacs.

I mean i dont have a clue of how to open it and neither of how to run it.
Can someone help. I want to seriously lear about this much talked abouit text editor.

---

### Post by ibuclaw on 2008-04-12
Hi, I only know the very basics of emacs to get me through programming stuff in C.

But, from the top.
To Install it, type in the terminal
```
 sudo apt-get install emacs 
```

And then to open a file in it
```
 emacs file.c 
```

Now when it starts, a splash screen will be displayed, just press any key to close this (Usually the down arrow or using the mouse to click on it is the best thing to do).
And your file will be shown.

One handy thing about emacs is that it recognises over a dozen programming languages and has automatic syntax colouring and beatifying of the layout.

Now if we open up some of the tabbed menus. File for example, you'll see the all the basic features of a normal text editor, plus a few extras. But you'll also notice some alien-looking keyboard shortcuts.
(C-x C-f), (C-x d), etc...

So to break any confusion about it. In emacs, you enter a series of keyboard controls to run the different features. Not just one shortcut. This makes sense, since emacs has well over 200 keyboard commands, so this is needed so they aren't restricted to a single 32 command set.

So, what does it  mean?
Well, 
**C** is the **Ctrl** key.
**M** is either the **Alt** or **Esc** key. it doesn't really matter which.
**C-M** is Ctrl+Alt together (or Ctrl+Esc together).
After that, all lower case letters are just the keys you press with Ctrl or Alt.

ie:
(C-x C-f) - This is **Ctrl+x** followed by **Ctrl+f**. You can hold down the Ctrl button and just hit x,f if you find that quicker.

ie2:
(C-x d) - This is **Ctrl+x** followed by just the key **d**.


The very basic functions that you'll use the most are:
Saving the file - Hold **Ctrl** and press **x** followed by **s**
Closing the file - Hold **Ctrl** and press **x** followed by **c**
Cancel the shortcut you half entered - Hold **Ctrl** and press **g**

And all shortcuts that are specific to the language you are using can be found in the "Insert" menu tab. This can have handy things such as insertting a "for loop" for you into the file.

And that is about all I know, as I said earlier, I only know the drop down basics to get my work done.
Though, you can go on to learn more, there are quite a few good tutorials out there.

Here is one that is looks especially useful
[http://xahlee.org/emacs/emacs.html](http://xahlee.org/emacs/emacs.html)
Unlike others that I've had a quick look through, it doesn't preach that you should never use the mouse. Though it gives you a good set of useful shortcuts for you to get started on your way.

Regards
Iain

---

