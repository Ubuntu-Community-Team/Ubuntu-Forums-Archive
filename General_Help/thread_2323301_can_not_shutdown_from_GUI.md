---
title: "can not shutdown from GUI"
date: 2016-05-04
forum: General Help
---

### Post by roya2 on 2016-05-04
Hi, when I click on shutdown from the right corner in ubuntu 12.04 the system is not shutting down and is just logging out. Is it anything in the settings or files that I should change ?
The command-line works (sudo shudown now) . But I want to be able to do it from GUI. 
I saw other threads but they were not asking for GUI shutdown. 
Thanks.

---

### Post by T.J. on 2016-05-04
> **roya2 said:**
> Hi, when I click on shutdown from the right corner in ubuntu 12.04 the system is not shutting down and is just logging out. Is it anything in the settings or files that I should change ?
The command-line works (sudo shudown now) . But I want to be able to do it from GUI. 
I saw other threads but they were not asking for GUI shutdown. 
Thanks.

As a general suggestion, I would consider saving yourself the time to fix it, and just upgrade to a new version.  You will have to upgrade to at least 14.04 by the end of 2016 if you want to have support.  Support for 12.04 will end in April 2017.


If you prefer to stick with what you have, then what we do next depends on what GUI you are using. There is more than one.  It also depends on what changes you have made since your install.  I'm sorry, but I can't give you a more specific answer without more details.

---

### Post by roya2 on 2016-05-06
Thank you for your response. I have installed ubuntu 12.04 recently and the shutdown from the menu in the right corner did not work from the beginning. What information can I post here so that you can help?
Thank you.

---

### Post by steeldriver on 2016-05-06
Are you logging in with a user account that belongs to the sudo group, or as an unprivileged user?

I *think* the way that it works is that actions such as shutting down / rebooting / modifying network settings are controlled by PolicyKit, but that PolicyKit assigns its "localauthority" based on membership of the unix-group "sudo"

---

### Post by roya2 on 2016-05-06
When I want to shutdown from terminal I have to do 'sudo' .  So probably I am an unprivileged user. I changed the sudoers file at /etc/sudoers and I do not need to enter password for shutdown. Do I need to change PolicyKit? I am not familiar with that. Can you explain? thanks.

---

### Post by steeldriver on 2016-05-06
No - if you are allowed to do "sudo shutdown" then you are for sure a member of the sudo group

So it must be something else that's preventing shutdown. In fact I think I misunderstood your question - if you're not privileged, the menu shouldn't even offer the shutdown / reboot option

If it's allowing you to select "Shutdown" from the menu but then is not actually shutting down, that's something different - sorry

---

### Post by roya2 on 2016-06-02
I just figured out that this was a live image of ubuntu 12.04 (customized os )  not a fresh install.

---

