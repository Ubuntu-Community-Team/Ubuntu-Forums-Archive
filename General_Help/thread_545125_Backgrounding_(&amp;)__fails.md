---
title: "Backgrounding (&amp;)  fails"
date: 2007-09-07
forum: General Help
---

### Post by Eitri on 2007-09-07
I've just recently installed ubuntu on my HP Pavilion dv6000.
And most things run smoothly, but the backgrounding (&) does not work properly. If I simply write the command: "firefox &". Firefox will open, but in 9/10 times it will close as soon as I close the gnome terminal window. xmms will close in 10/10 and gaim will stay open, but be useless.

I've searched the web, and I've asked some friend who's used Linux for a long time. But we've not been able to come up with anything to solve the problem. Best solution so far has been to create a command named run. But that does not work to good when trying to use more than one command.

The run command: function run { nohup $1 > /dev/null & }

Does anyone know why this is happening and what I can do to fix it?

Thanks for your time.
Eitri

---

### Post by mannheim on 2007-09-07
Someone gave me a good answer to this in another thread. If you close the terminal window by typing "exit" at the command prompt, then the backgrounded jobs will remain running. You can also hit Ctrl-D in the terminal to achieve the same thing.

---

### Post by Eitri on 2007-09-08
yes, it work.

Thanks
Eitri

---

