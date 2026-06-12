---
title: "login to administrator account from non-administrator account through console"
date: 2008-04-21
forum: General Help
---

### Post by Pacifik on 2008-04-21
Dear friends,
I have few queries. Please help me out.

I have 2 users in my Ubuntu Gutsy system. The first user is **Pacifik** (which is the administrator, by default). And the second user is **Guest**. Only me can enter the admin a/c. Other members of my family login by Guest a/c. So almost all the time the system is in Guest login. When ever I need to do some administrator task I login by admin a/c. 

Many of the times I feel very difficulty when, say, some application is running in Guest a/c and simultaneously I need to do some administrator task I have to close that app(s) and then logout and login into admin a/c and do my work, and then login into Guest a/c. Previously I use to do quick user switch (switching between admin and Guest a/c). But this does not behave properly. Many desktop customization I loose when switching between a/c. Is there any easy way out.

Previously I use to have **opensuse** and **debian**, so I am very conversant with **su**. I can easily login to root by console and do the administrator work. But here, since Gutsy uses sudo, I cant login to **admin (Pacifik)** a/c from **Guest** a/c through console. _Basically I need only console to have my administrator work done._ Is there any way out. Please guide. Or if I am wrong anywhere, please correct me.

Thanks a lot.:guitar:

---

### Post by ryanhaigh on 2008-04-21
All you need to do is enter
```

su Pacifik

```
Then it will ask you for Pacifiks password then you will be logged in as Pacifik and can use sudo to do your admin work. Dont forget to use exit to terminate the session as Pacifik.

---

### Post by Pacifik on 2008-04-22
ohhh, it was so simple.
Thanks a lot.

---

