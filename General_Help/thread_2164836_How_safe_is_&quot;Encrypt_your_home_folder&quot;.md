---
title: "How safe is &quot;Encrypt your home folder&quot;"
date: 2013-08-02
forum: General Help
---

### Post by CaptainMark on 2013-08-02
When installing Ubuntu (or a derivative of it), if you use the standard option to encrypt the home folder, I believe it uses ecryptfs how safe is that option against someone with physical access to the machine?
On a scale of 1 - 10, 
1 being: An absolute noob could accidentally break in (Now I know its not this one but the scales got to start somewhere right?)
5 being: Someone relatively experienced with Linux but not with penetration testing and armed with Google could break in
10 being: It would take an expert level hacker with professional pen testing equipment and plenty of time to get in
11 being: Uncrackable

Try to avoid speculative answers here or what you've heard from a friend, I'm really looking for replies from people with experience in encryption techniques.
And just to clarify I'm not asking for advice or a guide on how to do it, I'm merely trying to judge how safe this option is for use in various situations for my own computers.

---

### Post by sudodus on 2013-08-02
A. The security level depends very much on the quality of your log in password. With a good one, I think it will be hard to break the system, so I think the score is higher than 5 to decrypt the encrypted files of the home directory. And you should know, that the files that you 'see' when running it, are *not* stored on the HDD.

B. You should make sure that cryptswap is also working and that there is no standard swap partition (or swap file). Otherwise sensitive information might be found in a swap area.

C. But I think the temporary directory /tmp is not encrypted, and I think it is a security hole. If you mount /tmp onto a ramdrive or overwrite /tmp at shutdown/reboot, the situation would improve.

-o-

There is an option to "Select Guided - use entire disk and set up encrypted LVM", which should improve the security above that of 'only encrypted home'.

See this link

[http://iso.qa.ubuntu.com/qatracker/testcases/1439/info](http://iso.qa.ubuntu.com/qatracker/testcases/1439/info)

---

### Post by Dave_L on 2013-08-02
You also have to consider different scenarios.

Examples:

1. While the computer is shutdown and powered off, someone steals it.
2. The computer is on, you're logged in, with the screen locked, and someone steals it.
3. While the computer is shutdown and powered off, someone boots with a Live CD and installs a key logger or other hostile application. Later you use the computer.

---

### Post by Dave_L on 2013-08-02
(duplicate)

---

