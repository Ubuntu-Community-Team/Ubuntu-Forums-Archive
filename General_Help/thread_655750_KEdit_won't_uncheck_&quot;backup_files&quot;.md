---
title: "KEdit won't uncheck &quot;backup files&quot;"
date: 2008-01-01
forum: General Help
---

### Post by Syndacate on 2008-01-01
Pretty much exactly what the title says.

I like to use kedit, kate is a bit too much for a "simple text editor" in my opinion, I go to "configure kedit" and uncheck "back up files" - hit apply, close the preferences, open them back up, and it's checked again.

I hate it trying to leave this lil backup files wherever I edit something.

Any ideas?

---

### Post by p_quarles on 2008-01-01
You can configure your file browser (whether Konqueror, Dolphin, Nautilus, Thunar or whatever) to ignore files ending in "~". 

If that doesn't do it for you, you can also use kwrite, which is the "simple text editor" that's included with the kate package.

---

### Post by Syndacate on 2008-01-01
> **p_quarles said:**
> You can configure your file browser (whether Konqueror, Dolphin, Nautilus, Thunar or whatever) to ignore files ending in "~". 

If that doesn't do it for you, you can also use kwrite, which is the "simple text editor" that's included with the kate package.

Nah, I don't want it to ignore them altogether, I just want whatever I use to edit basic HTML stuff not to leave droppings of its backup files everywhere.

kwrite doesn't seem to exist, it's not on my comptuer (and I have kate), and sudo apt-get install kwrite returns a "package not found" error.

Possibly called something else?

---

### Post by p_quarles on 2008-01-01
> **Syndacate said:**
> Nah, I don't want it to ignore them altogether, I just want whatever I use to edit basic HTML stuff not to leave droppings of its backup files everywhere.

kwrite doesn't seem to exist, it's not on my comptuer (and I have kate), and sudo apt-get install kwrite returns a "package not found" error.

Possibly called something else?
It's not a separate package, so it won't show up in APT.

Try opening a terminal and running:
```
kwrite &
```
Does that work?

---

### Post by Syndacate on 2008-01-02
> **p_quarles said:**
> It's not a separate package, so it won't show up in APT.

Try opening a terminal and running:
```
kwrite &
```
Does that work?

Yeah, that works, any way to get it to work out of terminal?  It's not in the Applications menu and Katapult doesn't recognize it worth of damn.

---

### Post by p_quarles on 2008-01-02
Sure, you can add a launcher to the menu/desktop/panel by putting in that command (kwrite).

---

### Post by Syndacate on 2008-01-02
> **p_quarles said:**
> Sure, you can add a launcher to the menu/desktop/panel by putting in that command (kwrite).

I didn't have to make a custom launcher, it was in the "menus" - just wasn't activated.

Though how do I get it to work with Katapult?

Nevermind, I got it - I had to uncheck "ignore applications without icons" in katapult settings - thanks a bunch man - weird *** deal with KEdit, though, is this a problem with the program universally, or is it only with my computer - can you turn it off?

---

### Post by p_quarles on 2008-01-02
> **Syndacate said:**
> I didn't have to make a custom launcher, it was in the "menus" - just wasn't activated.

Though how do I get it to work with Katapult?

Nevermind, I got it - I had to uncheck "ignore applications without icons" in katapult settings - thanks a bunch man - weird *** deal with KEdit, though, is this a problem with the program universally, or is it only with my computer - can you turn it off?
Kedit is intended to be a limited text editor:
> A simple text editor for KDE.  It can be used with Konqueror for text and configuration file browsing. KEdit also serves well for creating small plain text documents. KEdit's functionality will intentionally remain rather limited to ensure a reasonably fast start.
(taken from [the package description]("http://packages.ubuntu.com/gutsy/editors/kedit"))

---

### Post by Syndacate on 2008-01-02
> **p_quarles said:**
> Kedit is intended to be a limited text editor:

(taken from [the package description]("http://packages.ubuntu.com/gutsy/editors/kedit"))

