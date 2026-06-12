---
title: "Freenx question about sessions"
date: 2006-11-18
forum: General Help
---

### Post by btboudreaux on 2006-11-18
I have FreeNX installed on my desktop. I log in as user "tom" at the local machine and it starts a session (Session A). Then from my laptop, I log in to the desktop as user "tom". This starts another session (Session B) on my desktop using the same user "tom". At the local machine I can't see anything Session B is doing, and at the laptop with the FreeNX client I can't see anything Session A is doing. 

Now I have a couple of questions.

Is their anyway to view Session B, from the local desktop after I suspend it?

Is their anyway to maybe merge the two sessions together? If I start downloading something remotely  in Session B, then I come home and log into my desktop... I can't see session B!!

Is their anyway to make it so that a Session B is never created? and FreeNX just logs into Session A??? Much like Remote Desktop does in Windows. 

I'm trying to migrate my desktop to linux, but some things need to be worked out and tested before doing so. 

Anyhow, I know VNC does what I need, but for some reason I can't get it to work with SSH. And besides, FreeNX seems to kick it's *** in everyway. I just need a solution to this sessions problem.

Thanks! Hope someone can shed some light!

---

### Post by btboudreaux on 2006-11-18
Anyone?

---

### Post by btboudreaux on 2006-11-18
How about, how do I switch between sessions if they are both logged in under the same name??

---

### Post by Marsolin on 2006-11-19
I haven't used [FreeNX]("http://linuxappfinder.com/package/freenx") in a while, but what you are describing is the main feature I was missing. The client seemed to indicate an ability to connect to an existing session, but I couldn't ever get it to work and I wonder if FreeNX implements that piece. One possibility you could try is using FreeNX to connect through VNC. The client can supposedly do that, but I'm not sure if the performance is any better than regular VNC.

---

### Post by btboudreaux on 2006-11-19
I tried to connect to VNC though FreeNX and it doesn't seem to work.

---

### Post by Xappe on 2006-11-20
to view the nx-session from your local session, just connect to it using the nxclient (connect to localhost) and use the same client config you use from your laptop...

---

### Post by btboudreaux on 2006-11-21
> **Xappe said:**
> to view the nx-session from your local session, just connect to it using the nxclient (connect to localhost) and use the same client config you use from your laptop...

Thank you kind sir!!! I shall try this as soon as I'm back near my desktop. 

Although I'm still confused about how linux (or ubuntu or gnome) handles sessions logged in on the same user name and why it isnt easier to switch between them or combine them or why FreeNX can't just log into my current session.

---

### Post by Rizla on 2008-03-12
**This post could be related to an Ubuntu bug filed at**: I got hellanzb working yesterday based on the initial setup in this post, come to find out after reading ALL 26 pages.  That its in the repo's now.  For the sake of easy managemnt, I want to remove all the files associated with hellanzb that I installed and configed yesterday.  Whats the best way to do this. [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Has anyone had any updates on this.  I'm in the same situaiton.  I've got FreeNX client at work that i'm using to remote into my home PC, but it opens a new session.  Rather than work in a new session.  I want to connect to my existing session that I had on my home pc (the local session).  Is it possible?

---

