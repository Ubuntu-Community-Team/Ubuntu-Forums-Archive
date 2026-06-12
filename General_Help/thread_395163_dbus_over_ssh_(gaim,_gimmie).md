---
title: "dbus over ssh? (gaim, gimmie)"
date: 2007-03-27
forum: General Help
---

### Post by everdred on 2007-03-27
I bring my laptop to work daily. Though I use my work desktop primarily for work stuff, I run Gaim and Thunderbird off of my laptop, but have them appear on my work desktop via ssh (with X forwarding), as I like to keep my mail and IM history in one central, portable place.

I've recently been playing around with Gimmie ( [http://beatnik.infogami.com/Gimmie](http://beatnik.infogami.com/Gimmie) ) as a gnome-panel replacement, and think its dbus integration with my Gaim buddy list is pretty slick. Unfortunately, my buddy list only shows up as active in Gimmie when I have Gaim appear on my laptop itself, but not when I X-forward Gaim to my work desktop.

So basically, I'm guessing that the problem lies not in Gaim nor Gimmie, but in either dbus or ssh. Does anyone know if dbus works with ssh-X-forwarded apps?

---

### Post by everdred on 2007-03-29
(two-day bump)

Any ideas?

---

### Post by Endolith on 2007-10-13
I think one of my questions is related:

[http://ubuntuforums.org/showthread.php?t=569109](http://ubuntuforums.org/showthread.php?t=569109)

---

### Post by Endolith on 2007-11-14
**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+question/15070](https://answers.launchpad.net/ubuntu/+question/15070) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Bump.  No one can help us with this?

---

### Post by Endolith on 2007-11-14
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/162672](https://bugs.launchpad.net/ubuntu/+bug/162672) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Reported as a bug.

---

### Post by boutil on 2008-04-07
I don't think this is a bug.
You have to type :
```

export `dbus-launch`

```
to define environment variables so that programs can communicate with the dbus server on the remote machine. At least It worked for me: I could launch several KDE4 programs.

That the same kind of procedure as for ssh-agent or gpg-agent.

Can someone with access to launchpad test and write a comment for the bugs related to this message ?

---

### Post by Endolith on 2008-04-07
> **boutil said:**
> I don't think this is a bug.
You have to type :
```

export `dbus-launch`

```
to define environment variables so that programs can communicate with the dbus server on the remote machine. At least It worked for me: I could launch several KDE4 programs.

That the same kind of procedure as for ssh-agent or gpg-agent.

Can someone with access to launchpad test and write a comment for the bugs related to this message ?

Can you give more specific instructions?  Which machine do you run export on?    This should work out of the box as far as I'm concerned, and it doesn't.  

You can write a comment on the bug report.

---

### Post by Endolith on 2008-07-07
Any ideas what is meant by dbus-launch here?

---

