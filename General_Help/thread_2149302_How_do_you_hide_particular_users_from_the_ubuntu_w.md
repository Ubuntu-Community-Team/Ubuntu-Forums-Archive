---
title: "How do you hide particular users from the ubuntu welcome screen?"
date: 2013-05-28
forum: General Help
---

### Post by apollothethird on 2013-05-28
Can someone help me with hiding particular users from the ubuntu welcome screen.  I've followed the steps provided in:

How do I hide a particular user from the LightDM login screen?:
[http://askubuntu.com/questions/92349/how-do-i-hide-a-particular-user-from-the-lightdm-login-screen](http://askubuntu.com/questions/92349/how-do-i-hide-a-particular-user-from-the-lightdm-login-screen)

These steps are repeated in on numerous sites.  However, it doesn't work in release 12.04.  I have a fresh install.  I performed the steps and rebooted the computer.  The users that I add the the "hidden-users=nobody nobody4 noaccess" line are still displayed on the Welcome screen.

I also see references about adding a line in the /etc/lightdm/lightdm.conf.  The line, "greeter-hide-users=true", will hide all the users, not just the particular users I would like to specify.

Thanks in advance for anyone that has any input or suggestions of things I can test.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

---

### Post by zombifier25 on 2013-05-28
Please read the entire page. The answer on AskUbuntu stated that
> Currently this method is not working because of a [bug](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/857651) in lightdm.

Please check the bug status before applying this method.

And the bug is not fixed, so you will have to modify the uid of the user you want to hide to a value less that 500. Run this command:
```
sudo usermod -u 499 user-name
```
Replace user-name with the actual username.

---

### Post by apollothethird on 2013-05-28
> **zombifier25 said:**
> Please read the entire page. The answer on AskUbuntu stated that


And the bug is not fixed, so you will have to modify the uid of the user you want to hide to a value less that 500. Run this command:
```
sudo usermod -u 499 user-name
```
Replace user-name with the actual username.

Thank you very kindly for your reply and suggestion.  And yes.  I read the entire page.  I followed the bug link and know it doesn't work.  As I mentioned, I see this suggestion repeated numerous times.  Some of the times it's presented they don't mention that it's a bug, it's presented as a solution.  So I posted it to remind anyone that might give that suggestion, that it doesn't work.

I can't change the user ID for each user because I use the common UID for other conveniences across the local network as well as VPN.

I posted this message in case there was something that I was missing, some type of tweet that would make it work while, of course, the developers are fixing the bug.

I read somewhere that you can change and use gdm instead of lightdm to get it working, but I wasn't to keep the system as clean as I can if possible... but of course, if changing from lightdm to gdm is the only way to go I may start working on that.  It's really pretty bad that you have to either display all or none (or as you mentioned, change the UID... which the latter isn't and option... it'd cause other problems in my network).

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

