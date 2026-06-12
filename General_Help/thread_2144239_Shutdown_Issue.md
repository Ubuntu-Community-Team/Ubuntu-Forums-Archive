---
title: "Shutdown Issue"
date: 2013-05-11
forum: General Help
---

### Post by iDrofox on 2013-05-11
Hello, I am new to this forum and i came here for help!

My issue is that my ubuntu 13.04 is not shutting down. It just hangs at shutdown screen with dots keep running. It didn't show a error it just freezes there and then i have to use power button on pc tu restart directly!

----------------------------------
[B]Issue Solved:
I found that my ubuntu is not starting due to metasploit service not closing. So, i turned it off using bootup-manager and now my ubuntu is shutting down properly. Please close this thread now and mark this as solved!
Thank You
-----------------------------------[/B]

**When problem started to occur:**This problem started to occur when i disabled ubuntu error manager or whatever it is because i am tired of getting an error releated to "Speech Dispatcher".Now i trying to enable error manager again maybe it will solve the problem!

What is tried:
"**sudo service lightdm restart**" - Stuck after showing " *** Checking Battery Status [Ok]**".
"**sudo gedit /etc/default/speech-dispatcher**" set it to yes, ubuntu takes more booting time after doing this change. However it still hangs at shutdown!
"**sudo shutdown -h now**" - Didn't help! still hangs at shutdown screen!
"**sudo poweroff**" - Same story it just hangs on shutdown screen forever.

Please help me i am trying my best but i am new to linux and need assistance to solve this problem.Any help would be appreciated.Thanks

Regards
iDrofox

---

### Post by Hyper Tails on 2013-05-11
I have a similar issue too.

When I click on the shut down button on my top right-bar, it doesn't shut down; I have to got to terminal and type **sudo poweroff** in order for me to shout down my computer. It's very annoying!

---

### Post by iDrofox on 2013-05-11
> **Hyper Tails said:**
> I have a similar issue too.

When I click on the shut down button on my top right-bar, it doesn't shut down; I have to got to terminal and type **sudo poweroff** in order for me to shout down my computer. It's very annoying!
Thanks for the reply but it didn't help either!

It looks like the problem is with "speech dispatcher".However i am still trying to find the cause of this problem.

---

### Post by iDrofox on 2013-05-11
----------------------------------
[B]Issue Solved:
I found  that my ubuntu is not starting due to metasploit service not closing.  So, i turned it off using bootup-manager and now my ubuntu is shutting  down properly. Please close this thread now and mark this as solved!
Thank You
-----------------------------------[/B]

---

