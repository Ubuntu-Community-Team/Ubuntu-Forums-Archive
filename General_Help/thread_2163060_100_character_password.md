---
title: "100 character password"
date: 2013-07-16
forum: General Help
---

### Post by SchnappiJedi on 2013-07-16
Hi,

This isn't a big deal as I did this in the first place to see what would happen. I will be re-reinstalling this particular server anyways. Using a single user and no root login I changed the password to a 100 character password through an ssh connection. The password change went through. But after exiting the session and trying to login again I can no longer login with either the new 100 character password or with the old password.

Is this a bug or is there a password limit in Ubuntu?

---

### Post by SchnappiJedi on 2013-07-16
Ah forgot. Version 12.04.2 LTS

---

### Post by HiImTye on 2013-07-17
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
better to disable password authentication and use keys
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)
you should be able to go to recovery mode and reset your password, or you may find some success using a livecd. as for a password limit, there shouldn't be one, as a salted hash of your password is used in lieu of your actual password.

---

### Post by t0p on 2013-07-17
I have often come across situations where a password has to be 64 characters or less.  For some reason I have taken this onboard and generally assume the 64 character limit is something built into ssh/ssl/etc.  That's just me though (and stuff I've read that made me think this).  If I'm wrong, I shall crash, flaming, into the mountainside.

---

### Post by SchnappiJedi on 2013-07-17
> **HiImTye said:**
> better to disable password authentication and use keys
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)
you should be able to go to recovery mode and reset your password, or you may find some success using a livecd. as for a password limit, there shouldn't be one, as a salted hash of your password is used in lieu of your actual password.

Thanks. I know I could reset with a CD, but this was more an experiment that I half way expected to break a server that needs to be-rebuilt anyways. In regards to your other point. I am not fan of keyfile authentication. As I understand the same keyfile must be shared across all users (some who may not be in the sudo group). I deem that a serious serious risk. Granted in my example there was one user though. And this is not even mentioning that keys sometimes end up being sent via insecure methods which is another security risk. I guess the same can be true of passwords, but keys seem to lend themselves to need to occasionally be sent via an insecure method such as email more often than even a complex random password.

---

### Post by SchnappiJedi on 2013-07-17
> **t0p said:**
> I have often come across situations where a password has to be 64 characters or less.  For some reason I have taken this onboard and generally assume the 64 character limit is something built into ssh/ssl/etc.  That's just me though (and stuff I've read that made me think this).  If I'm wrong, I shall crash, flaming, into the mountainside.

I think that you are right in theory. However 64 characters very well may not be the magic number for ssh at least...

Anywho to sum up. I can confirm that I could not login to Ubuntu 12.04.2 LTS via SSH after changing to a 100 character password and rebooting. Maybe I will try again in the near future in a virtual machine to confirm my findings.

---

### Post by prodigy_ on 2013-07-17
> **schnappi2 said:**
> As I understand the same keyfile must be shared across all users
Actually you can make your server accept as many public keys as you want. They don't have to be shared between users in any way and they can be further protected with passphrases. And even a shared key can be "revoked" (by removing it from **authorized_keys** files) at any time.

---

### Post by rnerwein on 2013-07-18
> **schnappi2 said:**
> Hi,

This isn't a big deal as I did this in the first place to see what would happen. I will be re-reinstalling this particular server anyways. Using a single user and no root login I changed the password to a 100 character password through an ssh connection. The password change went through. But after exiting the session and trying to login again I can no longer login with either the new 100 character password or with the old password.

Is this a bug or is there a password limit in Ubuntu?
hi
this sounds for me: it's a bug in the sshd. is the deamon still running after exiting the login ? 
start your connection in debug-mode. 
by the side - sounds very strange. 100 char for an password - think nobody tried before.
ciao

---

### Post by CaptainMark on 2013-07-18
> **schnappi2 said:**
> I am not fan of keyfile authentication. As I understand the same keyfile must be shared across all users (some who may not be in the sudo group). I deem that a serious serious risk.Password-less authentication is by far more secure than any password you can come up with, what could be more secure than only allowing pre-authorized computers to connect?

---

### Post by t0p on 2013-07-30
> **CaptainMark said:**
> Password-less authentication is by far more secure than any password you can come up with, what could be more secure than only allowing pre-authorized computers to connect?

Just to play devil's advocate: I know you have an account on a server; I steal your pre-authorized laptop and access your account on the server.  If you were using password authentication (and followed strong password protocols) I would have to torture you or steal your brain to get into that account.

Stupid scenario, I know.  But devils' advocates dig stupid scenarios (otherwise they'd work for the Goddess, eh?)

---

### Post by CaptainMark on 2013-07-31
> **t0p said:**
> Just to play devil's advocate: I know you have an account on a server; I steal your pre-authorized laptop and access your account on the server.  If you were using password authentication (and followed strong password protocols) I would have to torture you or steal your brain to get into that account.

Stupid scenario, I know.  But devils' advocates dig stupid scenarios (otherwise they'd work for the Goddess, eh?)
Not stupid at all, it's a valid point but not one that I haven't planned for. The laptop has an encrypted home folder so no-one can access the data on it (RSA keys are stored in your home folder so wouldn't be readable without logging in) and as a second security net you can still lock the RSA keys so they still require a password to be used (kind of like a second encryption), I make the RSA password nice and strong and choose not to save it on the laptop but to punch it in manually each time. If in the event that I lose my laptop (because you stole it you evil person!! :mad:) then way before you have the chance to crack both of my passwords, I would have more than enough time to connect to my server and remove the laptop from authorized_keys.

Whilst no method in the world is 100% secure, this is about as close as you'd get for a home setup, and is about a thousand times more secure than just making even a 100 character password to login.

When it comes to laptops, they are as secure as you are vigilant, and as venerable as you as careless.

---

### Post by t0p on 2013-07-31
> **CaptainMark said:**
> Not stupid at all, it's a valid point but not one that I haven't planned for. .

Bah!  If you insist on being right, how am I supposed to prove you wrong?  I call foul!  ;)

---

### Post by SchnappiJedi on 2013-07-31
Just to confirm. I recreated the 100 character password failure in a virtual machine. So I can confirm there absolutely is a bug somewhere that prevents a 100 character password from being sent over ssh.

*To clartify further. You can change your current password to a 100 character password over shh. However you will not be able to login next time you try over ssh.

---

### Post by CaptainMark on 2013-07-31
@t0p: Time to call in the judges then....

@schnappi2: Well then I suppose you have found a bug in the ssh client, assuming you're using openssh-client then here's the guidelines to bug reporting [http://www.openssh.org/report.html](http://www.openssh.org/report.html), but I wouldn't keep your hopes up for them taking it too seriously, how many people have a 100 character password? You're probably one of only a few, most people serious about security use the above method

---

### Post by SchnappiJedi on 2013-08-09
> **CaptainMark said:**
> @t0p: Time to call in the judges then....

@schnappi2: Well then I suppose you have found a bug in the ssh client, assuming you're using openssh-client then here's the guidelines to bug reporting [http://www.openssh.org/report.html](http://www.openssh.org/report.html), but I wouldn't keep your hopes up for them taking it too seriously, how many people have a 100 character password? You're probably one of only a few, most people serious about security use the above method

I don't think I am going to report it. After all TrueCrypt passwords are limited to 64 characters so I don't see why an Ubuntu installation would need to be "more secure" than a TrueCrypt container or encrypted drive.

---

