---
title: "Bluetooth set up - Unable to do it"
date: 2014-01-25
forum: General Help
---

### Post by viriatovigo on 2014-01-25
Good morning/afternoon/evening everybody
 

 I open System Settings [FONT=Liberation Serif]>[/FONT][FONT=Liberation Serif] Bluetooth and the Bluetooth window shows greyed up, I can't do anything,[/FONT]
 

 [FONT=Liberation Serif]Also it shows &#8220;Bluetooth: OFF&#8221; and &#8220;visibility: OFF&#8221;, but, as I said, I can't change it.[/FONT]
 

 [FONT=Liberation Serif]I am trying to set up a wireless keyboard and a wireless mouse. The mouse was not problem because it did start to work straight way, but the keyboard needs to be paired and insert a code and I can't do it because I can't search for new gadgets since the Bluetooth is OFF and greyed.[/FONT]
 

 [FONT=Liberation Serif]How can I resolve the issue, please? Thank you in advance for your kindness.[/FONT]

 

 [FONT=Liberation Serif]Tino[/FONT]

---

### Post by Linuxisfast on 2014-01-25
[HTML]sudo rfkill unblock all[/HTML]

Try it and see if it enables bluetooth.

---

### Post by ClientAlive on 2014-01-25
Stupid question : Are you set up as an administrative user?

---

### Post by viriatovigo on 2014-01-25
Hi ClientAlive and Linuxfast, thank you for your answer.

ClientAlive: Yes

Linuxisfast: I can't believe this... I have 38 different passwords, I never repeat the same in two places, and now I can't remember which one is for the Terminal. I did try most of then and didn't work and I can't find where the hell I put the piece of paper with all of them.

Sorry, gime some minutes. Ta.

---

### Post by viriatovigo on 2014-01-25
Sorry Linuxisfast

I can't find it... I got fed up and I went to My Account, Settings, Edit email and password, I did chage the password but the Terminal still doesn't take it.

This "thing" of the Terminal is why I don't use Ubuntu for business but Apple Maverick. No way that in the middle of an interpretation on Skype and a problem arises I am going to tell the Agency "Sorry, tell the customer to wait a couple of hours" and then going into this Forum, find the solution and the solution may be to write a string of sudo commands larger than the history of my life.

When Linux do start to make things easier and customer friendly I will use it for business because is the safest and fastest OS in the market, but at the moment is not customer friendly at all.

Let's going to have a rest and I need to find out how to resolve the issue of the password.

Once more, thank you so much for your help. It is appreciated. See you soon (I hope...).

Tino

---

### Post by Linuxisfast on 2014-01-25
You don't really need the terminal except in rarest of cases like this, remembering password is must for any OS.

---

### Post by dragonfly41 on 2014-01-25
> 
I have 38 different passwords, I never repeat the same in two places, and now I can't remember which one is for the Terminal.


I suggest installing KeePass from Ubuntu Software Centre to help with multiple password management.

---

### Post by viriatovigo on 2014-01-25
Hi Linuxisfast

I am back... after a lot of swearing...

I am sorry to tell you that each time that I did ask for help, exept 4 times, every single time I had to write something in the Terminal and have been a lot of times, and once up to 23 scripts but with up to 5 scripts several times. This time I am back since 1 year ago; up 2 years ago I was in Linux since Red Hat (that was a real, real nightmare. Still I am keeping the book and the CD as a matter of curiosity), so 2 years ago, after discovering Apple Snow Leopard (nowadays upgraded to Maverick), I've got fed up and I did uninstall Ubuntu. So I am having a new go.

I did find out the password in a word doc in the Lenovo Ideacentre  PC desktop with Windows 8 (that I use to to teach to jobseekers to use PCs as a voluntary workfor the UK Employment Department), but now, after inputing the password, it does nothing.

This is what happens:

constante@constante-X50V3:~$ sudo rfkill unblock all
[sudo] password for constante: 
constante@constante-X50V3:~$ 
constante@constante-X50V3:~$ sudo rfkill unblock all
constante@constante-X50V3:~$ 

What I am doing wrong this time?

---

### Post by viriatovigo on 2014-01-25
Sorry dragonfly41, I didn't mean to be rude, I do apologize.

Thank you for the tip. I'll have a go (whe I do cool down...).

What it does exactly?

---

### Post by viriatovigo on 2014-01-25
Hi dragonfly41

I was looking at it. It is a very good idea, thank you.

It is called KeePassX, is that one?

There is already a KeePass2 but it seems not rated as good as KeePassX. I'll go for it just now. Thank you.

There is something similar in Apple Maverick but, except in Linus, nothing is free and no cheap precisely.

Take care.

Tino

---

