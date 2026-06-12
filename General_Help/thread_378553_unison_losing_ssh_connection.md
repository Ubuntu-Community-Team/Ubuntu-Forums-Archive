---
title: "unison losing ssh connection"
date: 2007-03-07
forum: General Help
---

### Post by TomFumb on 2007-03-07
Hi, thanks for taking an interest

I just set up an ssh server on my xp laptop so that I can synchronise files with ubuntu using unison. 
I can connect to xp via ssh and sftp without any problems, but if I try to use unison through the ssh connection I get 'fatal error, lost connection with the server'. 

User name and password are fine, as far as xp is concerned I don't see how it's any different to me sshing in from command line. 

Can anybody explain?

thanks


ps This happens with both command line and gui unison

---

### Post by richjoyce on 2007-04-15
This happens to me too.

My destination ssh is another ubuntu machine.  Both are running feisty.

EDIT: I'm a little red in the face, didn't realize unison needed to be installed on the remote machine.  Once this was done, ran fine.

---

### Post by topgun98 on 2008-04-16
Well, I am having the "Fatal error" "connection lost" problem as well, and I do have Unison installed on both ends.

Locally, I'm running 2.27.57 on Ubuntu Hardy AMD64.  Remotely, I'm running FreeBSD 6.2 i386.

Any troubleshooting ideas are more than welcome.

---

### Post by kevdog on 2008-04-16
I saw a solution to this a ways back.  ssh is timing out.  I cant remember the change that needed to be done however.

---

### Post by MathSWE on 2008-05-19
Here's how I fixed this, in a terminal do:

1. Either remove or rename the file .ssh/known_hosts
2. Run ssh and connect to the remote host ('ssh user@remote_host')
3. When ssh asks if you really want to connect, enter 'yes'
4. Enter 'logout' to terminate the session

You should now have a new .ssh/known_hosts file, and Unison should work again!

Hope that helps!

---

### Post by topgun98 on 2008-05-20
As it turned out, this was due to my hosting company killing off the process after it started consuming more than 15MB.

---

