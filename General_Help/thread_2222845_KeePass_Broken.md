---
title: "KeePass Broken"
date: 2014-05-08
forum: General Help
---

### Post by PCman13 on 2014-05-08
Hi there!

I am having some serious issues using keepass on my linux box. When I run KeePass 2 via mono, and I try to open my database, the password screen looks like this:
[IMG]http://i.imgur.com/ziSxTL0.png[/IMG]
Furthermore, I cannot enter my password. The password field only picks up a few characters. This renders KeePass completely unusable. 

Steps to reproduce:

1. Download KeePass 2.26 portable
2. unzip
3. mono KeePass.exe
4. open a database file

This is the output in my shell: 
```

SendMessage (50331686, 0x101f, (nil), (nil))
SendMessage (0, 0x1203, (nil), 0x7fff90ee8060)
SendMessage (0, 0x1204, (nil), 0x7fff90ee8060)
SendMessage (0, 0x1203, 0x1, 0x7fff90ee8060)
SendMessage (0, 0x1204, 0x1, 0x7fff90ee8060)
SendMessage (0, 0x1203, 0x2, 0x7fff90ee8060)
SendMessage (0, 0x1204, 0x2, 0x7fff90ee8060)
SendMessage (0, 0x1203, 0x3, 0x7fff90ee8060)
SendMessage (0, 0x1204, 0x3, 0x7fff90ee8060)
SendMessage (0, 0x1203, 0x4, 0x7fff90ee8060)
SendMessage (0, 0x1204, 0x4, 0x7fff90ee8060)
SendMessage (50331686, 0x101f, (nil), (nil))
SendMessage (0, 0x1203, (nil), 0x7fff90ee90c0)
SendMessage (0, 0x1204, (nil), 0x7fff90ee90c0)
SendMessage (0, 0x1203, 0x1, 0x7fff90ee90c0)
SendMessage (0, 0x1204, 0x1, 0x7fff90ee90c0)
SendMessage (0, 0x1203, 0x2, 0x7fff90ee90c0)
SendMessage (0, 0x1204, 0x2, 0x7fff90ee90c0)
SendMessage (0, 0x1203, 0x3, 0x7fff90ee90c0)
SendMessage (0, 0x1204, 0x3, 0x7fff90ee90c0)
SendMessage (0, 0x1203, 0x4, 0x7fff90ee90c0)
SendMessage (0, 0x1204, 0x4, 0x7fff90ee90c0)



```

Other dialogue windows like the settings window have the same issue. I have tested this in ubuntu and fedora. Neither work. The keepass2 package from the repositories has exactly the same issues. I am aware of the KeePassX project, but that application does not provide all the functionality of keepass2.

---

### Post by TheFu on 2014-05-08
Never used Keepass v2 for a few reasons.  
Been on KeePassx since the beginning. It is compatible with v1.x DBs, so extremely cross-platform - and zero MONO dependencies. Might be an option for you?
I've never used the normal keepass and never missed anything. Please enlighten me on what I'm missing.

---

### Post by PCman13 on 2014-05-09
I'd like to use KeePass2 for the neat firefox integration with KeeFox. It basically replaces the firefox password manager with KeePass.

---

### Post by dragonfly41 on 2014-05-09
If you want Firefox integration try [www.LastPass.com](www.LastPass.com).

You can import your KeePass data into LastPass.

---

### Post by TheFu on 2014-05-09
> **PCman13 said:**
> I'd like to use KeePass2 for the neat firefox integration with KeeFox. It basically replaces the firefox password manager with KeePass.

Good enough - so you are running a Windows program under Linux, but not using WINE. Interesting.  Beyond my depth.  
Found this [link]("http://keepass.info/help/v2/setup.html#mono") with the large number of setup steps, which may help (or not). 

Did this ever work, for you , under Linux?

---

### Post by PCman13 on 2014-05-09
Yes I did follow those instructions. It has never worked, but then I found the pass ncurses password manager. I'm looking into that now, it seems that no one is familiar with this problem.

---

### Post by dragonfly41 on 2014-05-09
Did you miss my post #4?

---

### Post by PCman13 on 2014-05-10
> **dragonfly41 said:**
> Did you miss my post #4?
I missed your post, but I don't consider lastpass an option since it stores all my passwords on their servers, giving me little to no control over my data. The passwords are client-side encrypted, but still I have very little control over my data. I don't like that :)

---

