---
title: "Samba without making additional accounts?"
date: 2014-09-25
forum: General Help
---

### Post by AwaitingUserInput on 2014-09-25
I've recently formatted my hard drive and am starting fresh with a new installation of Ubuntu. I would like to configure Samba so that I can access my files from a variety of devices, but not have to make additional users. The last time I set up Samba (over a year ago), I created a new user account and then gave access to that account. This caused problems because if I wrote a file to my Ubuntu machine's hard drive from a client computer, it would be owned by another user so I had to sudo chown ... every time I copied data onto my computer.

Is there a way to just register my devices and have it default so that my regular Ubuntu user account is the owner? I do want to block access from people that are visiting my house, so I don't want to leave the network wide open.

I have a Windows 7 machine, another linux machine, and a couple android devices.

---

### Post by TheFu on 2014-09-25
Why no use the normal userid that you always use?  I'm confused.
If you don't want others to see it, don't give guest/everybody access.

So - what have you tried?

---

### Post by papibe on 2014-09-25
Hi AwaitingUserInput.

You may just need to force that all files be saved using a particular user (yours for instance).

You can add this globally or under a single share:
```
force user = youruser
```
where 'youruser' is your actual Linux username.

Hope it helps. Let us know how it goes.
Regards.

P.S.: remember you'll need to restart samba.

---

### Post by AwaitingUserInput on 2014-09-26
> **TheFu said:**
> Why no use the normal userid that you always use?  I'm confused.
If you don't want others to see it, don't give guest/everybody access.

So - what have you tried?

I will try to do it that way. Please understand, I'm still at the level where I just cut and paste and maybe do tiny modifications here and there based on written instructions. The way I set up Samba last time was by following this web page: [http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/)

Most other guides I have seen say to create a new linux user for each person with access.

As you and the other person suggested, I will try to just log in with my normal username and see how that works. It sounds so simple and obvious now, but as I said, all the guides that I saw online involved creating new users, so it never occurred to me to just use my one account's credentials. I'll report back when I have a moment to try that. Thank you!

---

### Post by TheFu on 2014-09-26
Just read that guide.  I didn't see anything inside it that says NOT to use your Linux account as the samba account.  You will still need to use smbpasswd to initially set any user passwords, but after that, things just work.

At least that has been my experience.

BTW - I'd be careful using 
```
force user = youruser
``` in your environment. I think that is more for groups of users and everybody/all connections to make things just work on the linux side. With what you want (or my understanding of it), this won't be an issue at all.  1 user makes things easy - provided you only use 1 user.

If you do want more than 1 user, that's where using Linux groups becomes important and more than a passing understanding of them and file permissions matters.

---

### Post by AwaitingUserInput on 2014-09-26
I just wanted to update that I was able to make a samba user that was identical to my login name / password for my main Ubuntu machine. It went together really easily and I no longer have the hassles of having to change ownership of the files the way I used to do when I used separate user IDs.

Also, I did not do "force user." I just made a Samba user the normal way and named it the same as my login ID.

Thanks for the help!

---

### Post by TheFu on 2014-09-27
So - solved then? Please mark the thread solved, if true.

---

### Post by MGrs on 2014-10-16
Hi!
And do you know if it's possible not to create unix user for each samba user? I'd like to share files among various users (samba users) without the need for creating new unix user. Maybe it would be possible to have some samba users but just one unix user??
What about this parameter forced user? Do you think it might help?

---

### Post by papibe on 2014-10-16
@MGrs,

That's is exactly the purpose of the 'force user' option. Although, somehow, this creates a valid security concern, in my assessment this concern is more valid in a context of a company network, and not so much in case of a home network.

Regards.

---

### Post by MGrs on 2014-10-17
ok, I'm not sure if I understand properly the sense of this parameter after reading documentation. Could you just in few words explain that to me.
What if I have some workers in a company, for example 5 (let's assume monika, anna, eric, richard and eva) , each of them has different rights.
If I'd like to share something among them but for example some shares would be accessible only for two of them, others for just one and some for all. I would probably specify it using 'valid users'/'invalid users'.
What kind of users should I create then?

---

