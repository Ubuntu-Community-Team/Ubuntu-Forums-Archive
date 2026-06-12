---
title: "Need Emergency Help!"
date: 2008-04-23
forum: General Help
---

### Post by Svaler on 2008-04-23
Hello guys im writting you for 1st time.
I need some help.
I don't know is it up to Compiz ive installed,but emidiatly after him ive rebooted pc and it just went mad!
So what happend?
I run my Pc and on boot i get message:
The greeter applycation appears to be crushing.Attempting to use different one.
And then after couple of times trying automaitcly i get this message:
The display server has been shut down about 6 times in the last 90 seconds.It is likely that something bad is going on.Waiting for 2 minutes before trying again on display :O

And then ive come here to find the answer whats going on with my Pc and i tho ive found one answer and used it.
It was going like this:
When it comes to boot i press alt+f2 and type:
sudo dpkq-reconfigure xserver-xorg and then i choose "VESA"
and for others ive just manually next and ok...

And now when i boot my Pc its just some splashing cursor and it says that my pc is going low on grapshics...ive changed it on options its provides and still nothing...it just crashes non-stop...

Ive made quite mess here right? :)
If is there any solutions...please give them...
Its rly emergency becouse i need to use my pc today at noon becouse a lot of work things inside.

---

### Post by warbread on 2008-04-24
Go to Administration>Restricted Drivers and uncheck your drivers.  Then recheck the box.  Restart.

---

