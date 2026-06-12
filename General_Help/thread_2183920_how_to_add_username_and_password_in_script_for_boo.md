---
title: "how to add username and password in script for bootup login"
date: 2013-10-26
forum: General Help
---

### Post by avinashrao47 on 2013-10-26
I am looking for help in writing script to enter password and username automatically(using script) for ubuntu(linux) login. 

Thanks,

---

### Post by deadflowr on 2013-10-26
Do you want to autologin?

If so, that can be set in the users account in system settings.
Set the user to automatically login and it will skip the login screen and log the user in.

---

### Post by avinashrao47 on 2013-10-27
Thanks for the reply.. 
Yes, It has to autologin... 
By doing settings in user account,every time it will be login directly and it will not be secure. Also in my requirement, we should not disable password protection.  We have to provide from script and so that it will run automatically for every system restart. 

Could you please provide where and when login will come in system bootup flow. 
Thanks,

---

### Post by deadflowr on 2013-10-27
It's 100% secure

Autologin does not disable the password.

It just doesn't require a password to login.
Doing administration work will still need the password.

---

### Post by avinashrao47 on 2013-10-27
Thanks for the info... We will consider this possibility...
But is there any possibility of without disabling password and passing through script.. Also if possible please provide any info of when and where login page will be appear in booting procedure..  

Thanks,

---

### Post by deadflowr on 2013-10-28
I don't know where you get the idea that autologin disables the password.
It doesn't.

---

### Post by avinashrao47 on 2013-10-28
Do you mean, it is not possible to pass login username and password using script. 
If possible please provide where/when login page will be appear in booting procedure...

---

### Post by deadflowr on 2013-10-28
> **avinashrao47 said:**
> Do you mean, it is not possible to pass login username and password using script. 
If possible please provide where/when login page will be appear in booting procedure...

I'm not saying that.
I'm saying setting the user to autologin does not disable the password.
It just sets the user to login in without needing to enter a password.

It's the simplest way.

---

### Post by ian-weisser on 2013-10-28
> **avinashrao47 said:**
> I am looking for help in writing script to enter password and username automatically(using script) for ubuntu(linux) login.

deadflowr is right. Use the existing autologin. It's safe and secure. That is what it is for.

Putting your password in a script is insecure and unwise. This community, in the past, has strongly advised against workarounds that defeat your system's security by exposing passwords.

---

### Post by avinashrao47 on 2013-10-29
Thanks for the reply... 

Could you please provide info for when/where login page will be appear in bootup flow.

---

