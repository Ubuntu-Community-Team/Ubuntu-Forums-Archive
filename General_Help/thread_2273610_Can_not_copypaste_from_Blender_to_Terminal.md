---
title: "Can not copy/paste from Blender to Terminal"
date: 2015-04-14
forum: General Help
---

### Post by No_I_wont on 2015-04-14
I can't copy text from Blender and paste into Terminal.
I can copy from blender, paste in gedit, copy again and then paste in terminal...

Neither ctrl+c or right click-menu copy works.
terminal > Blender works.

Tests:
Copy *TestA* from Blender. Nothing gets pasted in Terminal with Shift+ctrl+v, Paste is greyed out with right click.
Paste in gedit and *TestA* is pasted. Copy this from gedit. Paste in Terminal *TestA* is pasted.
Now copy *TestB* from Blender. Nothing pasted in Terminal but *TestB* in gedit.
Terminal can't read what Blender puts in clipboard.
Why!? How!?

Ubuntu, 14.04, 64-bit, Blender 2.73a, GNOME Terminal 3.6.2
Have tried asking at blenderartists forum but without any answers.

---

### Post by pmi2 on 2015-04-14
Have you tried to a) highlight the text in Blender, and b) mouse center-click in Terminal?
Is that also not working?

---

### Post by No_I_wont on 2015-04-14
Hmm... That DID work!
Very strange that normal copy doesn't. Why do you think this is?

---

### Post by pmi2 on 2015-04-14
I don't know, not sure I understand how the different applications use Paste, and the clipboard, but I have noticed that it is not consistent, which is a shame... cut and paste are such basic productivity tools, you might think they would work the same no matter where you use them.

edit:

I think the center-click version of paste may bypass the default clipboard somehow.  I do know that there are different clipboards.  I have not had a chance to install the ClipIt manager, it is supposed to provide a way to sync the clipboards (if that is what you want), which may fix this problem.  I have not tried it yet myself, its somewhere on my todo list.

see:

[http://askubuntu.com/questions/167570/how-does-middle-click-paste-work](http://askubuntu.com/questions/167570/how-does-middle-click-paste-work)

If you try it, please post the results, I can't play much until after business hours... :D

---

### Post by No_I_wont on 2015-04-15
Thanks. It's definitely a multiple clipboard issue.
I've just installed ClipIt and it works to copy Blender>Terminal now. I've noticed one issue though, also reported in the answer you link to, that I can't copy something then select a part of another text and paste to replace... I'll have to see how annoying this becomes in daily use.

One other issue I noticed before installing clipit was that only the text I left-click-drag-selected in blender got copied when middle-click in terminal... So I couldn't drag-select a small portion (which I usually do just to get the right window in focus) and then hit ctrl+a. Only the first portion got copied... This was what got me installing ClipIt.

---

### Post by pmi2 on 2015-04-15
> **No_I_wont said:**
> ...only the text I left-click-drag-selected in blender got copied when middle-click in terminal... So I couldn't drag-select a small portion (which I usually do just to get the right window in focus) and then hit ctrl+a. Only the first portion got copied... This was what got me installing ClipIt.Yes, dragging and selecting text, double- and tripple-click works, but Ctrl-A does not.  Does not seem consistent.

---

