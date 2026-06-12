---
title: "Ubuntu Single Sign-On Account never logs in"
date: 2021-10-06
forum: General Help
---

### Post by kingpenguin on 2021-10-06
When I am trying to log into my ubuntu single sign on account it just spins forever saying "Connecting". I have left if for hours but it just spins. I can log into ubuntu one to get into the forums but just not the os for live patch. I have tried to reboot and it does not solve the issue. Is there any log that I can get to find out what is going on? I am using ubuntu 20.04.

[IMG]https://preview.redd.it/99hoimlryqr71.png?width=556&format=png&auto=webp&60769336[/IMG]

---

### Post by kingpenguin on 2021-10-06
I am not sure if this helps at all but I have been doing some digging around and I have some weird messages about apparmor in dmesg. I am going to try and disable apparmor and see if I am able to sign into ubuntu one.

---

### Post by QIII on 2021-10-06
Do you have more than one Ubuntu One login?

The Ubuntu One account you use to sign in here should apply to all Ubuntu sites run by Canonical.

If there is a problem, we can't help with that.  We don't administer Ubuntu One.  You may find information to help [here]("https://login.ubuntu.com/+faq") or [here]("https://help.ubuntu.com/community/SSO/FAQs").

---

### Post by dain-bramage on 2021-10-06
I am having this exact same problem on Ubuntu 21.04.

I only have one Ubuntu One login.

Someone else got this problem too.

[https://www.reddit.com/r/Ubuntu/comments/q2rg4g/ubuntu_single_stuck_on_connect/](https://www.reddit.com/r/Ubuntu/comments/q2rg4g/ubuntu_single_stuck_on_connect/)

Look forward to a solution.

---

### Post by roadmr on 2021-10-06
> **dain-bramage said:**
> I am having this exact same problem on Ubuntu 21.04.

I only have one Ubuntu One login.

Someone else got this problem too.

[https://www.reddit.com/r/Ubuntu/comments/q2rg4g/ubuntu_single_stuck_on_connect/](https://www.reddit.com/r/Ubuntu/comments/q2rg4g/ubuntu_single_stuck_on_connect/)

Look forward to a solution.


Hello folks,

I don't think this is related to Ubuntu One logins. If you're able to post in this forum, then your Ubuntu One login is working and there is nothing wrong with that service. It might be a problem with Ubuntu itself and integration with the login service. In this case it should be reported as an Ubuntu bug, possibly (if this happens when trying to enable livepatch) as part of [https://launchpad.net/canonical-livepatch-client](https://launchpad.net/canonical-livepatch-client).

An easy way to test - in  your browser, go to [https://login.ubuntu.com](https://login.ubuntu.com). If you are able to log in there and get to a page with generic account details, then the problem is NOT with the Ubuntu One SSO service. 

- Daniel

---

### Post by kingpenguin on 2021-10-06
I never said the issue was with the ubuntu sso service. I am just not able to log into it from my computer. I am really not sure where to submit bugs other than in the forums. Where can I report this issue?

---

### Post by psychohermit on 2021-10-06
I just logged onto the SSO login and it worked fine.

--glenn

---

### Post by roadmr on 2021-10-07
Hello again,

We traced the problem to another service the Online Accounts panel talks to, in the process of setting up the Ubuntu One account. As I mentioned earlier, it's not directly/strictly speaking the SSO service itself, but that's beside the point.

We will have it fixed in the next 30 minutes or so.

Thanks for your patience :)

---

### Post by kingpenguin on 2021-10-09
Mine is still not connecting today. I have just tried. It just spins saying "Connecting...". It is not locking up the settings application but I am getting "Error connecting to Ubuntu Single Sign-On server: Provided email/password is not correct. I am pulling the password from my password manager that I used to log into the ubuntu forums on my web browser.

---

### Post by kingpenguin on 2021-10-09
Found this was a dns issue even though I could log using ubuntu one account on my web browser. Maybe they use a different address.

---

