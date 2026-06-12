---
title: "Terminal Server Client hangs up."
date: 2007-01-15
forum: General Help
---

### Post by FeraTech on 2007-01-15
I am using "Terminal Server Client 0.148" with VNC trying to access my Ubuntu Web server. However, after 30 seconds my Terminal Server Client hangs. The picture freezes however my keystrokes are still remotely being displayed. This eventually fails after 2-5min. 

I am running Edgy on an AMD T-30 laptop with an ATI 200M graphics card.

---

### Post by FeraTech on 2007-01-15
I forgot to mention, when I connect to a windows machine TSC works fine but occassionally disconnects. When someone else connects through VNC to my server it works for them without any problems.

---

### Post by boaz60 on 2008-03-05
I'm having a very similar problem.  I'm running WinVNC on a W2k machine and I can connect to it without a hitch with any client except the Ubuntu TSC w/ VNC.

Actually what happens is, I get a connection immediately and I can see the screen but my input doesn't respond graphically.  I've learned that I have to keep reconnecting, usually 3-5 times before I can see my input graphically.  I know the input is transferring even when I can't see it though, because if I try to move the login window with the mouse, I don't see it move, but when I finally get a responsive connection the login window will be moved around.

Anyways, it sounds similar to me, and it's baffling, because it works fine from other platforms/clients.

I think I'm going to try and install a different VNC client on the Ubuntu machine to see if that changes anything.

---

### Post by boaz60 on 2008-03-05
Yeah TightVNC client works great, solved my problem anyway.

```

sudo apt-get install xtightvncviewer

```

---

