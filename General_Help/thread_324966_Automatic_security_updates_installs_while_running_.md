---
title: "Automatic security updates installs while running as desktop user?"
date: 2006-12-24
forum: General Help
---

### Post by Spin Doctor on 2006-12-24
Scenario:

I am a desktop user, meaning I dont have rights to administer the system.

Lets say I prefer running the system as a desktop user since this is more safe than running it as an administrator (rights to administer the system). Would Ubuntu let the system install automatic security updates without confirmation running as desktop user? 

I know there is an option for installing security updates without confirmation in: **System>Administration>Software sources**, under the ** Internet updates tab**. (If you are running with system admin rights)

However, I am assuming you have to have rights to administer the system for this to work automatically.

But, could someone  confirm to me that if this is the case or not, because [COLOR=Red]**[COLOR=Black]_would it not be nice if a desktop user also could have the option of security updates installed without confirmation?_[/COLOR]**[/COLOR]

---

### Post by dorcssa on 2006-12-24
What do you mean by security updates? The update notifier will tell you if something needed to update(all of your programs), and you can install them very easily. It's only asking for your password. You know about sudo, don't you? Look at this: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Dubbayoo on 2006-12-24
I use the account I created during install. I'm not sure which additional rights that account has but I am able to install security updates while logged in with that user. I can't recall if I ever accepted a previous prompt to allow that or not.

---

### Post by Spin Doctor on 2006-12-24
> **dorcssa said:**
> What do you mean by security updates? The update notifier will tell you if something needed to update(all of your programs), and you can install them very easily. It's only asking for your password. You know about sudo, don't you?.....

Security updates are those who fixes securityflaws on your Ubuntusystem. If look under software sources and click on the internet update tab, you will see what I mean...

_ The update notifier does not run when you are logging in as a desktop user_. If you look at your rights, and have all rights except "administer the system", you cant use sudo, or anything else that requires "system rights".

I personally, prefer not being an administrator if I dont need to. 

**For Dubbayoo:**
The account you create during installation will always be in your admin group, which has rights to administer the system. Try creating yet another account on your Ubuntu, and you will find out it will create it as a desktop user with no rights to administer the system...if you dont change the default values...

---

### Post by Spin Doctor on 2006-12-24
Oh yeah.... dont downgrade your admin account to a desktop user....it would be some extra work for you to get it back again.... Create a new useraccount to test if you want to...

---

### Post by dorcssa on 2006-12-25
Ok, now I know what's your problem is. But I see no point using a desktop user, hence the user who has administrating right has to use sudo when administaring something, and I think it's safe enough. And it would in a pain in the a**, if I couldn't use sudo while everyday use..

---

### Post by Spin Doctor on 2006-12-25
Well, if you running administrative tasks on a daily bases, yeah living without sudo would be a pain... But for regular users who dont install new software on a daily basis or tweek administrator settings, it is easy to log in to your admin account when needed. 

If you are a regular plain desktop user who does his wordproccessing, surf the internet, email and such, there is no need of the constant sudo privileges. 

What I have learned, is that you should never have more rights that absolutely necessary. I think this should be appliable on Linux systems aswell. . 

Let's say you are running an internetcafe with Ubuntu installations. Would you like them to be part of the admin group, or would you set them up as desktop users?

---

### Post by dorcssa on 2006-12-25
Ok, desktop user would be my choice. Like in win, an administrator of a company set the pc's for desktop users. But I'm learning linux, so I'm not an avarage desktop user. :D

---

