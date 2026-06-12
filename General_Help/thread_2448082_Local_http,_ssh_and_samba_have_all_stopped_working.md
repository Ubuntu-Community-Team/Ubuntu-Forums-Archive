---
title: "Local http, ssh and samba have all stopped working Just today on my office PC"
date: 2020-08-01
forum: General Help
---

### Post by maxabercrombie on 2020-08-01
[B][SIZE=2][FONT=arial]EDIT - I'll save everyone the hassle of reading all that! found the issue, seems to be rodent related! turns out that some services still work on a half chewed through Ethernet cable while others do not :confused: Thanks anyway.


Hi 

I am new here, but not new to Ubuntu. I have been using ubuntu as my main distribution for around 6 years now and if I have ever encountered issues I tend to try to fix them myself where possible or just suffer in silence, but today I have something that has completely baffled me and is so important that I need to reach out.

Here is the scenario, and apologies in advance for the length as it is quite a complex issue - 

I have 5 Ubuntu machines that all perform various tasks that sit in the garage quite happily. I have just upgraded my office PC, so my old one is now out there too making it 6 (so I have 7 in total). The 5+1 in the garage are all absolutely fine and work as well as they always have. My new Shiny office PC is the issue running Ubuntu 20.04. Just *today*, I am getting: 

1) 400 bad request (all browsers) when trying to connect to my pi-hole server management page but Internet web pages are fine. 
2) My samba share which is on the same box as my pi-hole server will also no longer connect from my office pc, and I cannot ssh from my office pc to any of them over the LAN. when I try to ssh it hangs for a minute or so and then returns Connection closed by 192.168.x.x port 22. 
3) Nothing of note in any logs (that I can see) for the ssh issue - it's as if I did not issue the command.
4) I have port forwarding set up on my router to gain access to my network externally which connects to my pi-hole (Not best practice I know, but hey) - if I use the full FQDN, ssh [EMAIL="user@somedomain.ddns.net"]user@somedomain.ddns.net[/EMAIL] I can get in fine from my office pc. Cannot see how that works and local does not as it's the same box I'm connecting to!
5) an ubuntu 19.10 VM installed on my Office PC running 19.10 works flawlessly when trying the above

Now, this is where things get weird, because if that was all, then I have plenty to go at to troubleshoot, but there is a twist:

The Garage PCs perform all of the above absolutely fine: 

1) I can ssh from any of them back to my office PC which has the latest openssh server installed.
2) they can all ssh to each other without issues
3) the ones that I use with a GUI can connect to my pi-hole server without the 400 bad request error
4) I can connect to my samba share with no issue from any of the Garage PCs
5) I can also use my pi-hole web console with no issues from my Android phone and browse my samba share along with ssh to any machine

The garage PCs are all various versions of things including Ubuntu 16.04, 18.04, 19.10 and Raspian something or other.

My Office PC is an AMD Ryzen 7 running on a B450 ATX ASUS board with an AMD Firepro V7900 Graphics card with 32 GB of RAM and a 1TB SSD.
[/FONT][/SIZE][/B]

[SIZE=2][FONT=arial]I'm hoping that it's just a duff patch that will soon be fixed that's caused this but I'm pulling out what little hair I have left so any help much appreciated. Also worth noting that there are no Microsoft or Apple products attached to this setup.

Thanks[/FONT][/SIZE]

---

### Post by tea for one on 2020-08-01
> **maxabercrombie said:**
> EDIT - I'll save everyone the hassle of reading all that! found the issue, seems to be rodent related! turns out that some services still work on a half chewed through Ethernet cable while others do not :confused: Thanks anyway.

Usually, the issue is a non-working mouse, yet yours is hungry for work ;)

---

### Post by maxabercrombie on 2020-08-01
Mouse through Ethernet - Literally!

---

