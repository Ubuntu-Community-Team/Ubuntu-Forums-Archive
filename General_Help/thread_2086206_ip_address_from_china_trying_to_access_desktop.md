---
title: "ip address from china trying to access desktop"
date: 2012-11-20
forum: General Help
---

### Post by bart1963 on 2012-11-20
Hi all love ubuntu but have 2 irritations. 1st is when i turn on laptop it boots ok but then says network disabled, I have to restart laptop it then connects automatically and works fine. 2nd is more serious i keep getting ip address 81.9.81.126 trying to access desktop i click deny. But have had this several time over last few months. How can i disable remote desktop and ssh would like to secure ubuntu and stop these attacks.
Hope someone can help.
Bart1963  :P

---

### Post by SlugSlug on 2012-11-20
load up 

```
vino-preferences
```and disable it.

You only need to remove ssh if you've installed it. If you use it then I'd suggest you install denyhosts which will block IP address if they attempt to login,

You should also have a strong password and set up keys

---

### Post by prshah on 2012-11-20
> **bart1963 said:**
> 2nd is more serious i keep getting ip address 81.9.81.126 trying to access desktop i click deny

That's a russian federation ip address: See [http://www.ip2location.com/81.9.81.126](http://www.ip2location.com/81.9.81.126)

It's from ISP (?) ZAO ELTEL; I guess you could email them your relevant log contents, with time, and complain.

You can also disallow remote access in settings->Desktop Sharing (a friendlier name for vino-preferences as recommended earlier, both are the same thing).

---

### Post by bart1963 on 2012-11-20
> **prshah said:**
> That's a russian federation ip address: See [http://www.ip2location.com/81.9.81.126](http://www.ip2location.com/81.9.81.126)

It's from ISP (?) ZAO ELTEL; I guess you could email them your relevant log contents, with time, and complain.

You can also disallow remote access in settings->Desktop Sharing (a friendlier name for vino-preferences as recommended earlier, both are the same thing).

Thank you all for you help have disabled sharing will get deny host as suggested.

---

### Post by coldraven on 2012-11-20
Check that your router has not got ports open.
Go to SheildsUp for a scan
[https://www.grc.com](https://www.grc.com)

---

### Post by bart1963 on 2012-11-22
> **coldraven said:**
> Check that your router has not got ports open.
Go to SheildsUp for a scan
[https://www.grc.com](https://www.grc.com) still got people trying to view my desktop i thought ubuntu was more secure than windows if i cant lock this down will have to go back to using windows don’t want to so any help would be appreciated.
thanks 
bart.:confused:

---

### Post by bart1963 on 2012-11-22
> **bart1963 said:**
> still got people trying to view my desktop i thought ubuntu was more secure than windows if i cant lock this down will have to go back to using windows don’t want to so any help would be appreciated.
thanks 
bart.:confused: now getting vps-7408.united-hoster.de and uhs553.united-hoster.de
trying to access desktop PLEASE HELP..

---

### Post by lisati on 2012-11-22
> **prshah said:**
> That's a russian federation ip address: See [http://www.ip2location.com/81.9.81.126](http://www.ip2location.com/81.9.81.126)

It's from ISP (?) ZAO ELTEL; I guess you could email them your relevant log contents, with time, and complain.

You can also disallow remote access in settings->Desktop Sharing (a friendlier name for vino-preferences as recommended earlier, both are the same thing).

I also found something nasty: [http://cbl.abuseat.org/lookup.cgi?ip=81.9.81.126](http://cbl.abuseat.org/lookup.cgi?ip=81.9.81.126)

What did the shields-up page tell you?

If your router has a firewall option, I'd suggest looking into activating it.

---

