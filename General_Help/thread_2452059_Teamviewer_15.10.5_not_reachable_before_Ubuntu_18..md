---
title: "Teamviewer 15.10.5 not reachable before Ubuntu 18.04's local login."
date: 2020-10-15
forum: General Help
---

### Post by thosecars822 on 2020-10-15
Hello

I have set up Teamviewer as "Start TeamViewer with system".
The thing is this computer does not show up as connected in Teamviewer until I login in locally in Ubuntu.

Is there anything that can be done so that someone could connect and login remotely on this computer by means of Teamviewer before anyone logs in locally in Ubuntu?

Thanks

---

### Post by CelticWarrior on 2020-10-15
[https://community.teamviewer.com/t5/Linux-EN/Teamviewer-13-not-connecting-in-Ubuntu-18-04-Login-Screen/td-p/35342](https://community.teamviewer.com/t5/Linux-EN/Teamviewer-13-not-connecting-in-Ubuntu-18-04-Login-Screen/td-p/35342)

---

### Post by TheFu on 2020-10-15
Doesn't this seem like a really bad idea to anyone else?

[LIST]
[*][https://www.bbc.com/news/technology-36459015](https://www.bbc.com/news/technology-36459015) - 2016
[*][https://www.makeuseof.com/tag/teamviewer-hack-everything-need-know/](https://www.makeuseof.com/tag/teamviewer-hack-everything-need-know/) - 2016
[*][https://thehackernews.com/2017/12/teamviewer-hacking-tool.html](https://thehackernews.com/2017/12/teamviewer-hacking-tool.html) - 2017
[/LIST]

I never understand using these things when we have real VPNs or ssh using keys for authentication. **x2go** is pretty easy to setup for a remote desktop and it isn't like ssh isn't all we need 99% of the time.

---

### Post by thosecars822 on 2020-10-16
The problem with the solution linked by CelticWarrior is that my Ubuntu 18.04 has Lightdm instead of Gnome as display manager and it does not even have a folder called /etc/gdm3

[https://community.teamviewer.com/t5/Linux-EN/Teamviewer-11-12-Beta-No-access-to-Linux-host-before-login/m-p/104623#M4550](https://community.teamviewer.com/t5/Linux-EN/Teamviewer-11-12-Beta-No-access-to-Linux-host-before-login/m-p/104623#M4550)

Do you have any idea about how to proceed bearing this in mind?

Thanks

---

### Post by scorp123 on 2020-10-16
> **thosecars822 said:**
>  Do you have any idea about how to proceed bearing this in mind?


Install "gdm3" and make sure it will be the default login manager. Current iterations of Teamviewer do not work well with current versions of "lightdm", there's no way around it. Also make sure "wayland" is turned off.

And as for security: Please make sure you have a strong Teamviewer password and have 2-Factor Authentication active. People getting their system hacked because they left Teamviewer running all the time + they had a weak password is not unheard of.

---

### Post by thosecars822 on 2020-10-16
I just tried the following: installing dgm3 and uncommenting the following line

WaylandEnable=false
of the file
/etc/gdm3/custom.conf

Anyway it did not work yet for some reason.

I also have another old laptop with Teamviewer. In this second one there is no problem to access Ubuntu 18-04's login screen even with lightdm.

It sounds weird.

I do not know what I can do in the laptop that does not allow to access its login screen from Teamviewer even with the mentioned gdm3 and custom.conf file. May be just I could disable the login screen so that the computer boots up straight without the need to log in. I do not know anything else that might work.

---

### Post by scorp123 on 2020-10-16
> **thosecars822 said:**
>  I do not know what I can do in the laptop that does not allow to access its login screen from Teamviewer even with the mentioned gdm3 and custom.conf file. 

Other question: Does it absolutely have to be Teamviewer? There are various alternatives that may or may not work better.

For a Teamviewer-like experience you could try **AnyDesk**. It was created by disgruntled former Teamviewer engineers, so it has basically the same look + feel and works the same way. Advantage over Teamviewer: better performance and better cross-version compatibility, better cross-platform support. And if you intend to buy a license (e.g. because you are using this in your company) they also cost less.

But further up several free + open source solutions were mentioned already and maybe you should look at those options too: VPN, SSH, X2go, FreeNX ... 

I used to own a professional license for Teamviewer 11 ... but frankly I find the software is no longer as good as it used to be and I have given up on it since. The free options (OpenVPN + SSH) work a lot better for me.

---

