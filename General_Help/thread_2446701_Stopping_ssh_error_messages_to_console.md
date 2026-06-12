---
title: "Stopping ssh error messages to console"
date: 2020-07-05
forum: General Help
---

### Post by jonwil2 on 2020-07-05
I know why I am getting the "channel 3: open failed: connect failed: Connection refused" messages from ssh but I want to stop them coming to the console. I have configured the "LogLevel" parameter in the /etc/ssh/sshd_config file to "QUIET" but it does not help. It is really messing up my terminal. Thank you.

---

### Post by The Cog on 2020-07-05
When I get those messages, I normally just leave the tunneling session in the background somewhere, and open a second non-tunneling session to the destination machine for the command-line work.

If you really don't want to use a second session, you might try "ssh -blah blah 2>/dev/null" to redirect all output to stderr, but I don't know if this would work.

---

### Post by jonwil2 on 2020-07-05
Thank you - actually that is what I have been doing. However, another host I connect to does not exhibit the same behaviour and I can't find the difference in the configuration. Thanks for your help.

---

