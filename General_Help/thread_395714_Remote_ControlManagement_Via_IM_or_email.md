---
title: "Remote Control/Management Via IM or email?"
date: 2007-03-28
forum: General Help
---

### Post by jamesjtucker on 2007-03-28
Does anybody know of any apps that can either allow me to send a command via email or (preferably) IM, and have it run on the remote host? Heres what i am trying to do; I have hellanzb set up on my feisty box at home, and want to be able to send it an nzb file via IM or email from work and have it queue it up. All it needs to do is drop a file in a given directory. I have tried a number of ideas, such as using thunderbird to run scripts, etc but cant find a good way to handle this.I dont want to open ssh or web ports to the outside, unless i have to, but it might be the only option. 
Anyone have any ideas?

---

### Post by nhandler on 2007-04-05
Well, from what I could find, thunderbird is not able to use a filter to run a script (which is what you would probably be doing). As for im, I believe this is totally possible. I know that in perl and php you are able to make a "bot" that will sign in. I'm not sure exactly which networks allow the bot to send and receive files (I think msn works). From there, you just send it a file and a command (The command will tell it to move the file to the correct directory).

As you can see, unless you try a different email client (I don't have any suggestions), IM will be the way to go. I've only done an aim bot in perl, so for anything else, you are on your own.

Another option that might be easier would be ftp or ssh.

---

### Post by steevc on 2007-04-05
I've been investigating this area whilst looking at ways to remotely administer my web site. I came to the conclusion that some sort of IM bot would be ideal. I'm using Jabber and have found [gozerbot]("http://code.google.com/p/gozerbot/") as a possible candidate, mainly because it uses Python and already has lots of plugins I can look at for ideas.

An IM bot seems like a fairly secure method of remote access as you can set it up to only perform certain actions and restrict who can talk to it. There's even the possibility of using encrypted messages for extra security.

---

### Post by jamesjtucker on 2007-04-05
Cool, gozerbot seems to be a good solution, im dl'ing it now. What i have set up in the mean time is gmailfs, so i can just cp the file there, and the remote host reads it in. 
 Will try to post a followup when i get the bot set up.

---

### Post by frolle on 2007-04-23
Its easy mate:)

Zussaweb, php interface for hellenzb. Now you can load what you want.

---

