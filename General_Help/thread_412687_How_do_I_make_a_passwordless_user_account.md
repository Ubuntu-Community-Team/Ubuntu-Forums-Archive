---
title: "How do I make a passwordless user account?"
date: 2007-04-18
forum: General Help
---

### Post by endo on 2007-04-18
Hi all!

I have the following problem:

So far I haven't been able to create a user account with no (/a blank) password. Is it possible and how?

I have several user accounts and I want to create another that does not login automatically, but rather requires no password to log in after typing its name.

I'm not sure whether I've managed to make it clear... I want to be able to type the name of the account at the login prompt/screen and then hit the Return key and then login without having to type ANY password.

Is there a way to create such an account?

I've tried several times to create one by just leaving the password field empty, but I get a message that this field cannot be left empty and then no account is created.

Some help would be very much appreciated.

---

### Post by Oki on 2007-04-18
I don&#8217;t think it&#8217;s possible. 

But you could perhaps make a login screen that has the password typed on it? Like &#8220;Password for guest are &#8220;guest&#8221;.

---

### Post by akshaysrinivasan on 2007-04-18
It must be possible ,i've heard distributions like Madriva and Linspire would allow users without passwords ,sadly though i am not sure how to.

---

### Post by endo on 2007-04-18
Well, I managed to remove the password using this command:
passwd -d username

and outside GDM everything is OK, no password is required for login anymore... but GDM still refuses to let me in with no password and still requires one, no matter that it has already been deleted :(

---

### Post by aidanr on 2007-04-18
edit:// nevermind i read the op wrong

---

### Post by endo on 2007-04-18
> **aidanr said:**
> edit:// nevermind i read the op wrong

ok, nevermind

Any other suggestions?

---

### Post by aidanr on 2007-04-18
found this
[http://mirror.hamakor.org.il/archives/linux-il/05-2004/10149.html](http://mirror.hamakor.org.il/archives/linux-il/05-2004/10149.html)

seems pretty complicated though, i wonder why gdm doesn't allow no password:-k

more reading here
[http://bugzilla.gnome.org/show_bug.cgi?id=414862](http://bugzilla.gnome.org/show_bug.cgi?id=414862)

---

### Post by endo on 2007-04-18
> **aidanr said:**
> found this
[http://mirror.hamakor.org.il/archives/linux-il/05-2004/10149.html](http://mirror.hamakor.org.il/archives/linux-il/05-2004/10149.html)

seems pretty complicated though, i wonder why gdm doesn't allow no password:-k

more reading here
[http://bugzilla.gnome.org/show_bug.cgi?id=414862](http://bugzilla.gnome.org/show_bug.cgi?id=414862)

Thanx a lot! :)

I've already seen this sophisticated approach but I was wondering if there was a simpler way to do it...
Seems that GDM is more stubborn than I thought :)

---

### Post by aysiu on 2007-07-30
Try this. It's a very simple way to get a passwordless user.
[HowTo: Create a Passwordless / Guest Login (Simple Method)](http://ubuntuforums.org/showthread.php?t=513820)

---

