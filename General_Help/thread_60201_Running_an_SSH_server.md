---
title: "Running an SSH server"
date: 2005-08-26
forum: General Help
---

### Post by endtime on 2005-08-26
(This is sort of a follow-up of [this thread](http://ubuntuforums.org/showthread.php?t=59965))

1.  I want to be able to connect to this PC (in my room in NJ) from college, via SSH.  If I do $ssh localhost I connect just fine, but if I do $ssh 192.168.49.(me) or $ssh (my ip) it doesn't connect.
2.  I want to change the listen port from 22 to something else.
3.  I want ssh listening to start on boot - not sure if I have to do anything to make that happen.

How do I do these things?  I'm not very experienced with this stuff as I'm sure you can tell from my questions.  Thanks in advance.

---

### Post by jasmuz on 2005-08-26
Check out these threads, they might be useful:

This is the ubuntu wiki information [https://wiki.ubuntu.com/SSHHowto](https://wiki.ubuntu.com/SSHHowto)

This is a HOWTO SSH [http://www.ubuntuforums.org/showthread.php?t=27305](http://www.ubuntuforums.org/showthread.php?t=27305)

This is a HOWTO jazz up your SSH login [http://www.ubuntuforums.org/showthread.php?t=40688](http://www.ubuntuforums.org/showthread.php?t=40688)

This HOWTO is how to secure your SSH with public keys [http://www.ubuntuforums.org/showthread.php?t=30709](http://www.ubuntuforums.org/showthread.php?t=30709)

Hope they clear things out for you

---

### Post by endtime on 2005-08-26
[QUOTE=jasmuz]Check out these threads, they might be useful:

This is the ubuntu wiki information [https://wiki.ubuntu.com/SSHHowto](https://wiki.ubuntu.com/SSHHowto)

This is a HOWTO SSH [http://www.ubuntuforums.org/showthread.php?t=27305](http://www.ubuntuforums.org/showthread.php?t=27305)

This is a HOWTO jazz up your SSH login [http://www.ubuntuforums.org/showthread.php?t=40688](http://www.ubuntuforums.org/showthread.php?t=40688)

This HOWTO is how to secure your SSH with public keys [http://www.ubuntuforums.org/showthread.php?t=30709](http://www.ubuntuforums.org/showthread.php?t=30709)

Hope they clear things out for you[/QUOTE]
 Gracias x10...I feel bad, now that you lay that all out for me I'm sure I could have easily found it myself.  And you didn't even point that out.  Well, thanks.

---

### Post by endtime on 2005-08-26
[QUOTE=endtime]Gracias x10...I feel bad, now that you lay that all out for me I'm sure I could have easily found it myself.  And you didn't even point that out.  Well, thanks.[/QUOTE]
 OK...I'm still having trouble.  I do $ ssh (my username)@(my ip) -p (my port) and it still doesn't do anything...just hangs.  I guess it might time out if I left it long enough.  I edited my config file  to change the port and disable root login, but I can't see how that would make a difference.

If I do $ps aux I get:
root      6522  0.0  0.7   3472   980 ?        Ss   22:55   0:00 /usr/sbin/sshd
...but if I do $ top I don't see sshd anywhere.

If I do $ ssh (me)@192.168.49.(x) -p (my port) I get:
ssh: connect to host 192.168.49.7 port 2202: No route to host
...which doesn't happen when I use my remote IP.  If I do $ssh localhost I can log in just fine.  I'm not sure what needs changing...:-/ My port is between 2000 and 3000 - could my ISP be blocking it?  Even if that's the case, something's still not right because my local IP doesn't work completely either.

---

### Post by spin2cool on 2005-08-28
Is your computer sitting behind a router?  That 192.168.xx.xx IP address is usually only the internal IP address.  go into your router settings, determine your external IP address, and try again.  Also make sure that your router is forwarding port 22 to your computer's internal IP address.

Lastly, most DSL and cable plans have dynamic IP addresses, which means your external IP may change.  Look into a dynamic dns updater - no-ip.com is one, dyndns is another.

---

