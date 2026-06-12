---
title: "~/www/meetings? Why is it showing up?"
date: 2015-12-12
forum: General Help
---

### Post by moebob24 on 2015-12-12
This keeps showing up in my home directory on both my laptop and my virtual server. Even after I delete it.

I'm really curious about what is creating this.

---

### Post by yancek on 2015-12-13
On a standard Linux install, the only place one would expect to see a directory named "www" would be under the /var (or sometimes srv) directtory.  What does the command below output:

```
ls -ld ~/www
```

---

### Post by moebob24 on 2015-12-13
> **yancek said:**
> On a standard Linux install, the only place one would expect to see a directory named "www" would be under the /var (or sometimes srv) directtory.  What does the command below output:

```
ls -ld ~/www
```


From my laptop
```

drwxrwxr-x 3 user user 4096 Dec 10 21:11 /home/user/www/

```

From my VPS
```

drwxrwxr-x 3 user user 4096 Dec  9 04:55 /home/user/www/

```
Where 'user' is my username.


I'm aware of my*** /var/www/ ***path as thats where apache is configured to put my web assets.

---

### Post by davidmanuel1993 on 2016-05-21
In my case this folder was created by [Sopel IRC Bot]("https://www.google.pt/url?sa=t&rct=j&q=&esrc=s&source=web&cd=4&cad=rja&uact=8&ved=0ahUKEwjI6dDd6evMAhUJuhQKHUWyCbAQFgg3MAM&url=https%3A%2F%2Fsopel.chat%2F&usg=AFQjCNFh7iSC8fQysGXKAsNZyVyMSBgsTg&sig2=IihJYg-7hZfZaWYVAbcdzQ").

---

### Post by moebob24 on 2016-05-26
That must be it. I run that... haha

Thank you!

Funny enough I just happened to come back and check on this thread today as a friend of mine was asking.

---

### Post by DuckHook on 2016-05-26
*Please mark thread **solved** using *Thread Tools* in the top toolbar for the benefit of others searching for solutions*.

---

