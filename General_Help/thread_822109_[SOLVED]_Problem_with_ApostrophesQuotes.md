---
title: "[SOLVED] Problem with Apostrophes/Quotes"
date: 2008-06-07
forum: General Help
---

### Post by OpVines on 2008-06-07
I have a problem that whenever I hit the apostrophe key/quote key I have to hit space before I get either the apostrophe/quotation. If I hit apostrophe without hitting space it adds it on top of the next letter: éá&#263;óúá&#324;&#341; and so on. I have changed my keyboard model setting to the Generic 105-key (Intl) PC and I have the layout as USA. 

The problem is, I have to switch between this layout and another keyboard model (say Hewlett-Packard since my computer is an HP) every single time I restart my computer. No matter what keyboard model/layout it's on, every time I restart the apostrophe/quotes get messed up again so I have to change it again.

Does anyone have any problem like this where your quotes/apostrophes are buggy and changing your keyboard model/layout is only a temporary fix until you restart?

---

### Post by OpVines on 2008-06-08
Bump!

---

### Post by OpVines on 2008-06-08
Please help?

---

### Post by bingoUV on 2008-06-08
1. Did you not choose USA keyboard layout while installing Ubuntu?
2. Maybe you selected a location other than USA while installing, and Ubuntu in its infinite wisdom changed your layout to that location's common layout.
3. Some config file might have been corrupted. Create another user, and login through that. Does the problem persist?

---

### Post by OpVines on 2008-06-08
I have no idea how to create another user...

---

### Post by ricardisimo on 2008-06-08
You are clearly using US-International with dead keys, which is my layout. When you go to System >> Preferences >> Keyboard, what does it say in the Layout tab?

---

### Post by OpVines on 2008-06-08
Richard, I told you, no matter what settings I change it to a reboot always puts the problem back. It's currently at the Generic 105 USA one. But if I reboot right now it'll still say Generic 105 and USA, but it'll still have the quotes/apostrophe problem I had. So my only fix right now is to change the keyboard model between HP and Generic 105 after each reboot.

---

### Post by OpVines on 2008-06-08
Bump.

---

### Post by OpVines on 2008-06-08
Bump.

---

### Post by drs305 on 2008-06-08
The complicated way is to edit the X11 keyboard symbol files, but since you seem to really want an answer ;-)

Try running this and see if it fixes it. All the command is doing is telling the apostrophe key to be an apostrophe key, but you can try it. 

By the way, have you tried another physical keyboard?

```
xmodmap -e "keycode 48 = apostrophe"
```

If nothing else, you've got another bump.

---

### Post by OpVines on 2008-06-08
Sweet! That worked. I never had this problem though until I upgraded to Hardy, so I know it's not the keyboard.

By the way, can you tell me the code to make the quotations key... quotations?xmodmap -e "keycode 48 = apostrophe"

---

### Post by drs305 on 2008-06-08
> **OpVines said:**
> Sweet! That worked. I never had this problem though until I upgraded to Hardy, so I know it's not the keyboard.

By the way, can you tell me the code to make the quotations key... quotations?xmodmap -e "keycode 48 = apostrophe"

Give me a few minutes and I might be able to figure it out. The reason I can't give you an answer right away is that the quotes require two keys (Shft-apostrope) and I haven't learned how to do that with xmodmap yet.

You can put the command I gave you in System, Preferences, Sessions, Startup > Add so that it is always available from the start of the session. 

I am not entirely happy with the solution - it's pretty much a hack. The real thing to do is to edit the symbols file in /etc/X11/kbd/symbols/**your_language** but I haven't learned that one completely yet. You can learn to do it by searching the forums. I found a pretty comprehensive guide earlier today but only got about half way through it before quitting - since at the time it was academic only - I didn't really need to know.

I will try to find out how to get shift-apostrophe to work or maybe someone else will answer. When you finally get this resolved, please mark the thread solved via the Thread Tools link at the top right of the original post.

---

### Post by drs305 on 2008-06-08
After much thrashing and studying the 'man xmodmap' page....

To get the both keys to work, here is the command:

```

xmodmap -e "keycode 48 = apostrophe quotedbl"

```

Now, to put them in the Sessions Startup, run the command like this:
```

xmodmap -e "keycode 48 = apostrophe quotedbl"

```


lisati (below), sorry if this re-edit messed up your post!

---

### Post by lisati on 2008-06-08
(deleted)

---

### Post by sallymc on 2010-07-26
> **drs305 said:**
> After much thrashing and studying the 'man xmodmap' page....

To get the both keys to work, here is the command:

```

xmodmap -e "keycode 48 = apostrophe quotedbl"

```Now, to put them in the Sessions Startup, run the command like this:
```

xmodmap -e "keycode 48 = apostrophe quotedbl"

```
lisati (below), sorry if this re-edit messed up your post!

Oh you are so, so, so clever. I have been battling with this for hours, and at last found your solution DRS 305.  Well done and many thanks.  BTW, isn't there a better way of advertising that there is this easy apostrophe solution?  There are so many articles on it and yours is so obscure to find!

Love you,
Sallymc  ;)

---

### Post by drs305 on 2010-07-26
> **sallymc said:**
> BTW, isn't there a better way of advertising that there is this easy apostrophe solution?  There are so many articles on it and yours is so obscure to find!

Glad the solution worked for you. I added a few key words to the post's tags, but those words should come up in a normal Google search anyway.  

Using the SOLVED tag via "Thread Tools" also helps searching the Ubuntu forums as it should narrow the search considerably. That's a major reason why we continue to encourage its use.

---

### Post by simosx on 2010-07-26
> **sallymc said:**
> Oh you are so, so, so clever. I have been battling with this for hours, and at last found your solution DRS 305.  Well done and many thanks.  BTW, isn't there a better way of advertising that there is this easy apostrophe solution?  There are so many articles on it and yours is so obscure to find!

Love you,
Sallymc  ;)

The proper way to solve this is to use the appropriate keyboard layout.
If you still wish to use US International (that is, with dead keys), find the proper keys that produce 'apostrophe' and 'double quotes'.

The appropriate way is to press AltGr (right-Alt) and the key that is on the right of ;:.
If you press the same key with AltGr + Shift, you get ".

See
  key <AC11> { [ dead_acute, dead_diaeresis, apostrophe,    quotedbl        ] };


Try

---

### Post by sallymc on 2010-07-26
> **drs305 said:**
> Glad the solution worked for you. I added a few key words to the post's tags, but those words should come up in a normal Google search anyway.  

Using the SOLVED tag via "Thread Tools" also helps searching the Ubuntu forums as it should narrow the search considerably. That's a major reason why we continue to encourage its use.

Thanks for that, will look for SOLVED in future.  I am a newbie, but learning fast.  xx

---

