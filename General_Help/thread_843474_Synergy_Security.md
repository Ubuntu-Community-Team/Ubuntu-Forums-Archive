---
title: "Synergy Security"
date: 2008-06-28
forum: General Help
---

### Post by Arrowx7 on 2008-06-28
Hello,
Recently I have been using a program called Synergy, it's the one that allows you to share a keyboard and mouse between the two machines over a network.

I was wondering how secure it is.  I am sending keystrokes over the network.  These keystrokes could be passwords.  Could someone technically "catch" the keystrokes?

Thanks

---

### Post by tamoneya on 2008-06-28
someone very much could catch those password.  There are two solutions.

1.  Have a small keyboard for your other computer and use it just for passwords.
2. use a ssh tunnel and make the synergy connection through that.  SSH will do the encryption for you.

Personally I just use the first method because I am lazy and I had a spare keyboard lying around.  However it isnt perfect because I can sometimes forget that I need to type passwords in on the other keyboard.

---

### Post by Arrowx7 on 2008-06-28
I can't open an ssh tunnel when the server is a windows machine can I?

My setup is like this
1stMachine (Windows) (sever) --> 2nd Machine (ubuntu) client --> 3rd machine external server
My 2nd machine is actually a laptop, so I can just type in the passwords.  But is it still pretty secure if I ssh to a 3rd machine, type in the password on the laptop keyboard, and use the keyboard and mouse of the my windows machine to use the shell right?

---

### Post by tamoneya on 2008-06-28
> **Arrowx7 said:**
> I can't open an ssh tunnel when the server is a windows machine can I?

My setup is like this
1stMachine (Windows) (sever) --> 2nd Machine (ubuntu) client --> 3rd machine external server
My 2nd machine is actually a laptop, so I can just type in the passwords.  But is it still pretty secure if I ssh to a 3rd machine, type in the password on the laptop keyboard, and use the keyboard and mouse of the my windows machine to use the shell right?

[http://sshwindows.sourceforge.net/](http://sshwindows.sourceforge.net/)

You cant type on computer 2 and have it go to computer 3.  2 is just a client and therefore its keyboard and mouse are limited to the confines of its screen.  Just put ssh server and synergy on the windows.  Then on the 2 you ssh to 1 and open the session.  Then on 3 you do the same thing.

---

### Post by Arrowx7 on 2008-06-28
Ok here is another question:
Let's say I use the 1st approach: I use another keyboard to type in the password.

When machine 2 is sshed into a server (machine 3).  Can an attacker, in theory, send keystrokes from their machine to the ssh client (machine 2), thereby tricking machine 2 into thinking that machine 1 is sending keystrokes, and send bad commands to the ssh server (machine 3)?

lol, sorry I'm just want to make sure I understand the security risks.

Thanks a lot for your help.

---

### Post by tamoneya on 2008-06-29
ssh is very secure and a hacker would not be able to exploit a computer like that if you are making the ssh tunnels.

---

### Post by airbornespent on 2009-04-24
The simplest option is to confirm the network is switched and even better, both computers are on the same switch. The plain text TCP packets will never leave that switch as they will be routed in one port and out the other.

---

