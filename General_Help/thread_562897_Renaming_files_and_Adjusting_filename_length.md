---
title: "Renaming files and Adjusting filename length"
date: 2007-09-29
forum: General Help
---

### Post by Jose Catre-Vandis on 2007-09-29
OK, daughter has new mobile phone equipped with mp3 player. this has caused me considerable stress as it is extremely fussy about what type of mp3 it will accept, in particular filename length.  I can deal with bitrates and vbr/cbr etc, but it will only accept filename length of 32 characters.

I have found krename which will help to tidy up the filename, but is doesn't have a trim function, or one I can find. I can see I can add a command line sequence to the renaming, but am not sure what to put.

So if we take a long filename such as:
```

Dire Straits - Where Do You Think You Are Going.mp3  (51 characters)
```

krename will acheive this:

```
DireStraits-WhereDoYouThinkYouAreGoing.mp3  (42 characters)
```

I need to get to this:

```
DireStraits-WhereDoYouThinkY.mp3  (32 characters)
```

keeping the extension (for cross platform use!)

Can anyone help with a command line sequence that will do this?

---

### Post by cwaldbieser on 2007-09-30
krename should allow:
```

$[1-32]

```
character x-y of the old filename.

---

### Post by Jose Catre-Vandis on 2007-09-30
Thanks cwaldbieser, that does adjust filename length. need to set to 28 in order to keep the .mp3 extension, and unfortunately it runs the template before the find and replaces, so my example ends up as
```
 DireStraits-WhereDoYou.mp3  (26 characters)
```
instead of
```
DireStraits-WhereDoYouThinkY.mp3  (32 characters)
```
I suppose I could make two runs at it :)

---

