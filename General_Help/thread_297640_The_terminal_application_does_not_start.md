---
title: "The terminal application does not start"
date: 2006-11-11
forum: General Help
---

### Post by fluidity on 2006-11-11
Hi,

I have just installed Edgy Eft, the latest NVidia drivers from Nvidia and nothing else.

Now, when I select the terminal application in the "Applications/accessories" menu, I see a message in the bottom bar saying that the application is starting... But nothing happens and the message disappears after a few seconds.

How do I get the terminal window back? (it has to be within the graphical interface in order to install google-earth)

Thanks

---

### Post by digby on 2006-11-11
What happens if you press Alt+F2 and type in 'gnome-terminal'?

---

### Post by fluidity on 2006-11-11
Hi digby,

Well, the laucher window closes and... nothing happens :???:

---

### Post by digby on 2006-11-11
It isn't opening and showing up on another workspace is it?  I'd have you scan through the output of ps -ef, but well, we'd need a terminal open for that...:rolleyes:

---

### Post by fluidity on 2006-11-11
I can do this from a second command-line session : there is no terminal in the list of processes. I have tried to reinstall gnome-terminal using synaptic, but nothing changed :-k

---

### Post by digby on 2006-11-11
What about another terminal program like aterm, eterm, or multignome-terminal?

---

### Post by fluidity on 2006-11-11
digby,

I have installed aterm and it works :D 

Thank-you for the suggestion! Something is broken with gnome-terminal, but at least I can go on.

---

### Post by digby on 2006-11-11
Glad to help - if you'd like, you can try to launch gnome-terminal from aterm and see if you get any sort of error

---

### Post by fluidity on 2006-11-11
I have an error indeed :


"The program 'gnome-terminal' received an X Window System error.
...
The error was 'BadValue (integer parameter out of range for operation)'.
(Details: serial 108 error_code 2 request_code 78 minor_code 0)"


humm... sounds like I'll stick with aterm for a while :rolleyes: 

Thanks again for the hint!

---

