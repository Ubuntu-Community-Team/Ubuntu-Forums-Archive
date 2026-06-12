---
title: "Gaim + Google Talk"
date: 2007-02-27
forum: General Help
---

### Post by Ek0nomik on 2007-02-27
I am using Google Talk with Jabber inside Gaim.  I can't seem to get my buddy icon to get displayed to anyone.  I actually have 2 gmail accounts, and logged in on my other one on my other computer to make sure it was on my end.  The buddy icons don't seem to work for jabber/google talk.  Anyone else have that problem?

Thanks!

---

### Post by cronholio on 2007-02-27
Works fine here. Did you set the icon in Gmail or Gaim?

---

### Post by Ek0nomik on 2007-02-27
I went to:

Accounts / [email]myemail@gmail.com[/email]/Gaim (Jabber) / Edit Account

User Options:
   Buddy Icon:  [Image]  Open / Remove

I opened a .jpg, didn't work.  I did a .png and a .gif, still not working.  I saved them all with GIMP.

I can see other peoples icon, but mine isn't getting sent to other users.

Thanks for the help, hopefully you know what I'm doing wrong!

---

### Post by cronholio on 2007-02-28
Try setting the icon in your Gmail account and it should work.

---

### Post by Ek0nomik on 2007-02-28
Isn't that what I did?  I did change it under my Gmail account...

Accounts...


Than it lists AIM/ICQ, MSN, and Jabber (Jabber is my Gmail account)...

I choose Jabber, Modify Account... and under User Options I change my Buddy Icon.

Isn't that what I just did, or am I missing something?

Thanks,

Cheers!

---

### Post by Ek0nomik on 2007-02-28
On the official Google Talk site it says to user Jabber for Gmail... unless I missed something?

---

### Post by CocoAUS on 2007-02-28
You misunderstood what he was saying.

You need to change the icon in your gmail account using gmail.com  Since Google offers its own servers and chat through gmail, the user icon included in your gmail account overrides what you setup in Gaim.

To change your icon, log into your account at [http://gmail.com](http://gmail.com), click "Settings" (upper right corner), then on that page you will see an option called "My Picture."  Upload your icon using this and it will show up in your Gtalk chats using Gtalk, Gaim, Gajim, etc.

---

### Post by Ek0nomik on 2007-02-28
I totally have my buddy icon chosen on Gmail.com, and it still won't appear.  I logged into Google Talk on my Windows Box, and I can't see my icon from this computer.  Unless Gmail.com's buddy icon feature doesn't work, I don't even know how this is possible...

---

### Post by Ek0nomik on 2007-02-28
I think setting your buddy icon at gmail.com only changes the buddy icon for the chat that is web browser based...

Cheers!

---

### Post by cronholio on 2007-02-28
> I think setting your buddy icon at gmail.com only changes the buddy icon for the chat that is web browser based...

I use Gaim while most of my friends use the browser chat and I do see all their buddy icons.

---

### Post by CocoAUS on 2007-02-28
Ek0nomik,

Try right-clicking on their username on your buddy list and choosing Get Info.  For some reason, my buddy icon disappeared off Gaim, but after getting my own info, it reappeared.  Perhaps this will help.

---

### Post by Ek0nomik on 2007-02-28
Firstly, it seems as though Gmail continually deletes my Buddy Icon.  Settings/My Picture, I select one, Save Changes... than I check again a bit later and it just says Select Picture again.

I have 2 Gmail accounts.  One is [email]lovexxxxx@gmail.com[/email], and another [email]justin.xxxxx@gmail.com[/email].  (Not actually xxxx's.)

I use love on my Windows Box, and justin on my Linux box.  I added justin to my Google Talk on Windows, and I added myself (justin) onto my Gaim buddy list.

No buddy icon ever appears.

I appreciate the help and support, hopefully we can pin it down.

---

### Post by CocoAUS on 2007-02-28
That is awfully strange.  I know Gmail has been having some major server problems over the last few days...perhaps that's it?  I, for instance, deleted a message, logged out, then logged back in, and the message was still in the inbox.  I've also been having problems download attachments and such.  Perhaps this is the cause?  It seems that if Gmail.com actually holds onto your picture, then it should work in Gaim.

Have you tried another Jabber client for Linux?  Psi Jabber works and is in the repos.  You could just install it and see if the icons work that way, then uninstall it when you're done checking.  Gaim, as much as I love it, isn't really a "proper" Jabber client.

Note: If you're going to try Psi, you'll probably need to install the qca-tls package as well, which is available in the repos.

---

