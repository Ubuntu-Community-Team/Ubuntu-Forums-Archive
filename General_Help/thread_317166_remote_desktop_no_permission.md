---
title: "remote desktop no permission"
date: 2006-12-12
forum: General Help
---

### Post by waldorf on 2006-12-12
I want to be able to control box2 from box1 without having to touch box22.

I know about the remote desktop and the terminal server client GUIs but from what I've seen I need to be physically at box2. Can I get around this?

Thanks in advance

---

### Post by technodigifreak on 2006-12-12
> **waldorf said:**
> I want to be able to control box2 from box1 without having to touch box2.

I know about the remote desktop and the terminal server client GUIs but from what I've seen I need to be physically at box2. Can I get around this?

Ok, let's clarify. :D

Is box2 a fresh installation?  Are any other remote access tools installed (like openssh-server)?  Have you already turned on the Remote Desktop(VNC) on box2?  Are both machines on the same logical network or is one remote?

Once we know a little more about the setup, then we can help.  Any other info you have that might be pertinant, would be nice to provide as well.

---

### Post by waldorf on 2006-12-12
box2 is a fresh installation.

samba server is installed and running on box2

remote desktop (VNC) is turned on and I use it to access box1 from box2, but before it connects, box2 wants to know if it is okay and I need to click approval.

currently they are on the same network, but eventually I want to use box1 (a laptop) to access box2 from far away

thanks a lot technodigifreak

---

### Post by technodigifreak on 2006-12-12
Good :D

I'm going to ask a few more questions to clarify.  Not nit-picking, just making sure I'm understanding the problem.

The goal is to access the desktop on Box2 from Box1, right?  It sounded like in your last post that you want to access the other way around.

Also, you said you got a pop-up box asking for approval, was it a password box?  Have you specified a password on the machine you are trying to access? and what happens when you "approve" it?

Also, I made an assumption, are both of these machines running Ubuntu?  Which version?

---

### Post by waldorf on 2006-12-12
Thanks for the clarifying questions.

Oops on the box2/box1 issue. Yes you are right i want to access box2's desktop from box1.

This is what happens.

On box1: Applications>Internet>Terminal Server Client. I specify box2 address and VNC. click connect. get request for password. i provide it.

Then on box2 a window pops up saying 192.168.1.150 wants to connect. deny or accept? If I click accept on box2, then connection completed.

Then I can use box2 desktop from box1

I want to be able to skip the pop up window in box2 and have the connection completed as soon as I provide the password while sitting at box1.

Thanks again for taking the time. :)

---

### Post by technodigifreak on 2006-12-12
Take a look at the attached picture.  In System>Preferences>Remote Desktop.  Make sure that the checkbox in the (pink) highlighted area is **not** checked on the machine you are trying to access the desktop of.

Let me know if that gets it for you.

---

### Post by waldorf on 2006-12-12
yes! it works and honestly I feel a bit foolish for not having figured that out. Thanks for entertaining my questions - greatly appreciated.

Waldorf

---

