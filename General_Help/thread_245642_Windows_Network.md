---
title: "Windows Network"
date: 2006-08-28
forum: General Help
---

### Post by JoshHendo on 2006-08-28
Ok, so I have Ubuntu on a windows network. I have samba installed and everything, and I can see all the computers on the network.

The only computer that I can actually access is the one that I am currently using.

Any other computer comes up with the following message:

```
The folver contents could not be displayed.

Sorry, couldn't display all the contents of "Windows Network: <computer name>".
```

How would I fix this so it is easy to access opther comptuers on the network?

Thanks :)

---

### Post by Uluen on 2006-08-28
Are they all in the same workgroup? Is your username/pass the same on all computers?

---

### Post by JoshHendo on 2006-08-29
They are all on the same workgroup and I can't even access computers with no passwords. I would assume that if it needs a password, it will ask me for a username and password?

Thanks :)

- Josh

---

### Post by robt3hpirate on 2006-09-04
I'm getting this same error and they are on the same work group and  i believe the username and password are the same.

---

### Post by jongkind on 2006-09-04
Verify whether samba is installed in the right way and that you made the right tweaks to /etc/samba/smb.conf. Good instructions are given
[here]("http://www.ubuntuforums.org/showthread.php?t=76647").

Furthermore Samba works best when you access the network computers via their IP adress. Let's assume that you want to access the PC with IP 192.168.1.101: 
[LIST]
[*]open the location bar in Nautilus
[*]type smb://192.168.1.101/
[*]After this nautilus should displayed the shared folders of the network computer with IP address 192.168.1.101
[/LIST]

I hope this helps

---

### Post by robt3hpirate on 2006-09-04
i reinstalled samba with synaptic and re did all of samba.conf. and i also tried viewing it with natallist and it still didn't work. the thing that is odd for me is that, first i can get files off my ubuntu machine, and both see each other on the workgroup. the problem is that when i try to click on the windows server in ubuntu it says that error (can not open all files) i also removed everything except one folder with just one picture in it and still same thing happens. i suspect that its a windows error and not a ubuntu however but i guess its just a shot in the dark right now. if anyone knows what this error "means" and a new suggestion on how to fix it i'd love to hear any theroy. the error reads " The folder contents could not be displayed sorry, couldn't display all the contetns of "Windows Network: computername"."

---

### Post by heathen on 2006-10-08
I get this same error... any help?

---

### Post by dcstar on 2006-10-08
You may want to enable the "Guest" account on the Windows machines, and set the Windows Share/directory/file permissions to allow Read access to the Guest account.

It looks like an authentication issue, if you also look at the Windows Event files when you try the access you may well see error messages explaining the problem.

---

### Post by HereInOz on 2006-10-08
Just a long shot - check your firewall on both ends of the network.  It could be the culprit - dropping the packets.  I don't have a problem with Ubuntu to Windows XP, so I can't say for sure, but it is the place where I would start.

---

### Post by Iowan on 2006-10-11
I've seen that message (looking at it now) when I set up a share on a Windows (XP) box, but the (Windows) firewall does not have an exception set for file and printer sharing. (I got a similar message when I rebooted the Windows box and tried to access the share before the reboot completed.

As a sidenote, after I changed the firewall back, I still can't see the folder I could access before.
Well... I dinked with it long enough and got access back.

---

