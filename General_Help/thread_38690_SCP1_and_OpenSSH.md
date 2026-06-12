---
title: "SCP1 and OpenSSH"
date: 2005-06-01
forum: General Help
---

### Post by foamland on 2005-06-01
I can log to an ssh2 server in using open-ssh just fine, but can't use the "scp" it comes with to get to the same server for file transfers.  The error message is "FATAL: Executing ssh1 in compatibility mode failed."

Googling for that message, I see that apparently open-ssh uses ssh1 which won't
talk to servers using ssh2.  The solution is supposed to be "go put the openssh'  scp version onto the server."

What the h....?  I don't even have rights.

---

### Post by WhizCas on 2006-01-15
I got the same problem, look:

scp: warning: Executing scp1.
scp: FATAL: Executing ssh1 in compatibility mode failed (Check that scp1 is in your PATH).

Really strange, dont have any clue to the solution.

---

### Post by krizz on 2006-10-03
Same here ](*,) 

I didn't find a solution that fits me, but a description of the problem.
[SSH Frequently Asked Questions]("http://www.snailbook.com/faq/scp-ossh-to-ssh2.auto.html")
> The solution is to install either the OpenSSH or SSH1 version of scp on the server under the name "scp1," somewhere in the sshd2's PATH. 

As this FAQ, says is an issue on the server side. Obviously, I don't have root access on my Universities sever :) 

Work around: **sftp**

---