Well that's what I love about it, KEdit is everything I want in a basic text editor - though every time I go to save something, it leaves those stupid hidden backup files everywhere I edit something - and i don't want that crap, if I want to back something up, I'll back it up with a different name, y'kno?  

Though it wouldn't uncheck the "make backup" box - must be some kind of glitch in the program - so I'll just kwrite now I guess :-\

---

### Post by p_quarles on 2008-01-02
What's the output of this?:
```
cat .kde/share/config/keditrc
```

---

### Post by Syndacate on 2008-01-02
> **p_quarles said:**
> What's the output of this?:
```
cat .kde/share/config/keditrc
```

"No such directory/file exists"

It's not going to do anything if I can't find the file by navigating to it - my Kubuntu is "less" that file.

---

### Post by p_quarles on 2008-01-02
> **Syndacate said:**
> "No such directory/file exists"

It's not going to do anything if I can't find the file by navigating to it - my Kubuntu is "less" that file.
Well, that's weird. Sounds like the problem is the Kedit isn't generating this file, so it's forgetting your settings. Anyway, I got it working on my end the way you want it, so maybe my rc file will work for you. Create the file mentioned in my previous message, and put this in it:
```
[General Options]
BackupCopies=false
```
Let me know how it works.

---

### Post by Syndacate on 2008-01-03
> **p_quarles said:**
> Well, that's weird. Sounds like the problem is the Kedit isn't generating this file, so it's forgetting your settings. Anyway, I got it working on my end the way you want it, so maybe my rc file will work for you. Create the file mentioned in my previous message, and put this in it:
```
[General Options]
BackupCopies=false
```
Let me know how it works.

Can you send me yours?  So I can try it with a "settings" file in place?

I'll try making a blank one though and see how that works.

EDIT:
I did that and it works fine.

This time when I went into it, there WAS a file called **keditrc** - but it was a "special" file.  No program was able to open it up and it showed up different than the rest of the rc files (where the rest of the rc files show a preview of the text inside, this one just showed a blank white document with an orange x in the corner - nothing could open it, via terminal, nor GUI).

So I deleted that "bad" rc file - made a new file under the same name, put that in there, cat displays the option I added, and when I go into settings "make backup copy" is unchecked (**YAY**).

Though still, is there any way you can send me yours so I have complete options?  I mean judging by what I see here it seems as though changing any of my options would have proven pointless as it seems the keditrc file was corrupt or something...

---

### Post by p_quarles on 2008-01-03
> **Syndacate said:**
> Can you send me yours?  So I can try it with a "settings" file in place?

I'll try making a blank one though and see how that works.

EDIT:
I did that and it works fine.

This time when I went into it, there WAS a file called **keditrc** - but it was a "special" file.  No program was able to open it up and it showed up different than the rest of the rc files (where the rest of the rc files show a preview of the text inside, this one just showed a blank white document with an orange x in the corner - nothing could open it, via terminal, nor GUI).

So I deleted that "bad" rc file - made a new file under the same name, put that in there, cat displays the option I added, and when I go into settings "make backup copy" is unchecked (**YAY**).

Though still, is there any way you can send me yours so I have complete options?  I mean judging by what I see here it seems as though changing any of my options would have proven pointless as it seems the keditrc file was corrupt or something...
Already did. The text in the code box above is the entire contents of my keditrc file. Just create the file, place that text in it, and I'm guessing it should start working the way you want it to.

EDIT: Started my reply before you posted your edit. The first two sentences still apply, but it looks like you've already done what I suggested in the third. ;)

---

### Post by Syndacate on 2008-01-03
You mean the only thing in the rc file was the "save backup file" thing?

---

### Post by p_quarles on 2008-01-03
> **Syndacate said:**
> You mean the only thing in the rc file was the "save backup file" thing?
Yep. That makes sense, because that's the only non-default option I set. (I don't use kedit normally -- I was just trying to replicate the problem you described). 

Anyway, I'm guessing that the whole issue may be fixed now that you have a working keditrc file. Try changing another option, and check the file to see if it changes (as it should).

---

### Post by Syndacate on 2008-01-03
Gotcha, that's all I really cared to change, thanks a bunch!!

---

