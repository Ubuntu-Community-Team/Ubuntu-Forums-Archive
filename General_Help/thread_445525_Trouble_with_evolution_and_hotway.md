---
title: "Trouble with evolution and hotway"
date: 2007-05-16
forum: General Help
---

### Post by great_googley_moogley on 2007-05-16
I successfully setup Evolution to use hotway to check my MSN account.
it worked fine until about a week or so ago.
now when i click send/recieve i get this error:

"Error while performing operation.

Could not connect to 127.0.0.1: Connection refused"

what could have happened?  how can i fix?
any assistance would be appreciated

my /etc/inetd.conf:
pop3		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotwayd
2500 stream tcp nowait nobody /usr/sbin/tcpd /usr/bin/hotsmtpd

thanks!

---

### Post by jia103 on 2007-08-04
The following is what I tried for my problem. Note that I'm only trying to use hotwayd; I'm skipping over the hotsmtpd directions here:

[INDENT][http://www.ubuntugeek.com/send-and-receive-your-hotmail-messages-through-evolution.html](http://www.ubuntugeek.com/send-and-receive-your-hotmail-messages-through-evolution.html)[/INDENT]

To diagnose this problem, I began by running one of the following equivalents in a terminal:

[INDENT]telnet 127.0.0.1 110
telnet localhost 110
telnet 192.168.xxx.yyy 110
telnet hostname 110[/INDENT]

(110 is the pop3 port; 2500 can be used similarly to test hotsmtpd access). I suggest you try similarly to verify that the "Connection refused" error appears this way.

By the way, I also had the following running in a different terminal window:

[INDENT]tail -f /var/log/syslog[/INDENT]

This allowed me to see the errors from hotwayd's point of view as they occurred.

Since I continued getting the "Connection refused" message, I check my /etc/hosts file first. The log showed the IP address as 127.0.0.1 when I tried using my host name. It turned out there was an error in my /etc/hosts file:

[INDENT]127.0.0.1 host.domain localhost hostname
192.168.xxx.yyy hostname[/INDENT]

I removed the "hostname" part from the 127.0.0.1 line because I only wanted it for the 192.168.* line. This helped.

Once I fixed this, I checked my /etc/hosts.allow and /etc/hosts.deny files. (Google "nfs howto" for more information on these files.)

I have my /etc/hosts.deny file set to block everything that is not explicitly allowed. Opening port 110 is new for me, so I needed to add a line to my /etc/hosts.allow file for this:

[INDENT]hotwayd: 192.168.xxx.yyy[/INDENT]

If I was purely using the loopback address, I suppose the following would work:

[INDENT]hotwayd: 127.0.0.1[/INDENT]

Once I did this, the telnet command at the beginning of this post worked well. I was able to hit Ctrl+] to get back to the "telnet>" prompt, then typed "quit" to exit telnet.

I returned to Evolution and retried "Check for Supported Types" under the "Authentication Type" section, and this time it was successful. (I even saw the message in the log window.)

Again, this worked for me. It might not be a solution to your specific problem, but I hope it helps.

Good luck!

---

