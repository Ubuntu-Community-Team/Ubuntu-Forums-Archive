---
title: "gvfs backend admin://?"
date: 2017-11-12
forum: General Help
---

### Post by again? on 2017-11-12
Just came across the gvfs backend **admin://**
Is this what should be used to open files/directories as root.
eg
```
gedit admin:///etc/fstab
nautilus admin:///etc/
```

Would value a simple explanation or link to, what you should be using in 17.04 going forward.

---

### Post by vasa1 on 2017-11-12
jbicha had a brief post on it the other day: [https://ubuntuforums.org/showthread.php?t=2376888&p=13710239#post13710239](https://ubuntuforums.org/showthread.php?t=2376888&p=13710239#post13710239)

[https://github.com/brunonova/nautilus-admin/issues/29](https://github.com/brunonova/nautilus-admin/issues/29)

You may or may not like these videos: 
[https://www.youtube.com/watch?v=o1jv8fD6f94](https://www.youtube.com/watch?v=o1jv8fD6f94)
[https://www.youtube.com/watch?v=COED3Xfw1k0](https://www.youtube.com/watch?v=COED3Xfw1k0)

---

### Post by again? on 2017-11-12
Doesn't allow renaming and deletion of files not owned by me.
Is admin:// meant to be a safer more secure way to edit root files?

---

### Post by jbicha on 2017-11-13
> **guber2 said:**
> Doesn't allow renaming and deletion of files not owned by me.

Could you file a bug for that?

> **guber2 said:**
> 
Is admin:// meant to be a safer more secure way to edit root files?

Yes, it's better to not try to run the entire app as root but just use elevated privileges for the specific actions needed. Also, sudo and gksu won't work to run apps in the default Ubuntu (on Wayland) session in 17.10+.

---

### Post by again? on 2017-11-13
> **jbicha said:**
> Could you file a bug for that?

Is it a bug though, or is it designed that way?

---

### Post by jbicha on 2017-11-13
> **guber2 said:**
> Is it a bug though, or is it designed that way?

You could file the bug and find out! :grin:

---

### Post by again? on 2017-11-13
> **jbicha said:**
> You could file the bug and find out! :grin:
True, but I always try the lazy route first. :cool:

---

### Post by mc4man on 2017-11-13
> **guber2 said:**
> Doesn't allow renaming and deletion of files not owned by me.
Is admin:// meant to be a safer more secure way to edit root files?
It has some limitations compared to prior or other methods/enviroments.

I haven't seen any concrete user examples of previous or others being unsafe or insecure, (other than in recent Gnome),  so I'd  describe as more "proper" or in the case of current Gnome, necessary.

---

### Post by again? on 2017-11-13
> **mc4man said:**
> It has some limitations compared to prior or other methods/enviroments.

I haven't seen any concrete user examples of previous or others being unsafe or insecure, (other than in recent Gnome),  so I'd  describe as more "proper" or in the case of current Gnome, necessary.
So if using sudo or gksu with the GUI isn't supported in Wayland and admin:// doesn't support deletion or renaming of files not owned by me,
am I right in saying, for some operations I previously used the File Browser to achieve, I will have to do through terminal?
I am just trying to find out where it's heading.

---

### Post by again? on 2017-12-11
Also if I open a file using **gedit admin:///path/to/file** and then close gedit, I am prompted for Authentication
every time I just open gedit because "admin:///path/to/file"  is in my recent files list.
Have to clear recent to stop authentication popup.

---

### Post by jbicha on 2017-12-11
guber2, what version of Ubuntu are you using? I thought that bug was present in 17.04 but fixed in 17.10.

---

### Post by again? on 2017-12-11
You're right testing in 17.10 it works ok.
Went back to using my 17.04 partition. 17.10 has too many bugs for me and keeps locking up.

---

### Post by e7appew on 2017-12-24
I wonder if any of you are experiencing this too. When I do gedit admin:///..., I always get prompted for my password twice. Only after the second time can I proceed with editing. I'm on 17.10, but the same thing happens on Debian Sid. Could it be a configuration problem?

---

### Post by vanadium on 2018-02-26
Came here indeed to see if others experienced this. Yes, I also need to provide my password twice when invoking gedit with an URI admin://.

---

### Post by again? on 2018-02-26
> **vanadium said:**
> Came here indeed to see if others experienced this. Yes, I also need to provide my password twice when invoking gedit with an URI admin://.

I see this in Xubuntu 17.10 using gedit.

---

### Post by Mark Phelps on 2018-05-13
The "admin://" feature may work with Nautilus, but I'm using Ubuntu Mate 18.04 and it does NOT work with either Gnome Commander or Double Commander.

It APPEARS to work, but does not actually open either file manager with root permissions.

Using sudo in a launcher DOES work, as it opens a terminal prompting for the password.

---

