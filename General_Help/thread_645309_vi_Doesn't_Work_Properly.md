---
title: "vi Doesn't Work Properly"
date: 2007-12-19
forum: General Help
---

### Post by edarroyo on 2007-12-19
So, I run vi in a terminal... it doesn't work properly. I type 'i' to go into insert mode. As soon as I start typing, no text is inserted, instead the terminal starts getting full of lines with a single letter, the letter 'l', from the bottom all the way to the top. One line with a one letter 'l' for each character that I try typing. Any suggestions?

---

### Post by geraldm on 2007-12-19
# Try to find out what program you are using for vi
vi --version
ls -l /usr/bin/vi

# Next try to find out if there are any startup file with execution commands and remove it.  For vim:
ls ~/.vimrc
rm -f ~/.vimrc # remove this if it exists (unlikely if you did not put it there)

# Then try the tutorial OR read the manpage
vimtutorial

Gerald

---

