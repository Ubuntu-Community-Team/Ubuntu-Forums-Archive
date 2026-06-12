---
title: "Setting MFA 2FA google-authenticator but only for root user"
date: 2018-03-26
forum: General Help
---

### Post by wyattbiker on 2018-03-26
I would like to enable 2FA, using google-authenticator, when I SSH as root. Is it possible to set it up only for root but not for other  users? Or does the setup apply to all users on my server. I am using Ubuntu 16.04.

Any docs would be appreciated.

Thanks

---

### Post by dragonfly41 on 2018-03-27
I have also started looking at Two-Factor Authentication to use in server administration.

Now currently I am only in local server development mode so I'm just exploring the steps to take when I deploy.

I can share what I've researched so far.

...

First, I read about Google-Authenticator vs Authy

[https://www.howtogeek.com/199262/authy-two-factor-authentication-made-easy/](https://www.howtogeek.com/199262/authy-two-factor-authentication-made-easy/)

[https://authy.com/blog/authy-vs-google-authenticator/](https://authy.com/blog/authy-vs-google-authenticator/)

So I opted to start with Authy, although I will also research Google Authentication.

Now to answer your question you might find this tutorial helpful.

**How To Set Up Multi-Factor Authentication for SSH on Ubuntu 16.04**

[https://www.digitalocean.com/community/tutorials/how-to-set-up-multi-factor-authentication-for-ssh-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-multi-factor-authentication-for-ssh-on-ubuntu-16-04)


On the issue of setting up Multi Factor Authentication selectively for different users see the paragraphs below ... although I have not reached that stage in my experiments since I'm focussed on Authy to start with.


> Step 1

With the PAM installed, we'll use a helper app that comes with the PAM to generate a TOTP key for the user you want to add a second factor to. This key is generated on a user-by-user basis, not system-wide. This means every user that wants to use a TOTP auth app will need to log in and run the helper app to get their own key; you can't just run it once to enable it for everyone (but there are some tips at the end of this tutorial to set up or require MFA for many users).



> Tip 3 &#8212; Avoiding MFA for Some Accounts

As long as a couple of options in /etc/pam.d/sshd are set correctly, you can control which factors are used on a user-by-user basis.

---

### Post by wyattbiker on 2018-03-28
Ah yes. Great document. Thanks

---

