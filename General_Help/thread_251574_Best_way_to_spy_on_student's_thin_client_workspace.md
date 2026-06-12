---
title: "Best way to spy on student's thin client workspaces?"
date: 2006-09-05
forum: General Help
---

### Post by tebibyte on 2006-09-05
Hi, I am investigating Edubuntu for my school, and was wondering what security practices can be implimented. We are currently considering using LTSP. One thing that would be nice, is for a teacher or an admin to keep an eye on all the other termanals from thier own termanal. I'm sort of envistioning a teacher being like one of those security officers in front of 20 television camereas. Anyway does anyone know of an application or process  that can make that happen?

Thanks

---

### Post by pwrstick on 2006-09-05
While I don't know of a program that does the "security guard with his feet up drinking coffee staring at a screen with 8 squares of video feed" look, VNC is a program that will allow you to login to a single terminal and see what's going on, and even take control.

It's primarily used as a way for a person to remotely access another terminal and control it, but I believe it has a "view only mode" so you can watch your kids procrastinate on Myspace.com.

I'm sure there's a way to accomplish the "8 squares of video" option, but I don't know off hand.

---

### Post by ewl1217 on 2006-09-05
I really don't know of any options other than VNC. The biggest problem with VNC though, is that you'll be stuck with a separate window open for each display you're watching. There may be a VNC client that had some sort of tabbed or tiled display, but I don't know of one. Another remote access option, similar to VNC, is FreeNX. I don't know much about it, but you could always look in to it.

**EDIT:** I missed the part about LTSP. I don't know anything about that.

---

### Post by zhenya on 2006-09-06
UltraVNC has a tabbed VNC viewer that also has a view only mode.

---

### Post by Tomosaur on 2006-09-06
Is it really necessary? It's fairly easy to set up a logging system, and you can write a few lines of code which will flag an admin when a certain command is attempted. Trying to catch people 'live' is just a really sneaky Big Brother attempt. What happened to trust? Linux is very customisable anyway - the users will not be able to use commands you do not allow them to.

---

