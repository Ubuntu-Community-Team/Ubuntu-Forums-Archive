---
title: "Shift+Backspace"
date: 2006-12-03
forum: General Help
---

### Post by colonel_panic414 on 2006-12-03
Lately, I have begun trying to shift over to ubuntu from xp. So, at the moment, I am writing an essay in Open office, but every now and then, I accidentally hit shift and backspace at the same time, restarting my Xserver, and essentially wiping out the last couple of paragraphs. I have seen somewhere before how to disable that combination, but I can't find it anywhere. Can anyone offer any help?

---

### Post by syxbit on 2006-12-03
i believe it's "CTL-SHFT-BACKSP"
it's unlikely yo could accidentally hit all 3.

---

### Post by DarkN00b on 2006-12-03
I've done this a few times on my HP laptop. Not sure how to disable it though.

---

### Post by bmathis on 2006-12-03
> **syxbit said:**
> i believe it's "CTL-SHFT-BACKSP"
it's unlikely yo could accidentally hit all 3.

Its actually Ctrl+Alt+Backspace. this website should have the info you need

[http://ubuntuguide.org]("http://ubuntuguide.org")

---

### Post by colonel_panic414 on 2006-12-04
Yeah,  Shift+ BKSP and CTRL+SHIFT+BKSP and CTRL+ALT+BKSP do this. I looked at the web page you mentioned, and couldn't find the info. I feel so stupid lol... I knew how to do this once, but in my infinite stupidity... Well, forgot.

---

### Post by colonel_panic414 on 2006-12-04
Oh yeah, while I am getting help on keys, I have noticed something else... My Caps Lock key does nothing, whereas it does when I dual boot into XP... It may have something to do with me installing Compiz on Dapper?

---

### Post by ~LoKe on 2006-12-04
> **colonel_panic414 said:**
> Oh yeah, while I am getting help on keys, I have noticed something else... My Caps Lock key does nothing, whereas it does when I dual boot into XP... It may have something to do with me installing Compiz on Dapper?

Check your compiz settings, you're probably using it as a hotkey for something.

---

### Post by colonel_panic414 on 2006-12-04
No, that's not it. Just did that, and Caps isn't assigned to anything. I swear there's some command that is used to map this stuff, but I can't remember!

---

### Post by colonel_panic414 on 2006-12-06
Ok, got the caps lock fixed. It was some weird issue involving my gdm.conf-custom file. Anyway... I still can't figure out how to disable the shortcut that kills my X Server. It is in fact shift+backspace. And somehow, it gets hit everytime I'm on GAIM....

---

### Post by iamhugeinjapan on 2006-12-06
The shift+backspace problem is common with compiz/beryl installs. Try putting this into your startup programs:

```

xmodmap -e "keycode 22 = BackSpace Delete" 

```

I have it saved in a .sh executable script file so I can reuse it across installations without having to look up the code ;)

---

### Post by colonel_panic414 on 2006-12-06
You know what? I actually had that in there, from the Beryl installation thread. I think I either missed the Delete part, or it wasn't in the thread to begin with. Thank you SO much.

---

### Post by pentium0 on 2006-12-10
thanks guys.  exactly what i was looking for.  that little command works perfect to kill that too convenient hotkey SHIFT-BKSP.

---

### Post by Kanybus on 2006-12-14
Is there another way to do this, I tried the command.  Made it a .sh file and loaded it into my start up but shift+backspace still reloads me.

---

### Post by colonel_panic414 on 2007-01-06
Yes, I have found that it works well when you add the command to your xinitrc file. I'd tell you where to find it if you don't know, but I can't remember... (Fairly new user myself, and been unable to use Linux for a few weeks...)

---

### Post by aktiwers on 2007-01-07
Are you running XGL+Beryl?
I had the same problem, and fixed it doing this:

```
[SIZE=1]xmodmap -e &#8220;keycode 22 = BackSpace BackSpace Terminate_Server&#8221;[/SIZE]
```

If that doesnt do it, look here:
[http://gentoo-wiki.com/HOWTO_XGL/Troubleshooting#Shift_backspace](http://gentoo-wiki.com/HOWTO_XGL/Troubleshooting#Shift_backspace)

---

