---
title: "Connect From one Comp. to Another without..."
date: 2008-02-12
forum: General Help
---

### Post by TimUkaj on 2008-02-12
*Note: Could a moderator be kind enough to delete my recent post from the security section.*

Hey guys, this is my first post here, so be easy on me =)!

I have two laptops. On one of them I've installed Vista (we'll call this **comp. a**), and the other one which I'm currently on is my Ubuntu laptop (**comp. b**).

Both computers are connected to the same LAN (obviously).**Is it possible for me to connect from comp. a to comp. b without having to install anything on the host machine (comp. b)**?

I hope I've been clear enough.

Cheers!

---

### Post by TimUkaj on 2008-02-12
Bump... Someone.... Please?

---

### Post by Therion on 2008-02-12
[Crossover Cable]("http://en.wikipedia.org/wiki/Ethernet_crossover_cable") maybe??  Not sure what exactly it is you're trying to do...

---

### Post by ikonia on 2008-02-12
How do you want to connect ?

Do you want to map network drivers, 
User FTP ?


do you want comp a to comp b only, or comp b to comp a back.

try to be specific in your situation and your end results and you'll get a good response.

---

### Post by KCPokes on 2008-02-12
It is a bit vague.  From just a high-level, you could set up Samba on your Ubuntu box and connect from Vista.  I suppose that is what you are trying to accomplish? Otherwise SSH would give you terminal access, but you'd still need a client on Vista.

---

### Post by TimUkaj on 2008-02-12
Edit: I'm sorry I wasn't clear enough.

I wanna know if it's possible to connect to my other computer (Vista) without having to install any software on the host machine, i.e a telnet server. 

For example, I could install a SSH server on the host machine and then SSH from comp. a to comp. b. While this is possible, it's not the solution I'm looking for simply because I'd need to install a SSH server on the host machine. If I could just install a client on comp. a and then directly connect to comp. b. 

I've tried the Terminal Server Clien (RDP), but it didn't go well.

I hope you understand?

---

### Post by PeterJS on 2008-02-12
Ubuntu prides it self on having no listening ports in the base install, so that means that unless you install something on the ubuntu box above and beyond the base install there's nothing listening for connections from the vista box.

---

### Post by TimUkaj on 2008-02-12
> **PeterJS said:**
> Ubuntu prides it self on having no listening ports in the base install, so that means that unless you install something on the ubuntu box above and beyond the base install there's nothing listening for connections from the vista box.

It's the other way around. **Ubuntu (comp. a) to Vista (comp. b)**. 

I'm sory, I'm really lousy at explaining :(

---

### Post by PeterJS on 2008-02-12
Sounds like smb is the way to go then, I just can't remember if it's installed in the base. Might as well give it a try, see if there's anything in Places > Network > Windows Network.

---

### Post by apetresc on 2008-02-12
You could try looking for security vulnerabilities in Vista, I guess, since that's the only way to access a remote computer without them explicitly listening for it.

From what I've heard, though, Vista comes installed with plenty of vulnerabilities, so you're in luck ;)

---

### Post by PeterJS on 2008-02-12
I just realized I may have answered the wrong question, smb is for file transfers. If you're looking for remote control ubuntu does have an rdp client installed, take a look at Applications > Internet > Terminal Server Client.

---

### Post by TimUkaj on 2008-02-12
> **PeterJS said:**
> Sounds like smb is the way to go then, I just can't remember if it's installed in the base. Might as well give it a try, see if there's anything in Places > Network > Windows Network.

Thank's a lot! While it's not exactly the answer I was looking for, it's still enough to help me put some pieces together. I appreciate that you took your time to help me.

@ AdrianP

Great! That helps me out alot.

Thank's again guys!

---

### Post by TimUkaj on 2008-02-12
> **PeterJS said:**
> I just realized I may have answered the wrong question, smb is for file transfers. If you're looking for remote control ubuntu does have an rdp client installed, take a look at Applications > Internet > Terminal Server Client.

I actually tried this. I kept getting an error. I guess it's not possible without installing some kind of server on Vista.

---

