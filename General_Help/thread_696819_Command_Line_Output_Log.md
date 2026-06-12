---
title: "Command Line Output Log"
date: 2008-02-14
forum: General Help
---

### Post by niethslim on 2008-02-14
Is there a log file somewhere that save all the outputs I received from the terminal? What about outputs of specific command? 
More specifically: I want to know what the output of "ping www.google.com" was when I executed it some time ago.

Thanks,

---

### Post by jan quark on 2008-02-14
well you can save the output of a command with this command

```
command > ~/Desktop/output.txt
```

---

### Post by niethslim on 2008-02-14
I know that.
What I am asking  is if there's any file it saves automatically to.

---

### Post by pointone on 2008-02-14
Not by default.

---

### Post by niethslim on 2008-02-14
Bummer.
I guess there isn't any file that has my network stats from, say, a week ago?

---

### Post by p_quarles on 2008-02-14
> **niethslim said:**
> Bummer.
I guess there isn't any file that has my network stats from, say, a week ago?
This is *nix: there's a logging application for nearly everything. Try ntop. 

No, it won't give you a log from a week ago, but it will give you today's log in a week.

---

### Post by Pelham123 on 2008-02-14
Hmm, is this the sort of thing you're looking for?

[http://www.sun.com/bigadmin/content/submitted/handle_terminal_output.jsp](http://www.sun.com/bigadmin/content/submitted/handle_terminal_output.jsp)

Take a look at 'man script'

---

### Post by niethslim on 2008-02-14
Well, thank you all for your replies.
I guess there isn't really anything like I'm looking for.

---

