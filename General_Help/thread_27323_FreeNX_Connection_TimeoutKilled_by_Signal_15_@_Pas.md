---
title: "FreeNX Connection Timeout/Killed by Signal 15 @ Password"
date: 2005-04-15
forum: General Help
---

### Post by GaibryelRemorse on 2005-04-15
Ok... before i took my desktop and laptop to hoary, I was able to use NXClient pretty much without issue.  I updated my desktop machine to Hoary and was able to get NXClient to work once, but then started having "Error 99" every time I tried to connect.  I search the web via google for what "Error 99" was but couldn't get a straight answer.

I decided to update my laptop, as I like Hoary that much better.  (Even runs the laptop better too).

I pulled out all NX Files & Installs, and used synaptic to get FreeNX, NXClient, and NXServer via backports (hoary-extras-staging main).  From what everything is telling me (IE No errors and 'sudo nxserver --status'), all the packages *think* their running fine, or i don't know all the 'check status' commands.

However, the problem that I have now is that I am recieving timeout errors via the 'connection status' dialog box.  Though, if I click upon details, the last line is "NX> 102 Password: Killed by signal 15."

I am able to SSH from client into server directly. I'm also able to SSH from the server into the client.  However, In the situation that both server and client is, I haven't been able to test the server fully outside the network.  Though server is able to NX into itself via localhost.

I've terminal-rm'ed the cache files and removed them via NXClient.  I've gone through the "nxserver --adduser" "nxserver --passwd <user>" "nxserver --list" and finally "nxserver --deluser" ... still haven't been able to make a full connection.

Help? Please? With sugar gum drops on top?

If you need any more information, please include the command and i'll post the response.

---

