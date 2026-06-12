---
title: "Login Issue"
date: 2013-12-10
forum: General Help
---

### Post by codybricesands on 2013-12-10
Hello, I recently ran into an issue with Ubuntu were i'm not able to login to my account! Only as a guest i can login. I know i haven't forgot my password because i've been using it for years or so now. And what happens is when i attempt to login, it looks like it's about to login and then it just goes back to the login screen. When i purposly used the wrong password to see what happens, it says wrong password like normal. So i know i'm using the right password. I never really installed much on my Ubuntu machine just java so far. But if there is a way to use sudo commands while loged in as a guest could i fix it from there? I'm currently running Ubuntu 13.10. But a mostly fresh install.

---

### Post by jdeca57 on 2013-12-10
Just read this: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by codybricesands on 2013-12-10
Okay, I will give this a try.

---

### Post by Impavidus on 2013-12-10
That's about missing passwords, which is not your problem. Can you login from the console (ctrl-alt-F1)? Check the ownership of ~/.ICEauthority and ~/.Xauthority. They should be owned by you and have permissions -rw-------. Sometimes they get root-owned, usually as a result of not being careful when running GUI programs as root. This may cause the graphical login to fail.

---

### Post by drmrgd on 2013-12-10
> **Impavidus said:**
> That's about missing passwords, which is not your problem. Can you login from the console (ctrl-alt-F1)? Check the ownership of ~/.ICEauthority and ~/.Xauthority. They should be owned by you and have permissions -rw-------. Sometimes they get root-owned, usually as a result of not being careful when running GUI programs as root. This may cause the graphical login to fail.

+1 to this!  

It's definitely something other than your password, and those two files are the first culprits, especially since you can log in with a guest account (I've seen a similar problem on my own computer with video drivers, but that's a user-wide problem).

---

### Post by codybricesands on 2013-12-10
Alright i fixed it! So it wasn't a matter of wrong password but knowing about the recovery mode really helped me fix this.

---

### Post by Doug_Strain on 2014-08-12
Hi!

I'm having the same prob as the OP (that is, I can't login) and got so excited when I saw your response!  But, alas ...

~/.ICEauthority and ~/.Xauthority are owned and perm'ed by me, the user. 

 Two files in ~ are owned by root; ~/.cache/dconf and ~/.dbus/session-bus (that filename looks a little funny but it's close and I'm typing this from my windows boot).

Also, I'd set up the (only) account to skip logging in, if that helps.

Any suggestions?

Thanks
Doug

---

### Post by Impavidus on 2014-08-13
Those files (or directories) can cause problem for the graphical login too if they are owned by root. No file in your ~ directory should be owned by root. I don't know about ~/.cache/dconf as it is not present on my system, but maybe you have 12.04. Some things changed. ~/.dbus/session-bus is present here. It and it's contents must be owned by you and have read and write permission for your and execute permission on the directory.

---

### Post by Doug_Strain on 2014-08-13
Thanks Impavidus!

It was ~/.dbus/session-bus.  Don't know (yet) what the "bus" part is but the "session" part should have been a clue.

Everything's back to normal and I won't "sudo nautilus" anymore.

Thanks again
Doug

---

### Post by luxee on 2014-08-14
Hi,

I am having issue to log in my account,it has started, when I thought I dont remember my password, than I could change it.When I typed in there was not an error message, but still the same login screen come up.
I have no idea what to do, I' ve read trough different threads, but could not find the solution yet.
Any help would be appreciated.

Thanks.

---

### Post by Impavidus on 2014-08-14
Exactly as explained in post #4 and #8. If you don't understand, please start a new thread. This one has been marked solved and won't attract much attention. Note that your problem might not be exactly the same as that of the original post.

---

### Post by Bashing-om on 2014-08-14
luxee; Hi !

ninja'd by impavidus !

Anyway, posting too same same advise.

Try the directive from post #2.

If there continues a problem, you are well advised to start your own thread with the advisement to the forum of the results of:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
In order to gain a broader view of your particular situation.

[INDENT][INDENT]help, though
[INDENT][INDENT][INDENT][INDENT]is what we do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

