---
title: "needing to switch users before login"
date: 2017-06-12
forum: General Help
---

### Post by ktat on 2017-06-12
Hi All,

I am running ubuntu 17.04 - and very happy with how it goes in general.  However, recently, I added a guest account. Since then, whenever I start up my laptop, I'm presented with a prompt for the guest account login.  If I want to use my account I have to select it from the options at top right of screen.  I realise this is a small issue, but surely there is a way to set up the login screen so it offers both account options or defaults to my account.

ta,

---

### Post by TheFu on 2017-06-12
17.04 is too new for me, but you should be able to setup the login screen NOT to have selections, rather just a text entry field for the account and password.

I wouldn't send too much time on it.  The login manager is changing in future releases because the gnome login manager is tightly coupled.  Though I'm not positive that will happen on all alternate Ubuntu releases (lxde, xfce).  I only skimmed an article about this last week.  It also mentioned that the generated guest account options are or already are gone due to a security issue.

---

### Post by ktat on 2017-06-13
so, I deleted the Guest account and created another "Visitor" account and set it to so that it could login without a password.

Now when I boot Ubuntu just goes straight to my visitor desktop - surely this is unusual behaviour.  How can I fix this so that, on starting Ubuntu, it goes to the login screen and gives me an option to choose who logs in?

---

### Post by again? on 2017-06-14
If you set an account to autologin ...it will do what you're seeing.

This confuses me.
> I have to select it from the options at top right of screen
Are you using the unity lightdm greeter?
Which account are you referring to  when you said you deleted the guest account?
How did you delete it?
[[img]https://s19.postimg.org/ezkzqapgf/Light_DM_1.2.1_on_Ubuntu_12.04.png[/img]](https://postimg.org/image/ezkzqapgf/)

In my 16.04 ubuntu install the user in focus at the greeter is the one which was last logged in.
So if the guest or visitor account was the last one logged in to, that is what will be in focus at the greeter.
There used to be a config setting for default-user but I don't think this works anymore.
You can set an autologin after a timeout period.

The output of this command may be helpful.
```
lightdm --show-config
```

---

### Post by RobGoss on 2017-06-14
I've booted up one of my Ubuntu machines only to face this same issue, at first I thought there was something wrong with my system because when it booted up it when to the guest account but after I noticed the purple background wasn't what I had set and was not the default login I just changed it and was able to login as usual. I'm  not sure why this happens

---

### Post by ktat on 2017-06-14
Thanks guber, I will try and make things clearer.  

In my first post, what I was trying to say was that my account wasn't listed (in focus or otherwise) along with the Guest account.  To login with my account, I had to use the icon at the top right of the screen to select my account and then the screen refreshed and I was presented with my username and the password entry field.

I deleted the guest account by logging in to my account (administrator) and going to system settings/users and then deleting the Guest account from there.

The login screen behaviour that you get with 16.04 is what I would expect, however this isn't happening for me.  Now that I have set up a Visitor account with no password required, when Ubuntu boots it goes straight to the visitor Desktop.  Even if last time I shutdown I was logged in with my own account.

Here is the output of **lightdm --show-config**:

```
 [Seat:*]
F  user-session=ubuntu
A  unity-compositor-command=unity-system-compositor.sleep
A  session-wrapper=lightdm-unity8-session
B  allow-guest=false
D  greeter-wrapper=/usr/lib/lightdm/lightdm-greeter-session
E  guest-wrapper=/usr/lib/lightdm/lightdm-guest-session
G  greeter-session=unity-greeter
H  xserver-command=X -core
I  autologin-user=visitor

   [LightDM]
C  backup-logs=false

Sources:
A  /usr/share/lightdm/lightdm.conf.d/45-unity8.conf
B  /usr/share/lightdm/lightdm.conf.d/50-disable-guest.conf
C  /usr/share/lightdm/lightdm.conf.d/50-disable-log-backup.conf
D  /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
E  /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
F  /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf
G  /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf
H  /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
I  /etc/lightdm/lightdm.conf

```

RobGoss, did you change the default login settings?  If so, how?

---

### Post by again? on 2017-06-14
I doubt this will fix your original problem but you have set the "visitor" account to autologin.
You may want to disable that in your account settings.
If you need to do this from the console, I believe the file to edit is **/etc/lightdm/lightdm.conf**
You can use grep to check which file.
```
grep -r 'autologin' /usr/share/lightdm/lightdm.conf.d/ /etc/lightdm/
```

---

### Post by again? on 2017-06-15
Having another read and a look at 17.04 it appears you have created an account to autologin.
If you enable an account to autologin you won't see the login greeter and will have to log out or choose your account from the top right as you described.
If you created the account and enabled autologin you can turn off autologin in the **system settings > Users** GUI.

The default guest account doesn't show in  **system settings > Users** whether enabled or not so not sure what you deleted.
The guest account is disabled with the config file **/usr/share/lightdm/lightdm.conf.d/50-disable-guest.conf** as shown in your **lightdm --show-config** output.
The guest account is disabled because of this [**BUG**]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1663157").
To enable the default guest account you would have to edit a config file.

You can restore the config files in /usr/share/lightdm/lightdm.conf.d/ by reinstalling lightdm.
```
sudo apt install --reinstall lightdm
```

Then also check you haven't created a config in /etc/lightdm which allows autologin.
```
grep -r autologin /etc/lightdm
```

---

### Post by ktat on 2017-06-15
Thank you Guber2, I've switched off the auto login option and now both accounts are listed at the login screen.

I still don't know why there was a problem with the guest account that I created - but it no longer matters.

:)

---

### Post by again? on 2017-06-15
No problem. Sometimes it's a bit hard to understand what's going on.
I wasn't aware that the guest account had been disabled.
The default guest account can easily be enabled if required.
The [**bug**]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1663157") is only exposed to someone physically logging on to your guest account.
On a home computer where you know who's logging in, they would need to be malicious
and have the know how to take advantage of the bug.

To enable the guest account you can create a a config file in **/etc/lightdm** to override default settings.
Terminal command to create file:
```
echo -e "[Seat:*]\nallow-guest=true" | sudo tee /etc/lightdm/lightdm.conf
```

Then restart lightdm. This will log you out so save and close all appliications.
```
sudo service lightdm restart
```

To disable guest account again, remove the **/etc/lightdm/lightdm.conf** file you created.
```
sudo rm -i /etc/lightdm/lightdm.conf
```

---

### Post by Gstrazds on 2018-02-06
Feature Request; I was also locked out of my user account - booting into the guest account.

I was informed via these pages that I had to boot into the guest account session; then in the top right click on switch user account!

Adding a switch user account setting in the top right of the greeting screen and or in the guest dialog login box would be intuitive and productive.

Thanks, Glenn Strazds

---

