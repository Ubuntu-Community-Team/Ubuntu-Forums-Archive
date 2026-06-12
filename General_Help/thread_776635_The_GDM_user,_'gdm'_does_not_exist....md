---
title: "The GDM user, 'gdm' does not exist..."
date: 2008-04-30
forum: General Help
---

### Post by Lorgon Jortle on 2008-04-30
I just started up Ubuntu and I got this message. 

"The GDM user, 'gdm' does not exist. Please correct GDM configuration and restart GDM."

I have no idea what that means, as this is my second day with Linux. i think I may have deleted something. It asked me if I wanted to delete something at the beginning of last session and I ut my mouse over the button while I was reading it and the darn touch pad clicked down and it deleted. So now when it boots up there is no GUI. It is all terminal-based. Will someone please tell me what I need to type in to get this fixed. Or do I need to reinstall Ubuntu?

---

### Post by garyedwardjohnston on 2008-04-30
the gdm is the login screen.

when you installed Ubuntu it asked for a username and password enter them in the gdm

---

### Post by Lorgon Jortle on 2008-05-01
I did log in. There is no more graphics. It is all text based. How do I get the graphics back? It said it coudn't find them. Is there someway I can download and install them via the terminal it gives me upon startup?:confused:

---

### Post by BB_DaKraxor on 2008-05-01
Does this command have any result:

```
cat /etc/passwd | grep gdm
```

---

### Post by Lorgon Jortle on 2008-05-02
> **BB_DaKraxor said:**
> Does this command have any result:

```
cat /etc/passwd | grep gdm
```

Thanks, but this didn't work. No error came up, but it still didn't work. I found that if I type:
```

startx

```

then it works. But there is still something wrong with it. 

[IMG]http://www.jettmedia.com/files/or2ryqz0op26hvxlg2cr.png[/IMG]

This is what it is saying.

---

### Post by ljrossi on 2008-12-10
cat /etc/pasww | grep gdm

Gives no reply, Just prompt.

I started having this problem when installing software that requerired some changes on groups permision. I think something mess up things.

Regards

---

