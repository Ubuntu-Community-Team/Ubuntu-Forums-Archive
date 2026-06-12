---
title: "Use a &quot;Filesystem-wrapper&quot; to access a ext in a case-insensitive way"
date: 2012-10-15
forum: General Help
---

### Post by dfgdfgdfghfj on 2012-10-15
Hey there,

is there any possibility (like a "filesystem-wrapper") to use ext in an case-insensitive way?

I'd like to try linux/ubuntu, but when I first tried years ago this was one of the biggest "disadvantages" i noticed and return to win 7.

Since I dont like win 8, I think about giving a second chance to linux.

I DON'T want to start a discussion about case-sensitivity beeing a good or a bad thing. I want to type a Filename the way I like (with some letter upper case) but be able to access them quickly using lower case and auto-completion.
If you think case-sensitivity is better - I don't care. In my eyes it produces a) a bad usability or b) ugly filenames.

If linux is so great and configureable and so on, this should not be a very tough "fix", right?

PS: Sure, I can use FAT32 - but that is not realy a solution.

---

### Post by Vaphell on 2012-10-15
case sensitiveness one of the biggest disadvantages? you sure are picky ;-)

if you are talking about using terminal, then look at **shopt -s nocaseglob** and **shopt -s nocasematch** supported by bash.

---

### Post by dfgdfgdfghfj on 2012-10-16
well, I'm not "only" talking about the terminal, but every application :)

---

### Post by shreepads on 2012-10-16
I recommend using Dosbox...

---

### Post by dfgdfgdfghfj on 2012-10-16
afaik DosBox is for Dos-based Software. I doubt usual linux tools can be run there - or am I wrong?!

---

### Post by shreepads on 2012-10-17
> **dfgdfgdfghfj said:**
> afaik DosBox is for Dos-based Software. I doubt usual linux tools can be run there - or am I wrong?!

You're right, it only runs DOS apps, but clearly it gives you the across-all-applications-case-insensitives that you desire that's causing you to "return to Win 7" every time...

BTW how exactly do you enable this across-all-applications-case-insensitives in WIn 7?

---

### Post by Vaphell on 2012-10-17
you don't, it's a 'feature' of win32
ntfs is case-sensitive but the windows itself not so much.
[http://superuser.com/questions/364057/why-is-ntfs-case-sensitive](http://superuser.com/questions/364057/why-is-ntfs-case-sensitive)

---

