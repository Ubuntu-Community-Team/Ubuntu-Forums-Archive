---
title: "Cannot Change &quot;Open With&quot; Applications"
date: 2006-11-18
forum: General Help
---

### Post by justintime32 on 2006-11-18
I'm having a bit of trouble here.

I was trying to make a wma file open with Totem instead of MPlayer, but when I tried clicking on the bullet (in Properties > Open With), nothing happened. I logged in as root, same thing. I tried adding an application, but I got a message saying "Could not add application to the applications database".

Could anyone give me a hand here?

---

### Post by jimbob on 2006-11-18
In Nautilus, right click on the wma file, select open with -> other application and select the application you want ( or am I missing something?)
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by justintime32 on 2006-11-18
> **jimbob said:**
> In Nautilus, right click on the wma file, select open with -> other application and select the application you want ( or am I missing something?)

No, I want to change what program will open when I double click on a file. I can do that fine with my Dapper laptop, and my other Edgy desktop, but not this one.

---

### Post by jimbob on 2006-11-18
Please tell us how you did it on your Dapper laptop and your Edgy desktop.

---

### Post by aysiu on 2006-11-18
Paste this command in the terminal. Substitute in your actual username for *username*, of course. ```
sudo chown -R *username:username* /home/*username*
``` Then try changing the **Open With** application.

---

