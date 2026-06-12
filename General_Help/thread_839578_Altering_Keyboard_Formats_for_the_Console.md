---
title: "Altering Keyboard Formats for the Console"
date: 2008-06-24
forum: General Help
---

### Post by wilson47 on 2008-06-24
Hello All,

I have succeeded in changing my keyboard layout for the console to the standard German layout, but I have run into an issue. I now have support for important German characters, but I no longer have the symbol "|", which is a bit of a handicap.

Q: Is there a way to alter such a keyboard layout, to say, map "|" to an empty third level slot, say Third Level "j"? I found a way to do this in the GUI with xmodmap, but this doesn't help with the console. 

Thanks for your help!!!

---

### Post by wilson47 on 2008-06-24
bump?

---

### Post by wilson47 on 2008-06-24
Can anybody tell me where to locate these files so that I can attempt to edit them?

---

### Post by bodhi.zazen on 2008-06-24
First, please do not bump your own threads. If a question is unanswered it is often more technical or difficult.

We have an unanswered team to help, but they have no way of identifying unanswered threads if they are bumped.

Try :

```
sudo dpkg-reconfigure console-setup
```

---

### Post by wilson47 on 2008-06-24
I apologize for that. 

I used that command to set up the German keyboard format and also to change console font and font size. However, one is limited to the predefined keyboard layouts, from my understanding at least. 

Can one maybe set up a keystroke to change layouts betwee US English and German for the console? That would work just fine for me if there is no simple way to approach the desired result as seen in the previous posts.

Thanks!

---

### Post by wilson47 on 2008-06-24
This is more or less for any with similar questions, and for myself as a reference. 

This site has good information [http://www.faqs.org/docs/Linux-HOWTO/Keyboard-and-Console-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/Keyboard-and-Console-HOWTO.html)

The commands which look like they will do the trick are:

```
loadkeys, setupkeys, etc.
```

From there, one should hopefully have a good start to figure this out. 

If anyone has more experience with these commands, I would really appreciate guidance or any advice.

---

### Post by wilson47 on 2008-06-27
...also useful: [http://www.ibb.net/~anne/keyboard.html](http://www.ibb.net/~anne/keyboard.html)

---

### Post by wilson47 on 2008-07-17
In case anybody else would like to use a German keyboard layout on the console, I suggest using the Macintosh setup. This way you have "|" mapped to Option+7. This layout seems to cover all of the keys I use on a regular basis. 

Also, does anybody know of a console font which has the new versal-eszet character (unicode U+1E9E)???

---

