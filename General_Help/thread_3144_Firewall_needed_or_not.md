---
title: "Firewall needed or not"
date: 2004-11-03
forum: General Help
---

### Post by samgnu on 2004-11-03
I am confused as to whether and when I need a firewall if I have a dialup internet connection on a single computer. Ubuntu FAQ says I don't need one this forum says I need one. Also if I configure postfix to send mail with mutt as my email client should I have one?

---

### Post by az on 2004-11-03
I wouldn't even come close to thinking about being worried that someone will:
1- ever notice you are on the internet.
2- Find a bug in postfix that will allow them to take over your computer and use that information to go out and buy themselves a car - bankrupting you and putting your six tollders out into the street.

Don't worry.

---

### Post by jdodson on 2004-11-03
ya i agree i wouldnt be too worried about it, specially on dialup.

---

### Post by TekMate on 2004-11-03
I agree with the others on dialup it's unlikely someone will notice you are online and try to hack your system it's just not a good use of resources when you can attack thousands of Windows users on broadband with no protection.

---

### Post by Joeb on 2004-11-03
[QUOTE=samgnu]I am confused as to whether and when I need a firewall if I have a dialup internet connection on a single computer. Ubuntu FAQ says I don't need one this forum says I need one. Also if I configure postfix to send mail with mutt as my email client should I have one?[/QUOTE]

Although you had some tongue in cheek posts in response to your question, the short answer is that with dial-up you are significantly less likely to have a problem because you just aren't on long enough or consistantly enough for some to exploit your connection.  Plus with a lot of dial-ups, your IP address is different every time.  Besides that, the base install of Ubuntu doesn't have any ports open that would make you vulnerable.

Installing postfix changes that.  You now will have a port open that could be exploited, but then since you are still dial-up, the risk is minimal (unless you are going to leave your system online  for long periods of time).

Chances are your risk will be low, but if you are concerned, you could always install Firestarter for peace of mind.  It's not the hard to set up and would give you that extra peace of mind.

Joeb

---

### Post by samgnu on 2004-11-04
Many Thanks for these replies.

---

### Post by FLeiXiuS on 2004-11-04
Your welcome, as I didn't post earlier I am doing so now.  I would reccomend a firewall no matter what you run.   It will significantly decrease the icmp's which may be scattered on your network at times.  

Also, its fun to block stuff :-P

---

### Post by Burgundavia on 2004-11-04
I would second the firewall needed comment. As a (Windows) sysadmin, no amount of security is enough for me. However, that being said, you have several advantages others dont

1- no constant internet connection
2 - Linux (whether it is more secure is a debate for another time, but obscurity still helps you)
3 - Postfix is pretty mature and fairly well developed from a security point of view

All in all, download firestarter and set up your firewall.

Corey

---

