---
title: "can't see all tasks in top"
date: 2008-07-08
forum: General Help
---

### Post by Drate on 2008-07-08
I can't see all the tasks in top.  There are of course too many to fit on the screen.  My question is how do I navigate up and down the columns.  I know I can have the order in reverse and switch column sorting, but is there not a way to simply view the next line down (other than expanding your terminal window and getting more lines)?

---

### Post by bmac on 2008-07-08
You could use the the "Windows Selector" applet instead of the "Window List" applet.


Hope this helps....

---

### Post by msrinath80 on 2008-07-08
I think he is talking about the 'top' command and not the iconized windows on the top panel. I'm equally interested in finding how folks navigate pages in 'top'. I know that one can use the < and > keys to move processes around, but I'm not sure it does what I want.

---

### Post by jerome1232 on 2008-07-08
while running top
shift+G and a number between 1-4 will scroll not sure if it gets all the way to the end tho.

edit/ shift+G (capital) will prompt you for a number 1-4, then type in the number /edit

---

### Post by Taxman415a on 2008-07-08
You might be able to see more than what shift-G gives you, (check man top, always your best first start), but I wouldn't be surprised if you couldn't, since top is designed to be a summary and not really an exhaustive listing. For the full listing

ps -ef |less

is what you really want, and ps is referenced in the top manpage.

---

### Post by msrinath80 on 2008-07-09
> **jerome1232 said:**
> while running top
shift+G and a number between 1-4 will scroll not sure if it gets all the way to the end tho.

edit/ shift+G (capital) will prompt you for a number 1-4, then type in the number /edit

Thanks for the tip. But I think I'll stick to 'ps aux | less' for now :-)

---

### Post by Titan8990 on 2008-07-09
ps aux | less is the way to go.

The purpose of "top" is not see all your running processes. It is to see what is at the top using the most resources.

---

### Post by msrinath80 on 2008-07-09
> **Titan8990 said:**
> ps aux | less is the way to go.

The purpose of "top" is not see all your running processes. It is to see what is at the top using the most resources.

Interesting. Is that why it was called 'top'? I assumed that 'top' was an acronym for "Table Of Processes".

---

### Post by Titan8990 on 2008-07-09
That is a good guess but is not the case however. Here is an excerpt from top's wiki article:

> In most Unix-like operating systems, the top command produces a frequently-updated list of processes. The processes are ordered by amount CPU usage, with only the "top" CPU consumers shown.

---

