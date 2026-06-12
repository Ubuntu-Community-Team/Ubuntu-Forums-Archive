---
title: "Skip login but keep password"
date: 2015-04-09
forum: General Help
---

### Post by Thomas_Jansson on 2015-04-09
Hello!

This is my first time posting here, I read the PM I got from the bot so I hope I'm not doing anything horribly wrong!

So I have a laptop with Ubuntu on it. It has my main user account on it but I would like to skip the login on boot. This is because I'm not using the laptops screen. I have it plugged in to my main PC monitor and then I use Synergy(Synergy allows me to move my mouse over to another computer from my main computer as well as using my main computers keyboard on this secondary computer) to switch between my Ubuntu laptop and my PC when needed. I have set Synergy as a startup program so it connects upon login. But as of right now I have to pick up my laptop start it and log in before I can then close it and put it back. I would like to have this automated without removing my sudo password.

Is this even possible without extensive modification to the system?

Thanks!

---

### Post by Lars Noodén on 2015-04-09
Welcome.  In 14.04 Ubuntu you can set automatic login for an account by going to System Settings -> User Accounts -> {your account} -> Automatic Login -> On

Then when you start up, it should automatically go into your account.

---

### Post by Thomas_Jansson on 2015-04-09
> **Lars Noodén said:**
> Welcome.  In 14.04 Ubuntu you can set automatic login for an account by going to System Settings -> User Accounts -> {your account} -> Automatic Login -> On

Then when you start up, it should automatically go into your account.

Thanks, this worked great!

---

