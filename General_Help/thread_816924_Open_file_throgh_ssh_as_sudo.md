---
title: "Open file throgh ssh as sudo"
date: 2008-06-03
forum: General Help
---

### Post by thomseddon on 2008-06-03
I connected via ssh to my remote server, but how do i open a file on there as sudo?

how do you even open a file in that folder from the terminal?

sorry i just cant figure out how to access that directory from terminal,
i can connect in the terminal using the entire 
sftp [email]myname@myname.myhost.myex[/email]tension

but how do i edit a file locally on that connection?

---

### Post by Joeb454 on 2008-06-03
Does your remote server have X11 forwarding?

---

### Post by rune0077 on 2008-06-03
> **thomseddon said:**
> I connected via ssh to my remote server, but how do i open a file on there as sudo?

how do you even open a file in that folder from the terminal?

sorry i just cant figure out how to access that directory from terminal,
i can connect in the terminal using the entire 
sftp [email]myname@myname.myhost.myex[/email]tension

but how do i edit a file locally on that connection?

Try:

```
sudo nautilus /path/of/file
```

That should work.

---

### Post by ivze on 2008-06-03
Hmm... If I have understood correctly, ```
vim <filename>
``` or ```
 sudo vim root-only-file
``` will do just what you want. 
Another variant is to connect using
```

ssh -X <serveraddress>

```
and launch some gui editor```
gedit filename
```, or even ```
nautilus
```. You only need to install these apps on the server side.

---

### Post by thomseddon on 2008-06-03
> **Joeb454 said:**
> Does your remote server have X11 forwarding?

I am not sure?

ahh i see it because i need the text editor on the server side!
eugh how would i go about installing that? it isn't my server as such its a joyent one!

---

### Post by thomseddon on 2008-06-03
but i can use vim!! how do i save the changes i have made using vim?

---

### Post by Joeb454 on 2008-06-03
If you're done editing with vim, press Esc and then type ```
:wq
```

You may find using Nano instead of Vim will be easier, especially if you've never used vim before :)

---

### Post by thomseddon on 2008-06-03
> **thomseddon said:**
> but i can use vim!! how do i save the changes i have made using vim?

esc zz i have seen somewhere

---

