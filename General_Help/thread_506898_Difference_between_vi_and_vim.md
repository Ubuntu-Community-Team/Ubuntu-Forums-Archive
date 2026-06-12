---
title: "Difference between vi and vim?"
date: 2007-07-22
forum: General Help
---

### Post by altonbr on 2007-07-22
Every time I edit a file with 'vi', it gives me really odd functionality. For instance, whenever I hit 'i' for insert and then try moving around with arrow keys, it prints 'A', 'B', 'C' or 'D'. So I always have to quit and remember to use 'vim' instead. This never happened to me on Dapper, but it is now on Feisty, even after a fresh install. I thought 'vi' was just a symlink to 'vim' anway. What's going on here?

If I could find 'vi' and 'vim' in */bin then I would symlink it myself, but I can't find them.

---

### Post by bodhi.zazen on 2007-07-22
Ubuntu does not ship with a full blown vi

You should ```
apt-get install vim-full
```

---

### Post by altonbr on 2007-07-22
So what's the current difference between 'vi' and 'vim'?

---

### Post by stmiller on 2007-07-22
vim is

'vi improved'

More powerful, etc.

---

### Post by bodhi.zazen on 2007-07-22
> **altonbr said:**
> So what's the current difference between 'vi' and 'vim'?

[http://www.dc.turkuamk.fi/docs/soft/vim/vim_diff.html](http://www.dc.turkuamk.fi/docs/soft/vim/vim_diff.html)

---

### Post by altonbr on 2007-07-22
Thanks a lot for the information; The article will make an interesting read.

But this is what I don't understand:

'vi' links to '/usr/bin/vim.tiny' and,
'vim' links to '/usr/bin/vim.tiny'

So why does 'vi' have different functionality than 'vim' when they're the same script?

vim.tiny is a binary, so I can't view the source to see why. I'll download vim.tiny.tar.gz (if such a file exists) later on, but I don't have time tonight.

---

### Post by stchman on 2007-07-23
vi and vim and antiquated relics from Unix past.  There are WAY better text editors out there.  As a matter of fact I don't know if there is a worse text editor out there.  vi should be forgotten.

vim is vi improved.

---

### Post by altonbr on 2007-07-23
> **stchman said:**
> vi and vim and antiquated relics from Unix past.  There are WAY better text editors out there.  As a matter of fact I don't know if there is a worse text editor out there.  vi should be forgotten.

vim is vi improved.

I understand that; Please read my post above.

---

### Post by bodhi.zazen on 2007-07-23
> **stchman said:**
> vi and vim and antiquated relics from Unix past.  There are WAY better text editors out there.  As a matter of fact I don't know if there is a worse text editor out there.  vi should be forgotten.

vim is vi improved.

LOL, I am sure there are many who would both agree and disagree. How does your post help the OP or add to this thread ?

---

### Post by #Reistlehr- on 2007-07-23
Whatever you do, if you want to make it as a Linux Admin, that is, make sure you know vi. Vim (vi), and nano (pico), are the two most diffused text editors that can be found on 99.9% of all distros out their, in one way or another. I had a guy come in for an interview, i asked him to create a text file, and he said where's the gui. I wanted to shoot myself.

---

### Post by stchman on 2007-07-23
To insert in vi do the following:

(escape)(colon)(i)

ESC : i

This will put you in insert mode.

---

### Post by altonbr on 2007-07-23
Thanks gentlemen,

But I'm more wondering why vi and vim are different programs in Ubuntu (even though they are linked to the same program) as per this post: [http://ubuntuforums.org/showpost.php?p=3064091&postcount=6](http://ubuntuforums.org/showpost.php?p=3064091&postcount=6). They seem to have very different functionality... Such as: why do the arrows produce 'A', 'B', 'C', 'D' in vi but not in vim. They are both linked to vim.tiny.


I am already proficient in vim, but thanks for the advice.

---

### Post by kuja on 2007-07-24
Take a look at "vim --help". Perhaps when ran as vi instead vim acts as if its run with different options. I'm sure it's something like that.

---

