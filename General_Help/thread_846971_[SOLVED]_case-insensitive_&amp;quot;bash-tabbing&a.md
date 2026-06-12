---
title: "[SOLVED] case-insensitive &amp;quot;bash-tabbing&amp;quot; ?"
date: 2008-07-02
forum: General Help
---

### Post by PGScooter on 2008-07-02
Hi, I really enjoy the feature offered by bash where you start typing a word, and then press <tab> and it completes it or offers a list.

Is there anyway to modify this so that it is case-insensitive, at least for the first letter.

For example, if there is a file in my current working directory called "Ubuntu.txt"
I want to be able to type ubun  and then tab and have it match.

Thanks!

---

### Post by sdennie on 2008-07-02
You can.  Create a file called ~/.inputrc and put the following in it:

```

set completion-ignore-case on 

```

You'll need to close the terminal and start a new one before that takes effect.

---

### Post by PGScooter on 2008-07-02
great, thanks a lot vor!

---

