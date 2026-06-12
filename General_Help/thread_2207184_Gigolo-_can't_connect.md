---
title: "Gigolo- can't connect"
date: 2014-02-22
forum: General Help
---

### Post by PDA1 on 2014-02-22
From #! (Crunchbang) Gigolo will allow me to connect to several other Ubuntu computers in my house with no trouble at all. 


But, I can't connect from the other Ubuntu machines to my Crunchbang computer.


Any ideas?

---

### Post by Morbius1 on 2014-02-22
Not a lot of information there - I don't even know what version of Ubuntu you are using. But mostly I honestly have no idea what this means:
>  But, I can't connect from the other Ubuntu machines to my Crunchbang computer.
You can't "see" the #! samba server? ( And I'm guessing you are using Samba here ).
You can see it but it denies you access?

You might want to see if you can do what Gigolo does manually:

First the Microsoft way:
```
nautilus smb://server-name
```
Then the Linux way:
```
nautilus smb://server-name.local
```

[COLOR=#0000cd]*Change server-name to whatever name you've given to the #! machine.*[/COLOR]

---

### Post by PDA1 on 2014-02-22
> **Morbius1 said:**
> Not a lot of information there - I don't even know what version of Ubuntu you are using. But mostly I honestly have no idea what this means:

You can't "see" the #! samba server? ( And I'm guessing you are using Samba here ).
You can see it but it denies you access?

You might want to see if you can do what Gigolo does manually:

First the Microsoft way:
```
nautilus smb://server-name
```
Then the Linux way:
```
nautilus smb://server-name.local
```

[COLOR=#0000cd]*Change server-name to whatever name you've given to the #! machine.*[/COLOR]

I give up- I've wasted too much time on this.

It's got to be easier than this. Maybe it has something to do with a firewall?

---

