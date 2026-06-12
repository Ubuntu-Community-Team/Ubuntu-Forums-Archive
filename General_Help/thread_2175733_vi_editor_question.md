---
title: "vi editor question"
date: 2013-09-20
forum: General Help
---

### Post by feardotcom on 2013-09-20
So i'm taking this linux class in college and we went over VI. I actually like the vi editior but i got a few questions. This may not be an issue but rather the way vi works, i'm not sure. first whenever i enter insert mode (i) and start typing and hit the backspace it doesn't delete anything, and then i start typing and it starts to overwrite the text. If i need to go up a line and i hit the up arrow it put a C on my file on a new line above the current line. Same thing for the other arrow keys. If i need to delete a single character the backspace doesn't work. Is this normal? or is something wrong with my keyboard config? It doesn't do this while at school when using Putty from Winblows.

---

### Post by Impavidus on 2013-09-20
No, this is not normal.> start typing and hit the backspace it doesn't delete anything, and then i start typing and it starts to overwrite the textThis sounds like replace mode, but you enter that by pressing R or by pressing <insert> when already in insert mode. There may be something wrong with your terminal settings. Also check whether you have a .vimrc. If you have, there could be something in it that causes this behaviour.

/usr/bin/vi should be a (indirect) symlink to vim.basic. You might be using vim.tiny, but I don't think that would cause those symptoms.

---

### Post by feardotcom on 2013-09-20
ok, so i have vimrc it is in "/etc/vim" and the link vi from "/usr/bin/vi" goes to "/etc/alternatives/vi" which then links back to "/usr/bin/vim.tiny" for whatever reason. 

Also, i tried pressing R from command mode it did nothing.

 All <insert> does is capitalize the letter before the current highlighted letter.

As far as terminal settings, what would i look for and where?

---

### Post by 1clue on 2013-09-20
You have some sort of terminal or keymap problem.

What keyboard layout are you using?  And are you using some sort of fancy keyboard, or a foreign one?

What terminal app are you using?

What settings have you played with since you installed Linux?  Anything relating to the terminal, language, input methods, localization, whatever.

Regarding vi/vim:
Vi is a standard, non-free UNIX editor.  If you're using a commercial UNIX then it's probably installed.
Vim is a free/Open Source UN*X editor.  It has a LOT more features than vi, and it can be put on every commercial UNIX I've used since discovering Vim, as well as every Open Source OS, and Mac and Windows.  The difference is huge.

If you intend to finish your class and forget about it, then go ahead using the vi you're using, which is crippled so that it acts just like the original vi.  If you intend to use Linux regularly, especially if you intend to work with servers a lot, then I recommend you install and use the full Vim, or the full version of Emacs if you decide you like that better.

---

### Post by feardotcom on 2013-09-20
I'm a full time linux user right now actually. I'm getting my degree in networking with a specialization of linux. My intentions are to get a job working with linux in some form or fashion and see where it takes me. I have nano installed but i find VI is much more powerful. Not something i intend to finish and forget. The Vim i just installed does it come standard with every major linux distro (like CentOS, RH, SuSe) ?) If so, how come it doesn't with Ubuntu?

---

### Post by 1clue on 2013-09-20
Vim is not automatically *installed* on everything.  However it's easily available on everything, meaning it's in the repository and fully supported.  On Ubuntu it's *sudo apt-get install vim.*

Vim and Emacs are the two main command-line editors.  They are both programming editors and they are both powerful enough to give a modern GUI programming editor a run for its money.  They are not IDEs, but they can both do some amazing things.  Between these two editors, I'm betting most of Linux was developed in those editors.

I'm a Vim guy, but there are also Emacs guys.  Both editors have tremendous loyalty by their users, don't get sucked into a Vim-vs-Emacs fight, I'm only mentioning it because Emacs guys will inevitably read this.  They're both much more powerful than you'd imagine a command-line editor to be, and easily able to keep up with GUI editors.

Google the difference between vi and vim and you'll have to read awhile.

If you are running your own servers, you can install the full version of either of these editors and not take up much space.  Nobody will think twice about your installing them.

If you're used to vim and you have to use vi, then you'll feel like a big man in a tiny car, but as cramped as you get you can do the job.

---

### Post by feardotcom on 2013-09-20
It's funny my class never mentioned emacs as a command line editor. The book teaches emacs gui instead. Wasn't even aware it was command line. Think i'll stick with vim though, i'm beginning to like it alot. Thank you for your help.

---

