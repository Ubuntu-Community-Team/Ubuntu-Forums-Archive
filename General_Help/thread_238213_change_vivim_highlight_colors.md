---
title: "change vi/vim highlight colors?"
date: 2006-08-17
forum: General Help
---

### Post by tocleora on 2006-08-17
Hello everyone... I have decided to use vi/vim (whatever you call it) as my html/php editor and some of the colors used for highlighting are a little too dark, I want to say I've changed these in the past but I can't figure out how. :(  Can anyone tell me if there's a way to change what colors it uses for highlighting and how? I'd sure appreciate it! :)

:-({|= I just wanted to include that cause it looks cool. Thanks.

---

### Post by umonkey on 2006-08-17
Yes, you can change the highlighting in vim. I've never done it myself so I can't answer your question specifically, but there is pretty extensive documentation of vim in the help files. You can access it with the *:help* command. [This page]("http://www.vim.org/docs.php") also has links to some good info on Vim including a FAQ and an HTML version of the help files in case you prefer that over Vim's help system.

---

### Post by tocleora on 2006-08-22
In case anyone else is interested in the solution to this in the future, I thought I'd go ahead and post what I did.  Might not be the right solution, but it worked none-the-less. :)

1. I added this line to /etc/vim/vimrc

colorscheme desert

I did this because I read there was a desert color scheme and thought it might be something I could work off of to find the right colors. Also I should mention I turned "syntax on".  Don't remember why now (colors maybe?) but it was important.

2. I backed up and edited /usr/share/vim/vim64/colors/desert.vim.  What I did was I replaced all "Yellow" to "White".  Then I set each of the guifg=Yellow one by one, saving and viewing to see what that particular guifg changed.  I found that only a certain number of colors would work, but I think the #'s (1 through 7?) as well as some words ("White", "Yellow" and others) worked.  You'll get an error if it doesn't and you can change it back.  Time consuming but it works great.  Then I set my terminal window to show my background image, and to open wide, set the color scheme to match my background (as much as 7 colors can) and I use it as my web page editor!

---

### Post by benteveo on 2006-12-02
Been there too.  I "lost" my colors when upgrading to edgy last week. Here's what I learned and the simple solution.

Ubuntu comes with a stripped-down minimal version of vim (package: *vim-tiny*) which doesn't seem to have syntax highlighting (color) by default.

To get the colors back you need to:
```
$ apt-get install vim
```
and make sure you have this line in your *~/.vimrc* file:
```
syntax on
```

HTH

---

### Post by benteveo on 2006-12-02
Sorry for the double follow-up.  I just realized the original question was not about losing colors but having the wrong colors, sorry!

Anyway, the title of the question (having both **'vim'** and **'colors'** in it) may be the one users losing color click-on.  So having the *"getting color back in vim on edgy"* answer in here might prove useful to others in the future.

For the full discussion of why '**vim**' was demoted to '**vim-tiny**' in edgy see this thread:
   [http://ubuntuforums.org/showthread.php?t=247060]("http://ubuntuforums.org/showthread.php?t=247060")

---

