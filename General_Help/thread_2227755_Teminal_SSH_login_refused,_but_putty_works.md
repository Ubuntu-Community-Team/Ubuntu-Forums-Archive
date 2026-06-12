---
title: "Teminal SSH login refused, but putty works"
date: 2014-06-03
forum: General Help
---

### Post by nilandj-nilandsplace on 2014-06-03
I am using 12.04 with the old desktop. I don't know what could have changed but I suspect it has to do with cPanel Manage root’s SSH Keys. I can no longer use terminal for SSH. I get connection refused port 22. I can use putty OK but I like using terminal because I and paste commands and putty I have to type everything out. I have tried bypassing root keys for SSH by enabling Password Authentication. I have tried deleting knownhosts with no joy. I know at some point on my old server host terminal asked me to accept the host, but not this time. It was working a couple of weeks age before cPanel asked me to load new keys for their ticket system. I have deleted them all. I have un-installed and re-installed open SSH on both the server and client. I hate to leave Password Authentication on as I got hacked this week by Russia via SSH.
What do I need to do to get terminal to work again? Everything I look up has a lot to do with SSH and keys, but nothing on just using terminal for SSH!
Thanks James Niland

---

### Post by TheFu on 2014-06-04
You can copy/paste in putty.
Sorry, don't know anything about cPanel. Don't use it.

ssh key management isn't very hard, once the basics are understood. The client makes keys, pushes the public key to the remote system (ssh-copy-id), ensures any conflicting old keys are removed (on both the client and server sides) and things sorta "just work" from there.

So - have you wiped the ~/.ssh/ directory on the remote system to start over?

If you don't expect and valid ssh logins from Russia (or any other country), why not block them at the firewall?  Also, do you run fail2ban or denyhosts to dynamically prevent these attacks from having unlimited attempts?  [http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) might help.

---

### Post by pat20 on 2014-06-04
can you attach your /etc/ssh/sshd_config contents here, as well as the output from adding -vvv to your ssh command from the client?

---

