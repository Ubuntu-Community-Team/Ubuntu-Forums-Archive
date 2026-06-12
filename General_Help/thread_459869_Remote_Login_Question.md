---
title: "Remote Login Question"
date: 2007-05-31
forum: General Help
---

### Post by xenoix on 2007-05-31
Basically, I am setting up a company. It is small. I have my servers running Kubuntu feisty fawn.

My girlfriends laptop is running Windows XP Home Edition. She will be working for us,

Is the following possible and if so, what do i need installed to do it:

> She logins into the server remotley (Not VNC)
> She logins in with a specific user account
> She is then given basically a GUI interface and her own account which she can then use.
> Her login and logout hours are logged and all work is saved onto the server. (She can also upload stuff from her machine)

I know FTP would probably be best, but I need a good way to monitor her login and activity for pay purposes ($$ per hour) etc.

Thank you for any help,


Brendan

---

### Post by thelinuxguy on 2007-05-31
As far as the remote login from Windows goes, XMing could do the trick. But it is irritating sometimes...such as Alt+TAB cycles through the windows on the XP machine and not on the remote machine which you are logged into. I can't say if there is a setting somewhere to change that.

When the remote user logs in using her username, as long as she is logged in, she will appear in the list provided by the command 'w' alongwith the login time. But I can't say where the time is recorded so that you could retrieve it later. Maybe some log file. You will need some more info on that.

Nevertheless, XMing is a good place to start. Take a look here: [http://freedesktop.org/wiki/Xming](http://freedesktop.org/wiki/Xming)
Also take a look at the link in my sig.

Regards.

---

### Post by xenoix on 2007-05-31
I think that sounds like what I want.

How would I enable/install it for Kubuntu (KDE) because i know it wont be using gdm.

Regards,
Brendan

P.S
> 
Step 2: Configure Remote access options
System -> Administration -> Remote
Change any options that you want. Default settings will work fine.


Whats the equivlent of that in KDE?

---

### Post by thelinuxguy on 2007-05-31
> **xenoix said:**
> Whats the equivlent of that in KDE?

I missed that you are using KDE on your servers. I don't have a working KDE install. [COLOR="Red"]So someone using KDE do pitch in.[/COLOR]

Default settings in that dialog (System >> Administration >> Remote) work fine. So that shouldn't be a problem. But you need to figure out the equivalent of gdm.conf. I think, as mentioned at [https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/22218](https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/22218), it is /etc/kdm/kdm.conf. There should be an XDMCP section in that file.

Let me know if it works.

---

### Post by thelinuxguy on 2007-06-09
I just came across this howto with a section on enabling XDMCP on KDE.
[http://ubuntuforums.org/showthread.php?t=259448](http://ubuntuforums.org/showthread.php?t=259448)

---

