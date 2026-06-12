---
title: "how to change machine name"
date: 2012-12-28
forum: General Help
---

### Post by howhy on 2012-12-28
while installing Ubuntu i didnt set the machine name so now its displaying howhy@howHy-System-Product-Name: in the terminal....

I am using Gnome desktop environment

---

### Post by irv on 2012-12-28
Try this link:
[http://handytutorial.com/change-hostname-or-computer-name-in-ubuntu-12-04-precise/]("http://handytutorial.com/change-hostname-or-computer-name-in-ubuntu-12-04-precise/")

---

### Post by audiomick on 2012-12-28
> **irv said:**
> Try this link:

But don't make a typing mistake in the new name like he did... ;)

I'm sure there is a way to do that with GUI tools, but I'm blowed if I can find it right now...

---

### Post by howhy on 2012-12-28
> **audiomick said:**
> But don't make a typing mistake in the new name like he did... ;)

I'm sure there is a way to do that with GUI tools, but I'm blowed if I can find it right now...
their wont be typing mistake becuase i copied and pasted

---

### Post by MG&amp;TL on 2012-12-28
> **audiomick said:**
> 
I'm sure there is a way to do that with GUI tools, but I'm blowed if I can find it right now...

I believe you start gnome-control-center as root ('gksu gnome-control-center'), then go to "details" and the hostname field should be editable. :)

---

### Post by audiomick on 2012-12-28
> **howhy said:**
> their wont be typing mistake becuase i copied and pasted

Very good. ;)

@ MG&TL : if it is there, I can't see it...

---

### Post by N00b-un-2 on 2012-12-28
isn't it just in /etc/host?
```
sudo nano /etc/host
```

---

### Post by irv on 2012-12-28
> **audiomick said:**
> But don't make a typing mistake in the new name like he did... ;)

I'm sure there is a way to do that with GUI tools, but I'm blowed if I can find it right now...

Could you do it with [Ubuntu Tweak]("http://www.webupd8.org/2012/11/ubuntu-tweak-gets-full-ubuntu-1210.html")?

---

### Post by haqking on 2012-12-28
as above.

You can also set a temporary name with

```
hostname
```You can also change your prompt regardless of hostname with:

```
PS1="<desired name> : "
```There are many options to use with this for example:

```
PS1="\d \h $ "
```Would show the date and hostname.

Some permanent changes to prompt may need to be set in bashrc

Peace

---

### Post by MG&amp;TL on 2012-12-28
> **audiomick said:**
> 
@ MG&TL : if it is there, I can't see it...

I'm on 13.04 ATM, but if I recall it works on earlier releases with gnome-control-center too. See thumbnail. :)

---

### Post by audiomick on 2012-12-28
> **MG&TL said:**
> I'm on 13.04 ATM, but if I recall it works on earlier releases with gnome-control-center too. See thumbnail. :)

Hmm, looks completely different here, but this install is still 10.10. Never mind...

---

### Post by irv on 2012-12-28
> **audiomick said:**
> Hmm, looks completely different here, but this install is still 10.10. Never mind...

On 10.10 you can change the host name in the Network setting on the general tab, as I remember.

---

### Post by howhy on 2012-12-29
> **haqking said:**
> as above.

You can also set a temporary name with

```
hostname
```You can also change your prompt regardless of hostname with:

```
PS1="<desired name> : "
```There are many options to use with this for example:

```
PS1="\d \h $ "
```Would show the date and hostname.

Some permanent changes to prompt may need to be set in bashrc

Peacenice
already in love with Linux now

---

