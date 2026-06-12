---
title: "Problem with vi in 6.10"
date: 2007-01-10
forum: General Help
---

### Post by linuxonbute on 2007-01-10
HI,
I have just installed Ubuntu 6.10 and am having trouble with vi.

If I create a file and don't need to use the cursor keys 
eg:

Hello
another line
Goodbye

then it is fine.
But as soon as I try to use the cursor keys it goes wrong.

eg if the cursor is on the second line and I press one of the keyboard cursor keys say the UP arrow this is what happens:

Hello
D
another line
Goodbye

So instead of the cursor moving I get a new line with capital D in it.

Any idea what is wrong please.
tia
Norm

---

### Post by Wim Sturkenboom on 2007-01-10
Sorry, don't know what's wrong.

Use h, j, k and l :D

[edit]
obviously in command mode
[/edit]

---

### Post by linuxonbute on 2007-01-10
Sorry, I didn't explain fully.

This is while in Insert Mode so the keys you suggest just produce their normal text.

It's ok in command mode but it means I have to escape to command mode, move to the point I want to insert text at, go to Insert Mode and start typing again.

Never had this before with vi and I have been using it for, oh, about 7 years in other distros.

norm

---

### Post by mbeierl on 2007-01-10
I don't know the logic behind the choice, but 6.10 installs only the core vi.  What you really want is the full vi package:

```
sudo aptitude install vim-full
```

---

### Post by linuxonbute on 2007-01-10
> **mbeierl said:**
> I don't know the logic behind the choice, but 6.10 installs only the core vi.  What you really want is the full vi package:

```
sudo aptitude install vim-full
```

Well, I didn't know that.
However I have solved the problem a different way ( I think :eek:  )
in /usr/bin  vi is a symlink  and so is vim.

I tried deleting vi and making it a symlink to what vim pointed to.
That didn't work.
I tried making it a symlink to /usr/bin/vim.
That didn't work.
So I deleted vi copied vim to oldvim then renamed vim to vi :-? 
That does work.
Thinking back to other distros I think they aliased vi to vim so maybe that's different too.
Thanks anyway,
Norm

---

