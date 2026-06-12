---
title: "[SOLVED] Cream (vim) - Block Cut and Paste"
date: 2008-03-19
forum: General Help
---

### Post by Bruce M. on 2008-03-19
Hi Folks,

I couldn't find a "simple" TextPad equivalent text editor in Linux that does:

Select Block; Cut Block; Paste Block

Like this:

**1. Select Block** - top X to bottom X
```

item                           Xgil   | availability
-------------------------------------------------------------------------------
Potion                         70     | initially available
Antidote                       50     | initially available
Eye Drops                      50     | initially available
Phoenix Down                   250    | initially available
Echo Herbs                     50     | initially available
Gold Needle                    100    | initially available
Alarm Clock                    50     | initially available
Handkerchief                   50     | initially available
Hi-Potion                      210    | initially available
Bacchus' Wine                  120    | initially available
Smelling Salts                 50     | initially available
Remedy                         400    | initially available
Chronos Tear                   50   X | initially available

```

**2. Cut Block** to look like this:
```

item                           | availability
-------------------------------------------------------------------------------
Potion                         | initially available
Antidote                       | initially available
Eye Drops                      | initially available
Phoenix Down                   | initially available
Echo Herbs                     | initially available
Gold Needle                    | initially available
Alarm Clock                    | initially available
Handkerchief                   | initially available
Hi-Potion                      | initially available
Bacchus' Wine                  | initially available
Smelling Salts                 | initially available
Remedy                         | initially available
Chronos Tear                   | initially available

```

**3. Paste Block** like this:
```

gil    item                           | availability
-------------------------------------------------------------------------------
 70    Potion                         | initially available
 50    Antidote                       | initially available
 50    Eye Drops                      | initially available
250    Phoenix Down                   | initially available
 50    Echo Herbs                     | initially available
100    Gold Needle                    | initially available
 50    Alarm Clock                    | initially available
 50    Handkerchief                   | initially available
210    Hi-Potion                      | initially available
120    Bacchus' Wine                  | initially available
 50    Smelling Salts                 | initially available
400    Remedy                         | initially available
 50    Chronos Tear                   | initially available

```

So, I got CREAM (vim or Gvim), I've heard it can do it. But I can't for the life of me figure out how.

Any help out there?
Thanks
Bruce

Of course the next step would be to:

```

gil    item           | availability | gil    item             | availability
----------------------------------------------------------------------------
 70    Potion         | initially    |  50    Handkerchief     | initially
 50    Antidote       | initially    | 210    Hi-Potion        | initially
 50    Eye Drops      | initially    | 120    Bacchus' Wine    | initially
250    Phoenix Down   | initially    |  50    Smelling Salts   | initially
 50    Echo Herbs     | initially    | 400    Remedy           | initially
100    Gold Needle    | initially    |  50    Chronos Tear     | initially
 50    Alarm Clock    | initially    |

```
:guitar: ( Final Fantasy XII if you are wondering )

---

### Post by pointone on 2008-03-19
This sounds like a job for [Awk]("http://www.vectorsite.net/tsawk_1.html"), actually.

---

### Post by Bruce M. on 2008-03-19
> **pointone said:**
> This sounds like a job for [Awk]("http://www.vectorsite.net/tsawk_1.html"), actually.

I couldn't find a **"simple"** TextPad equivalent text editor....

AWK sure doesn't look simple. :(

Now if only I could find that [butterfly]("http://ubuntuforums.org/showpost.php?p=4548377&postcount=5")!

Me = non programmer
Bruce

---

### Post by ashayh on 2008-03-19
[LIST=1]
[*]In VIM, press Ctrl+V to go in Visual Block mode
[*]Select the required columns with your arrow keys and press x to cut them in the buffer.
[*]Move cursor to row 1 column 1 and press P (thats capital P) in command mode.
[*]The rest is also possible, including inserting empty columns. Research Visual block mode and figure out the rest.
[/LIST]

Kate in KDE also has a block mode. 
Press Ctrl+Shift+b to get in and out of it.

---

### Post by Bruce M. on 2008-03-20
> **ashayh said:**
> [LIST=1]
[*]In VIM, press Ctrl+V to go in Visual Block mode
[*]Select the required columns with your arrow keys and press x to cut them in the buffer.
[*]Move cursor to row 1 column 1 and press P (thats capital P) in command mode.
[*]The rest is also possible, including inserting empty columns. Research Visual block mode and figure out the rest.
[/LIST]

Thank you for this. I'll have to print that little list out as I'll never remember them  :)

It's not in Cream, but it works and a heck of a lot faster than what I had to do to show the examples in the first post:

```
MIGELO'S SUNDRIES
---------------------------------------------------------------
gil    item           | availability
---------------------------------------------------------------
70     Potion         | initially available                  50     Handkerchief   | after escaping from Leviathan   
50     Antidote       | initially available                  210    Hi-Potion      | after escaping from Leviathan   
50     Eye Drops      | initially available                  120    Bacchus' Wine  | after defeating Belias          
250    Phoenix Down   | after obtaining Crescent Stone       50     Smelling Salts | after defeating Belias           
50     Echo Herbs     | after escaping from Barheim Passage  400    Remedy         | after defeating Judge Master B. 
100    Gold Needle    | after escaping from Barheim Passage  50     Chronos Tear   | after defeating Judge Master B.  
50     Alarm Clock    | after escaping from Leviathan
```

> **ashayh said:**
> Kate in KDE also has a block mode. 
Press Ctrl+Shift+b to get in and out of it.

Not sure is I want to install KDE apps in Xfce ... but I guess I'll "test" it  :)
Thanks
Bruce

---

### Post by Bruce M. on 2008-03-20
> **ashayh said:**
> Kate in KDE also has a block mode. 
Press Ctrl+Shift+b to get in and out of it.

If I could I would thank you twice for this!

> **Bruce M. said:**
> Not sure is I want to install KDE apps in Xfce ... but I guess I'll "test" it  :)
Thanks
Bruce

This does "exactly" what TextPad did in Windows and something I have been searching for since July 07 when I came to Ubuntu.

> Edit > Block Selection Mode - use the mouse!

or: (as you said) [Ctrl]+[Shift]+[B] - use the mouse!

[CENTER][SIZE="4"]**Thank You ashayh !**[/SIZE][/CENTER]

Bruce

---

