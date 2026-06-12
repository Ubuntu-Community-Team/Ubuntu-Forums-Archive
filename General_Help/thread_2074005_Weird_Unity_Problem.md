---
title: "Weird Unity Problem"
date: 2012-10-20
forum: General Help
---

### Post by NM5TF on 2012-10-20
I am having a weird problem with Unity...if I log in as Guest then Unity is
full 3D & I can change the size of the launcher icons....

If I log in as myself then Unity is locked as 2D & I can't change the launcher icons...

If I look at sysinfo or details the graphics info are both the same no matter if logged in as myself or Guest....

```

lspci | grep VGA

``` 
gave these results:

00:0d.0 VGA compatible controller: NVIDIA Corporation C61 [GeForce 6150SE nForce 430] (rev a2)

I am using the latest Nvidia driver I believe..
Nvidia Unix 86_64 Kernel 304.43

Anyone else having this problem??

Can I force Unity to go to 3D mode, or somehow "purge" the Nvidia driver
& reinstall it??

Why should the Guest log in be any different than my normal log in???

TIA, 

Tommy

---

### Post by NM5TF on 2012-10-21
Looks like 75 people viewed the thread, but no one could solve it:confused:

I used a work-around by creating a new account, then transferred all
my files & settings to it....it now behaves correctly:P

I will mark the thread SOLVED tho it isn't really:(

---

### Post by deadflowr on 2012-10-21
When you are first logging in(before you enter your password and hit enter), check the cog(Ubuntu logo inside the login box(top right corner) and make sure the selected Desktop Environment is Ubuntu and not Ubuntu2d. Then login and see if that helps.

---

### Post by NM5TF on 2012-10-23
> **deadflowr said:**
> When you are first logging in(before you enter your password and hit enter), check the cog(Ubuntu logo inside the login box(top right corner) and make sure the selected Desktop Environment is Ubuntu and not Ubuntu2d. Then login and see if that helps.

I did try that, but no change...still same problem....

I will just use the 2nd profile I created as that works like it
should...and besides, I have already transferred all my files to
it anyway....

thanx for the reply just the same...

Tommy

---

