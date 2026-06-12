---
title: "crap. I don't even know what I did"
date: 2008-06-12
forum: General Help
---

### Post by zyxyellowxyz on 2008-06-12
I apparently did SOMETHING wrong
And I'm not exactly sure what it was

I get the following error(s) when I try to log into my main account on Kubuntu (yes, I have 2 log ins, and now I am very happy that I do)

```
The following installation problem was detected while trying to start KDE:

No write access to '/home/susan/.ICEauthority'.

KDE unable to start.
```


and after I sadly click okay, I get this one:


```
could not start ksmserver. check your installation
```


do I need to change the permissions on that folder/file? and I think the answer is yes... how would I do that? I know I can in terminal, but I have never memorized how to do that.

---

### Post by daleus on 2008-06-12
I once had this problem on Kubuntu years ago, I just went into a terminal (pushed ctrl + alt + f1) and logged in, and just deleted that .ICEauthority, worked then, it was obviously remade or something.

Good luck

---

### Post by avtolle on 2008-06-12
@OP: Take a look at this, and see if you might have done something akin to what aysiu describes therein, as the symptoms seem similar:
[http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)
Provided to (hopefully) allow you to avoid the same error *in futuro*.

---

### Post by wootah on 2008-06-12
> **zyxyellowxyz said:**
> I apparently did SOMETHING wrong
And I'm not exactly sure what it was

I get the following error(s) when I try to log into my main account on Kubuntu (yes, I have 2 log ins, and now I am very happy that I do)

```
The following installation problem was detected while trying to start KDE:

No write access to '/home/susan/.ICEauthority'.

KDE unable to start.
```and after I sadly click okay, I get this one:


```
could not start ksmserver. check your installation
```do I need to change the permissions on that folder/file? and I think the answer is yes... how would I do that? I know I can in terminal, but I have never memorized how to do that.

CTRL-ALT-F1
<login with username susan>
ls -lsad .ICEauthority

Should give you the following:
**tripp**@eclipse-desktop:~$ ls -lsad .ICEauthority
32 -rw------- 1 **tripp tripp **32369 Jun 10 23:19 .ICEauthority
Notice how all the bold matches? That means I own that file along with my group.

If yours does not match, you can do the following:
```
sudo chown susan:susan .ICEauthority
```

This changes the ownership of that file to the username and group **susan**. Reboot and try that :)

PS: If this works, that means that root probably owned that file before. Perhaps you did a gksudo or a sudo on something which caused that file to be created with root privs.

---

### Post by zyxyellowxyz on 2008-06-12
I actually changed the permissions in my second login and it worked.

Could it be the fact that I tried to log in with KDE 4? (My default is KDE 3.5.9)

Or the fact that I started it up in gnome (by acciedent) and instead of logging out and logging back in with KDE 3.5.9, I went to termnial and typed "sudo kcontrol" and changed the password on my second login? 

\at that point I couldn't get into my second login, and after I did that I COULD log into my second login but not my main. I thought it was because the passwords were the same, so I logged into my second account and did the proper way to sudo into kcontrol (kdesudo) and changed the password on both accounts so they wouldn't be the same. Nothing worked until I was able to I changed the file in question to where it was readable by everyone. I didn't want to delete it because I was afraid it was something very important.

Could it be both or just one of the things that caused the problem?

(I believe that the version of KDE 4 I have is still connected to 7.10 while I am running 8.04. I honestly have not tried to login with KDE 4 since the update. I also have a partion on my hard drive that JUST has one user. Its odd and I don't know why its there.)

---

### Post by avtolle on 2008-06-12
It might well have been all or any one of the things listed, but I'm leaning towards sudo kcontrol as the reason. :-)

---

### Post by wootah on 2008-06-12
> **avtolle said:**
> It might well have been all or any one of the things listed, but I'm leaning towards sudo kcontrol as the reason. :-)
I'm going to have to second on the *sudo kcontrol* :)

---

### Post by zyxyellowxyz on 2008-06-12
it makes a lot of since (I read the article that avtolle posted the link to, and it warns about doing what I did).

I fairly recently learned that using sudo to use root for a kde application is not right, but using kdesudo is the right way.

I will make a good and hard mental note about this because I DO NOT want to have this happen to me again.

---

### Post by wootah on 2008-06-12
> **zyxyellowxyz said:**
> it makes a lot of since (I read the article that avtolle posted the link to, and it warns about doing what I did).

I fairly recently learned that using sudo to use root for a kde application is not right, but using kdesudo is the right way.

I will make a good and hard mental note about this because I DO NOT want to have this happen to me again.

So everything is good now ?

---

