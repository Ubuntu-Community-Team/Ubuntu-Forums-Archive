---
title: "teamspeak"
date: 2007-03-21
forum: General Help
---

### Post by JELO on 2007-03-21
Hello,
I currently run teamspeak on an ubuntu server.  All that seems to be fine and dandy.  Recently though I can't connect to the server from ubuntu (the actual log in via teamspeak, everything else is fine).  I can log into windows and connect fine.  I ran the uninstall script that came with teamspeak and tried reinstalling.  I still can't connect.  I remember when I first installed the client onto ubuntu I could connect fine.  I'm not sure what's happened to cause this.  It just keeps coming back bad username/password.

---

### Post by hikaricore on 2007-03-21
I'm not too familiar with the server side of TS, but if you havn't upgraded anything, nor setup a firewall of anykind/tweeked your router, it could be very well that the TS server is rejecting your connection because of your version or something similar.

You may want to see first of all if you can ping the server, also be sure when trying to connect to it with the TS client you start the client from a terminal window so you can see any error output.

---

### Post by JELO on 2007-03-21
Server pings fine.  Running client from terminal no errors coming up.  I'm running the latest client and latest server both non beta.  I also tried doing the anonymous thing and still get bad user/pass.

---

### Post by hikaricore on 2007-03-21
If it's not a super secret server or anything, could you pm me the addy, port, and such so I might test it out?  This way we can see if it is possibly a problem with the linux client, I'll update mine now incase it's out dated.

---

### Post by ComputerGuy56 on 2007-03-21
I use TS a lot and I have a lot of things you can do:

1. On the computer that's hosting TS, try connecting to your server Via 127.0.0.1(or is that just Windows?)

2. Go to your tss2_rc2 and find a file bad_names.txt. Make sure it only has server in it.

3. MAKE SURE your doing that cd tss2_rc2 teamspeak2-server_startscript start. I used to do it a different way and I couldn't even shut down my server.

4. Make sure your client can connect to any TS server.

5. (This step is VERY optional) Delete your server.dbs. This stores all your user names, passwords, channels. You will get a new user name and password.

6. Check your server.log(server.txt) and make sure it has no errors, if it has anything, paste it here.

Couple other things but I'll wait till' you reply.

---

### Post by ComputerGuy56 on 2007-03-21
> **hikaricore said:**
> If it's not a super secret server or anything, could you pm me the addy, port, and such so I might test it out?  This way we can see if it is possibly a problem with the linux client, I'll update mine now incase it's out dated.

Possibly me too? I've been working with TS for over 2 years...

---

### Post by hikaricore on 2007-03-21
> **ComputerGuy56 said:**
> Possibly me too? I've been working with TS for over 2 years...

I think I scared them away lol.

---

### Post by ComputerGuy56 on 2007-03-21
> **hikaricore said:**
> I think I scared them away lol.

#-o

---

### Post by JELO on 2007-03-21
Ok from the top.
The computer hosting teamspeak is an older pc running ubuntu.  I manage it via ssh.
step 2 is a pass
step 3 is a pass
step 4 I haven't tried.  I'll post once i log back in to linux.
step 5 is a no go
step 6 no errors

I'll pm you guys login info.
Thanks

---

### Post by JELO on 2007-03-21
Never mind guys I got it working.  I feel so stupid.  Didn't notice that a nickname is required!  I just kept thinking bad pass or user.

---

