---
title: "GAIM not working in Ubuntu"
date: 2005-04-30
forum: General Help
---

### Post by surfduke on 2005-04-30
I recently installed ubuntu on my desktop machine and I cannot get GAIM to connect to any of the messenger services.  Sometimes MSN manages to SLOWLY connect.  But Not Yahoo or AIM/ICQ.  I love ubuntu.  It's an amazing distro, but I need to get this GAIM issue solved becasue we use it to communicate in my workgroup for my company.  If anyone has any ideas on how to fix this issue I'd sure appreciate the help.

Dennis

---

### Post by DJ_Max on 2005-04-30
The only reason I could see you not connecting to certain IM services is because AIM, YIM and whonot changed things around, and an older version doesn't support the new connection. But I don't think thats the case here. I'm using the latest version of Gaim (1.2.1), and don't have any problems. Are you behind a proxy or firewall?

---

### Post by rhys on 2005-04-30
[QUOTE=DJ_Max]The only reason I could see you not connecting to certain IM services is because AIM, YIM and whonot changed things around, and an older version doesn't support the new connection. But I don't think thats the case here. I'm using the latest version of Gaim (1.2.1), and don't have any problems. Are you behind a proxy or firewall?[/QUOTE]
 Gaim 1.2.1 is reluctant to change my msn screenname. :( I would think that 1.5.1-current would solve that, if only I could build it for ubuntu (glib not available)....

I do think that the package needs to be updated, no?

---

### Post by surfduke on 2005-05-01
I'm not sure if ubuntu firewall is on.... is it on by default?  I don't think it's my router since GAIM works in XP and SUSE.  Could it be something else?

Dennis

---

### Post by surfduke on 2005-05-01
Very Strange...... I applied this script [http://ubuntuforums.org/showthread.php?t=22646](http://ubuntuforums.org/showthread.php?t=22646) and GAIM started working.  I still do not have the latest version of GAIM.  How doi I get it for ubuntu?

---

### Post by DJ_Max on 2005-05-01
[QUOTE=surfduke]Very Strange...... I applied this script [http://ubuntuforums.org/showthread.php?t=22646](http://ubuntuforums.org/showthread.php?t=22646) and GAIM started working.  I still do not have the latest version of GAIM.  How doi I get it for ubuntu?[/QUOTE]
 You have two choices, use the backports (unofficial), or compile it yourself like I did.

---

### Post by surfduke on 2005-05-02
[QUOTE=DJ_Max]You have two choices, use the backports (unofficial), or compile it yourself like I did.[/QUOTE]

How do I compile it myself?  I have never done that before.  Thanks for the help.

Dennis

---

### Post by btdown on 2005-05-02
Yeah how do you compile it yourself? And why would you want to? Shouldnt the most recent version of the software be in the repositories? 
 
And also...If you compile your own version, will it screw things up when (if ) a new version hits the repository?](*,)

---

### Post by DJ_Max on 2005-05-02
[QUOTE=btdown]Yeah how do you compile it yourself? And why would you want to? Shouldnt the most recent version of the software be in the repositories? 
 
And also...If you compile your own version, will it screw things up when (if ) a new version hits the repository?](*,)[/QUOTE]
 No it would not mess anything up, you forget, that in order for someone to make a binary, they must compile on their machine first. There are a number of reasons why compiling software is better then using third-party pre-compiled versions(i.e., this is one of them) No the latest version isn't in the repositries all the time. The latest version of Gaim when I had Ubuntu was 1.1.4, the latest Gaim package availabe is 1.2.1.

Compiling software is simple, usually instructions come with it. Gaim is one of them.
Basicl it's 
./configure
make
make install

---

### Post by dewey on 2005-05-02
Compiling your own software tailors it to your own machine, rather that a generic one, the disadvantage is that there's no nice system for maintaining your source programs like that.  If you compile it from source, you won't be able to use dpkg to uninstall it, unless you created a .deb file of it.

---

